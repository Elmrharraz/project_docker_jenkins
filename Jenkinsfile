pipeline {
      agent any
      stages{
      
         // Création image
        stage('Etape 0 stop and delete mon container') {
            steps {
                sh 'docker rm -f cv_salma_container'
            }
            post {
                success {
                    echo "====++++Container stopped and delete with success++++===="
                }
                failure {
                    echo "====++++Docker failed to stop/delete my container++++===="
                }
            }
        }
        // Création image
        stage('Création de  image docker') {
            steps {
                sh 'docker build -t cv_salma .'
            }
            post {
                success {
                    echo "====++++Docker image created with success++++===="
                }
                failure {
                    echo "====++++Docker image failed++++===="
                }
            }
        }

          // Création image
        stage('Lancer un container de cette image') {
            steps {
                sh 'docker run -d -p 8089:80  --name cv_salma_container cv_salma'
            }
            post {
                success {
                    echo "====++++Container started with success++++===="
                }
                failure {
                    echo "====++++Failed to start Container++++===="
                }
            }
        }
      }
}
