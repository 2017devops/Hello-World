
node ('master') {
stage 'Dev'
    checkout scm
    
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
