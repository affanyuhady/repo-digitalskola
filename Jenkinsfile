pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub
                git 'https://github.com/username/repo-name.git'
            }
        }
        stage('Build') {
            steps {
                // Perintah untuk build aplikasi, sesuaikan dengan build tool (Maven, Gradle, dll.)
                sh './build.sh'  // contoh script build
            }
        }
        stage('Test') {
            steps {
                // Jalankan unit test
                sh './run_tests.sh'  // contoh script test
            }
        }
    }

    post {
        success {
            // Kirim notifikasi jika build berhasil
            mail to: 'youremail@example.com',
                 subject: "Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Good news! The build for ${env.JOB_NAME} completed successfully.\n\nDetails: ${env.BUILD_URL}"
        }
        failure {
            // Kirim notifikasi jika build gagal
            mail to: 'youremail@example.com',
                 subject: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Unfortunately, the build for ${env.JOB_NAME} failed.\n\nDetails: ${env.BUILD_URL}"
        }
    }
}
