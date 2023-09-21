@Library('jenkins-library') _

import groovy.json.JsonBuilder
import groovy.json.JsonSlurper
import java.io.File
System.setProperty("hudson.model.DirectoryBrowserSupport.CSP", "")

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
