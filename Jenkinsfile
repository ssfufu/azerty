pipeline {
    agent any 
    
    environment {
        url_api = "http://youtube.com"
    }
    
    stages {
        stage("etape1") {
            steps {
                echo "ce que je veux"
                script {
                    def unNom = 2
                    echo "${unNom}"
                }
            }
        }
        stage("url-api") {
            steps {
                echo "va sur ... : ${url_api}"
            }
        }
        stage ("tryCatch") {
            steps {
                script {
                    try {
                        def response = httpRequest 'https://httpbin.org/get'
                        println response.content
                    } catch (Exception e) {
                        error "erreur :  ${e.message}"
                    }
                }
                
            }
        }
    }
    post {
        success {
            echo "ce que je veux s'est bien passé !"
        }
        failure {
            echo "ce que je veux ne s'est pas bien passé :("
        }
        always {
            echo "s'execute toujours"
        }
    }
}
 
