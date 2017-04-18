#!groovy
jettyUrl = 'http://localhost:8081/'

stage 'Dev'
node ('master'){
    echo "dev stage running..."
}

stage 'QA'
node ('master'){
    parallel(longerTests: {
        echo "QA stage long run..."
    }, quickerTests: {
        echo "QA stage quick run..."
    })
}

stage name: 'Staging', concurrency: 1
node ('master') {
    echo 'staging'
}

input message: "Does ${jettyUrl}staging/ look good?"
try {
    echo 'Before production good'
} catch (NoSuchMethodError _) {
    echo 'Checkpoint feature available in CloudBees Jenkins Enterprise.'
}
