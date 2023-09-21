@Library('jenkins-library') _

pipeline {
    agent {
        kubernetes(containerCall(imageName: ACR_NAME, credentialSecret: SECRET_NAME, nodeSelectorValue: NODE_SELECTOR_VALUE, nodeTaintKey: NODE_TAINT_KEY, jdkBlocked: false, podmanBlocked:false, aksBuilderBlocked:false, lighthouseBuilderBlocked:false))
    }

    stages {
        stage('Prepare environment') {
            steps {
                container('aks-builder') {
                    echo "$GIT_BRANCH"
                }
            }
        }
    }
}
