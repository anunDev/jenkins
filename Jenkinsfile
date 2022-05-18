pipeline {
    agent { label 'ecs-anun-staging' }

    stages {
        stage ('Install ANUN Tracer') {
            steps {
                withCredentials([usernamePassword(credentialsId: "anun-staging-e2etenant-webhook-secret", passwordVariable: 'ANUN_SECRET', usernameVariable: 'ANUN_TENANT')]) {
                    sh 'apt-get update && apt-get install -y curl wget'
                    sh 'curl -s "https://downloads.anun-stg.cloud/tracer/pub/anun-installer.sh" | bash -s "https://downloads.anun-stg.cloud/tracer/anun-tracer.tar.gz?Expires=1669982554&Signature=1hhPpMnVXGdGv2lVv2PouyyRcnDL0thOlHAQIdkOTTbPoQyk2lg37BbkJzUF2zTzeulLfSl-gctIZwBeDW6ngBAKrTDTKiqRwqpS7xFeZfeyttlJdHwNViFMt5xy903TvZJ86O6b4IQhLoL6szWT0mhh9DCuoSAAGFUwgHm806ZlNXIz92eHdDDmC5071tu6F0B02w5I1~Ebrnys~8HSQ7mJr8zgpHn412lJEsz2jLkXNxOolLrP8kBvJ8XSXo0hru8qpS0Tse7RkKmfsfnoTCW8XWkBGV-v~9nUGoA~3oIl9tMGZSL0kdC9uIpIC~pzxO5S1bMwVQE6zjUTwG6Oyg__&Key-Pair-Id=K19MYNUVGQ3Q3N"'

                    sh "/anun-tracer/anun -p 1 &"
                }
            }
        }

        stage ('Stage 2') {
             steps {
                sh 'echo $$'
                echo 'running e2e test!'
                sh 'whoami'


                echo '============================================== anun-tracer should be running by now =============================================='
                script {
                    agent_pid = sh (
                        script: 'echo $$',
                        returnStdout: true
                    ).trim()

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
}