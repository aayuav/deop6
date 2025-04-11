# deop6
pipeline{
agent any
        stages{
            stage('Checkout'){
            step{
                git branch:'main',url:'https://github.com/aayuav/deop6.git'
            }
            }
            stage('Build')
            steps{
                shpipeline{
agent any
            stages{
            stage('Checkout'){
            steps{
                git branch:'main',url:'https://github.com/aayuav/deop6.git'
            }
            }
            stage('Build'){
            steps{
                sh'mvn clean package'
            }
            }
            stage('Test'){
            steps{
                sh 'mvn test'
            }
            }
            stage('Archive Artifacts'){
                steps{
                archiveArtifacts artifacts:'**/target/*.jar',allowEmptyArchieve:
                }
            }
            stage('Deploy'){
                steps{
                sh"""
                    export ANSIBLE_HOST_KEY_CHECKING=False
                    ansible-playbook -i hosts.ini deploy.yml --extra-
    ='ansible_become_pass=exam@cse
                }
            }
            }
                }
            }
        }
}
