pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                script{
                    scm_map = checkout scm
                    GIT_BRANCH = scm_map['GIT_BRANCH']
                    GIT_BRANCH_NAME = GIT_BRANCH.split('/', 2)[1]
                }
                sh "echo 'scm_map = ${scm_map}'"
                sh "echo 'GIT_BRANCH = ${GIT_BRANCH}'"
                sh "echo 'GIT_BRANCH_NAME = ${GIT_BRANCH_NAME}'"
            }
        }
        stage('build'){
            steps{
                sh "mvn -PautoInstallPackage clean install -Dcrx.host=10.0.2.15 -Dcrx.username=admin -Dcrx.password=admin"
            }
        }
    }
}