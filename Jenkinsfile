

pipeline {
    environment {
        ANUN_HOST_NAME = 'api.anun-dev.cloud'
        ANUN_TENANT    = 'e2etenant'
        ANUN_SECRET    = 'V9kV0Kir4jHZrXhhgrpbrZUg0r6YzLW5F5zazOMDugfCnwS3cv24TepfFPOxfPYU'
        ANUN_SOURCE    = 'jenkins'
    }
    agent { label 'ecs-anun-dev' }
    def myVariable = sh 'echo $$'
    stages {
        stage('Welcome Step') {
            steps { 
                sh 'echo $$'
                echo 'running e2e test!'
                echo '============================================== downloading & installing anun-tracer =============================================='
                sh 'curl -s "https://downloads.anun-dev.cloud/tracer/pub/anun-installer.sh" | bash -s "https://downloads.anun-dev.cloud/tracer/anun-tracer.tar.gz?Expires=1669373114&Signature=BqUp8fqf7O0EcFXUvdJvfUFUjg42cy~Yk2cRqC8r9urHZrNJ7D6zJ07YUcCjDvUwkJYwDiXqFKb1JW1RnUi3tlrdlFvwfQYMdwkCsvM51dfke-z9RfnJVPy4qzqC7-lEBjU2gWmJaMGwghXkqpIQsCw0uqKIhErDEtUvsArZW-dpWGDg6hvG1VyncZTcGUf7X3yDvNTKhdEYeXCVvoV2fOSFd8vX~CXklKb6e1uOuAssb5GKxj6SAGl~s9dXwre8TP56SJE00KHXXLvfmfKIU2Zfi1uE5MdWt9IiEsxRIYTLIMM40SXbhzP2ArEgMOILuFjvUoAQ8XqwTLcqJHTW9w__&Key-Pair-Id=K2LJ44JU7P44XR"'

                echo '============================================== finding agent pid =============================================='

                echo '============================================== running anun-tracer =============================================='
                
                sh '/anun-tracer/anun -p ${agent_pid} &'
                
                echo '============================================== anun-tracer should be running by now =============================================='
                sh 'ls'
                sh 'sleep 1'
                sh 'sleep 5'
                sh 'echo $$'
                sh 'ls -al /tmp/'
                sh 'ps'

            }
        }
    }
}
