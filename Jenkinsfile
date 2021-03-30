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
                    sh "sudo apt update"
                    sh "sudo apt install build-essential -y "
                    sh "sudo apt install docker.io -y"
                    sh "sudo groupadd docker"
                    sh "sudo gpasswd -a $USER docker"
                    sh "sudo reboot"
                    sh "sudo apt install -y curl jq"
                    sh "version=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r '.tag_name')
"
                    sh "sudo curl -L \"https://github.com/docker/compose/releases/download/${version}/docker-compose-$(uname -s)-$(uname -m)\" -o /usr/local/bin/docker-compose "
                    sh "sudo chmod +x /usr/local/bin/docker-compose"
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
