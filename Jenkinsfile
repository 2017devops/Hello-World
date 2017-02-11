#!groovy

def jobName = "${env.JOB_NAME}"
GIT_COMMIT = sh (
    script: 'git rev-parse HEAD',
    returnStdout: true
).trim()
echo "Git committer email: ${GIT_COMMIT}"
Jenkins.instance.getItem(jobName.split('/')[0]).description = "<a href='https://github.com/Anuj1990/pipeline-as-code-demo/commit/$GIT_COMMIT'>PR</a>"
currentBuild.description = "<a href='https://github.com/Anuj1990/pipeline-as-code-demo/commit/$GIT_COMMIT'>PR</a>"
node ('master') {
stage 'Dev'

    checkout scm
    //mvn 'clean package'
    //dir('target') {stash name: 'war', includes: 'x.war'}
    echo "${env.GIT_URL}"


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


}
