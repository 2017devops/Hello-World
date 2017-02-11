#!groovy

def jobName = "${env.JOB_NAME}"
GIT_COMMIT = sh (
    script: 'git rev-parse HEAD',
    returnStdout: true
).trim()
echo "Git committer email: ${GIT_COMMIT}"
Jenkins.instance.getItem(jobName.split('/')[0]).description = "<a href='https://github.com/Anuj1990/pipeline-as-code-demo/commit/$GIT_COMMIT'>PR</a>"
currentBuild.description = "<a href='https://github.com/Anuj1990/pipeline-as-code-demo/commit/$GIT_COMMIT'>PR</a>"

stage 'Dev'
node ('master') {
    checkout scm
    //mvn 'clean package'
    //dir('target') {stash name: 'war', includes: 'x.war'}
    echo "${env.GIT_URL}"
}

stage 'QA'

    echo "QA Deployment"

/*parallel(longerTests: {
    runTests(30)
}, quickerTests: {
    runTests(20)
})*/

stage 'UAT'

    echo "UAT Deployment"


stage 'PROD'

    echo "PROD Deployment"


stage name: 'Staging', concurrency: 1
node ('master') {
    deploy 'staging'
}

//input message: "Does staging look good?"
try {
    checkpoint('Before production')
} catch (NoSuchMethodError _) {
    echo 'Checkpoint feature available in CloudBees Jenkins Enterprise.'
}

stage name: 'Production', concurrency: 1
node ('master'){
    echo 'Production server looks to be alive'
    deploy 'production'
    echo "Deployed to production"
}

def mvn(args) {
    sh "${tool 'Maven 3.x'}/bin/mvn ${args}"
}

def runTests(duration) {
    node {
        sh "sleep ${duration}"
        }
    }

def deploy(id) {
    unstash 'war'
    sh "cp x.war /tmp/${id}.war"
}

def undeploy(id) {
    sh "rm /tmp/${id}.war"
}

stage('example') {
   annotate('WebLink','http://example.com');
   annotate('MySpecialCondition','true');
}
