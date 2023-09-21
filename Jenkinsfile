@Library('jenkins-library') _

pipeline {
    agent {
        kubernetes(containerCall(imageName: ACR_NAME, credentialSecret: SECRET_NAME, nodeSelectorValue: NODE_SELECTOR_VALUE, nodeTaintKey: NODE_TAINT_KEY, jdkBlocked: false, podmanBlocked:false, aksBuilderBlocked:false, lighthouseBuilderBlocked:false))
    }
    environment {
        BRANCH_MINUS = GIT_BRANCH.minus('origin/')
    }

    stages {
        stage('Branch name') {
            steps {
                container('aks-builder') {
                    echo "$BRANCH_MINUS"
                }
            }
        }
        stage('Repo name') {
            steps {
                container('aks-builder') {
                    echo "$GIT_REPO_NAME"
                }
            }
        }
    }
}
