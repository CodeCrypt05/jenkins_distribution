pipeline {
    agent any

    stages {
        stage('git pull') {
            steps {
                // Enter your github url here 
                git url: 'https://github.com/CodeCrypt05/jenkins_distribution',                       
                branch: 'main'
            }
        }

        // stage('Run Tests') {
        //     steps {
        //         // Running Flutter tests
        //         bat 'flutter test'
        //     }
        // }

        stage('Build Android APK') {
            steps {
                // Building the APK in release mode
                bat 'flutter build apk --release'
            }
        }

        stage('Archive APK') {
            steps {
                // Archiving the release APK
                archiveArtifacts artifacts: '**/build/app/outputs/flutter-apk/app-release.apk', allowEmptyArchive: false
            }
        }

    }
       
    post {
        always {
            echo 'Pipeline finished.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}