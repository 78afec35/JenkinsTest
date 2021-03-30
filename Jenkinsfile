pipeline{
        agent any
        stages{
            stage('Clean and Download'){
                steps{
                    sh "rm -rf JenkinsTest/"
                    sh "git clone https://github.com/78afec35/JenkinsTest"
                }
            }
        }
        stages{
            stage('Set Up Environment'){
                steps{
                    sh "sudo sh ./startupscript.sh"

                }
            }
        }
        stages{
            stage('Bring up'){
                steps{
                    sh "sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d."
                }
            }
        }          
}
