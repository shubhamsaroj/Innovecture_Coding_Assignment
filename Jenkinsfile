pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/shubhamsaroj/Innovecture_Coding_Assignment.git'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven1') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'Maven1') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Install Stage') {
            steps {
                withMaven(maven : 'Maven1') {
                    sh 'mvn install'
                }
            }
        }
        stage ('Deploy to tomcat') {
            steps {
                                sshagent(['656e7d80-ed1f-45c4-80a2-051f2968c4bc']) {
                                sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@18.219.227.17:/var/lib/tomcat/webapps'
                                                                   }
            }
        }

}
}
