pipeline{
        agent any
        stages{
            stage('Clean and Download'){
                steps{
                    sh "rm -rf JenkinsTest/"
                    sh "git clone https://github.com/78afec35/JenkinsTest"
                }
            }
        

            stage('Set Up Environment'){
                steps{
                    sh "sudo sh ./startupscript.sh"

                }
            }
        

            stage('Bring up'){
                steps{
                    sh "sudo docker-compose pull && sudo docker-compose up -d."
                }
            }
                 
        }
}
