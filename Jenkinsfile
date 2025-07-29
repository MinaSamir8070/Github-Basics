pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the app...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // افترض إن في أمر ممكن يفشل
                sh 'exit 1' // لاختبار حالة الفشل
            }
        }
    }

    post {
        always {
            echo 'This always runs (cleanup, close connections, etc)'
            // مثال على تنظيف ملفات
            sh 'rm -rf temp_dir || true'
        }

        success {
            echo 'Pipeline succeeded ✅'
            // مثال: إرسال إشعار
            // slackSend(channel: '#ci', message: 'Build succeeded!')
        }

        failure {
            echo 'Pipeline failed ❌'
            // مثال: إرسال بريد إلكتروني عند الفشل
            // mail to: 'dev-team@example.com',
            //      subject: "Build Failed",
            //      body: "The Jenkins build failed. Please check the console output."
        }

        unstable {
            echo 'Build is unstable (some tests failed)'
        }

        changed {
            echo 'Pipeline status has changed (from success to fail or vice versa)'
        }
    }
}
