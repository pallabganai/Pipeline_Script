pipeline {
    agent any
    stages {
        stage('GitCheckout') {
            steps {
                echo 'GitCheckout successfully';
                git 'https://github.com/pallabganai/Pipeline_Script.git';
            }
        }

        stage('Build') {
            steps {
                echo 'Build successfully';
                sh 'chmod 755 *.sh';
                sh './Build.sh';
            }
        }
	
        stage('Test') {
            parallel {
                stage('UnitTest') {
/*                    agent {
                        label "Windows_Node"
                    }*/
                    steps {
                        echo 'UnitTest passed successfully';
                    }
                    
                }
                stage('QualityGate') {
/*                    agent {
                        label "master"
                    }*/
                    steps {
						echo 'Quality Gate passed successfully';
					}
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployed successfully'
            }
        }
    }

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the pipeline changed'
        }
    }
}