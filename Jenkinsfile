
pipeline {
   agent { label 'ecs-anun-dev' }
    stages {
        stage('Welcome Step') {
            steps { 
                echo 'running e2e test!'
                echo 'downloading anun-tracer'
                sh 'curl https://downloads.anun-dev.cloud/tracer/anun-tracer.tar.gz?Expires=1669373114&Signature=BqUp8fqf7O0EcFXUvdJvfUFUjg42cy~Yk2cRqC8r9urHZrNJ7D6zJ07YUcCjDvUwkJYwDiXqFKb1JW1RnUi3tlrdlFvwfQYMdwkCsvM51dfke-z9RfnJVPy4qzqC7-lEBjU2gWmJaMGwghXkqpIQsCw0uqKIhErDEtUvsArZW-dpWGDg6hvG1VyncZTcGUf7X3yDvNTKhdEYeXCVvoV2fOSFd8vX~CXklKb6e1uOuAssb5GKxj6SAGl~s9dXwre8TP56SJE00KHXXLvfmfKIU2Zfi1uE5MdWt9IiEsxRIYTLIMM40SXbhzP2ArEgMOILuFjvUoAQ8XqwTLcqJHTW9w__&Key-Pair-Id=K2LJ44JU7P44XR --output anun-tracer.tar.gz'
            }
        }
    }
}
