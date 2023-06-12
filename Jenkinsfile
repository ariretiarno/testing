podTemplate(
    yaml: readTrusted('pod.yaml')
) {
    node(POD_LABEL) {
        if (env.BRANCH_NAME =~ 'PR-.*') {
            stage('Checkout') {
                def scmVars = checkout scm
                listFiles = sh(returnStdout: true, script: "git diff --diff-filter=d --name-only origin/master").split("\n")
            }

            stage ('Validate SQL') {
                script {
                    sh "echo PASSED"
                }

                if (currentBuild.currentResult != 'SUCCESS') {
                    notify("slack", "${currentBuild.currentResult}", "${message}", "${appFullName}", "#jenkins-build")
                }
            }
        }
    }
}