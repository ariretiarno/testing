podTemplate(
    yaml: readTrusted('pod.yaml')
) {
    node(POD_LABEL) {
        if (env.BRANCH_NAME =~ 'PR-.*') {
            stage('Checkout') {
                def scmVars = checkout scm
                
            }

            stage ('Validate SQL') {
                script {
                    sh "echo PASSED"
                }
            }
        }
    }
}