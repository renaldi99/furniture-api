pipeline {
    agent {
        node {
            label "linux && dotnet6"
        }
    }
    stages {
        stage("Build") {
            steps {
                script {
                    // code groovy
                    for(int i = 0; i < 5; i++) {
                        echo("display ${i}")
                    }
                }

                // sh('dotnet build --configuration Release')
                echo("Start Build")
                sleep(10)
                echo("Finish Build")
            }
        }
        
        stage("Test") {
            steps {
                script {
                    def data = ["row_id": "001", "job_name": "furnimonoapi"]
                    writeJSON file: 'data.json', json: data
                }
                // sh("error")
                echo("Start Test")
                echo("Finish Test")
            }
        }

        stage("Deploy") {
            steps {
                echo("Deploy with pipeline")

                def props = readJSON file: 'dataqu.json'
                echo("domain: ${props['domain-expansion']}")

                script {
                    if(fileExists('Dockerfile')) {
                        echo "Dockerfile is found"
                    }

                    if (env.BRANCH_NAME == 'master') {
                        echo "this branch ${env.BRANCH_NAME}"
                    } else  {
                        echo "this branch ${env.BRANCH_NAME}"
                    }
                }
            }
        }
    }
    post {
        always {
            echo "I always to run this pipeline"
        }
        success {
            echo "Pipeline is success"
        }
        failure {
            echo "Pipeline is failed"
        }
        cleanup {
            echo "Don't care success or error"
        }
    }
}