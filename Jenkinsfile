pipeline {
    agent { label 'ecs-anun-prod' }

    stages {
        stage ('Install ANUN Tracer') {
            steps {
                withCredentials([usernamePassword(credentialsId: "anun-prod-e2etenant-webhook-secret", passwordVariable: 'ANUN_SECRET', usernameVariable: 'ANUN_TENANT')]) {
                    sh 'apt-get update && apt-get install -y curl wget'
                    sh 'curl -s "https://downloads.anun.cloud/tracer/pub/anun-installer.sh" | bash -s "https://downloads.anun.cloud/tracer/anun-tracer.tar.gz?Expires=1680523204&Signature=o3pcQU~3po9GIWr0OZr4os4KTY~YHIt-QVfFARi21Y4tlbFHlmYc-0T9HTjUUjAMMyRd4Bo2qwjEfOxbYHkHzz-lE8uhazMqZQ8Ai9xF93OJK8gjro1dX7xvRBA7xqYmfScG0dt7fgfrOmh1HHIRJjPdLdAaUXQr~3hQwu43FHtYMJgSLduKJYHJoTnqJ5Q66iAotjKgA3nHnH4u-XtQ5qnVspLp~XjX2r-yRZjLozrTMsuBSLMwjmJHcKSQizRf54j-~NBnCaMroUKqzVIIUyB4DnsIQsiIrn5Vm4US6M3J-MyeX03wbMVCfi3RuOmRxw0iU1Oz1Dw9TjZzl0~P8g__&Key-Pair-Id=K3I8ZP4ALY4308"'

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