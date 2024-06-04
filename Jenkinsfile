pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo "build the code and using Maven"
            }
            post{
                always{
                    mail to: "96az.ma@gmail.com",
                    subject: "Integrate Git with Jenkins",
                    body: "The build has been done successfully!"
                }
            }
        }
        stage('Integration Test'){
            steps{
                echo "run unit tests to ensure execution of functionalities by using selenium"
            }
        }
        stage('Code Analysis'){
            steps{
                echo "analyse the code to ensure it meets industry standards. Tool is Jenkins!"
            }
        }
        stage('Security Scan'){
            steps{
                echo "Performed a security scan and identifies vulnerabilities. Tool is Nmap"
            }
        }
        stage('Deploy to staging'){
            steps{
                echo "Deploy the application to a staging server. Tool is AWS EC2"
            }
        }
    }
}
