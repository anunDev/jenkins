pipeline {
    environment {
        ANUN_HOST_NAME = 'api.anun-stg.cloud'
        ANUN_TENANT    = 'e2etenant'
        ANUN_SECRET    = 'VTJwVUzNXV28s4s4pADctjfFCE5Nb8aBcrHuW0eZGwl4EScvq4yeO6MNzgIksmPP'
        ANUN_SOURCE    = 'jenkins'
    }

    agent { label 'ecs-anun-dev' }

    stages {
        stage('Welcome Step') {
            steps {
                sh 'echo $$'
                echo 'running e2e test!'
                sh 'whoami'

                echo '============================================== downloading & installing anun-tracer =============================================='
                sh 'apt-get update && apt-get install -y curl wget'
                sh 'curl -s "https://downloads.anun-stg.cloud/tracer/pub/anun-installer.sh" | bash -s "https://downloads.anun-stg.cloud/tracer/anun-tracer.tar.gz?Expires=1669982554&Signature=1hhPpMnVXGdGv2lVv2PouyyRcnDL0thOlHAQIdkOTTbPoQyk2lg37BbkJzUF2zTzeulLfSl-gctIZwBeDW6ngBAKrTDTKiqRwqpS7xFeZfeyttlJdHwNViFMt5xy903TvZJ86O6b4IQhLoL6szWT0mhh9DCuoSAAGFUwgHm806ZlNXIz92eHdDDmC5071tu6F0B02w5I1~Ebrnys~8HSQ7mJr8zgpHn412lJEsz2jLkXNxOolLrP8kBvJ8XSXo0hru8qpS0Tse7RkKmfsfnoTCW8XWkBGV-v~9nUGoA~3oIl9tMGZSL0kdC9uIpIC~pzxO5S1bMwVQE6zjUTwG6Oyg__&Key-Pair-Id=K19MYNUVGQ3Q3N"'

                echo '============================================== running anun-tracer =============================================='
                sh "/anun-tracer/anun -p 1 &"

                echo '============================================== anun-tracer should be running by now =============================================='
                script {
                    agent_pid = sh (
                        script: 'echo $$',
                        returnStdout: true
                    ).trim()
                }
                echo "agent pid: ${agent_pid}"

                sh 'ls'
                sh 'sleep 1'
                sh 'echo $$'
                sh 'ls -al /tmp/'
                sh 'ls'
                sh 'ls -l'
                sh 'cat /tmp/anun.*.log'
            }
        }
    }
}