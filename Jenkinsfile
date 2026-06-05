// pipeline{
//     agent any

//     stages{
//         stage('Build'){
//             steps{
//                 bat 'mvn clean'
//             }
//         }

//         stage('Test'){
//             steps{
//                 bat 'mvn test'
//             }
//         }
//         stage('Package'){
//             steps{
//                 bat 'mvn package'
//             }
//         }

//     }
// }


pipeline {

    agent any

    environment {
        APP_NAME = 'StudentApp'
    }

    stages {

        stage('Info') {
            steps {
                bat 'echo %APP_NAME%'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

    }
}