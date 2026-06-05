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


// pipeline {

//     agent any

//     environment {
//         APP_NAME = 'StudentApp'
//     }

//     stages {

//         stage('Info') {
//             steps {
//                 bat 'echo %APP_NAME%'
//             }
//         }

//         stage('Build') {
//             steps {
//                 bat 'mvn clean package'
//             }
//         }

//     }
// }


// pipeline {

//     agent any

//     environment {
//         APP_NAME = 'student-app'
//     }

//     stages {

//         stage('Build') {
//             steps {
//                 bat 'mvn clean package'
//             }
//         }

//         stage('Docker Build') {
//             steps {
//                 bat 'docker build -t student-app:v1 .'
//             }
//         }

//     }
// }


pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t tyagianant/student-app:v1 .'
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub-creds',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {

                    bat 'docker login -u %DOCKER_USER% -p %DOCKER_PASS%'
                    bat 'docker push tyagianant/student-app:v1'
                }
            }
        }

    }
}