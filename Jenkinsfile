
pipeline {
   agent { label 'ecs-anun-#STAGE' }
    stages {
        stage('Welcome Step') {
            steps { 
                echo 'running e2e test!'
                echo 'downloading anun-tracer'
                curl #ANUN_TRACER_DOWNLOAD_URL --output anun-tracer.tar.gz
                tar xvzf anun-tracer.tar.gz
                chmod a+x anun-tracer/anun
                chmod a+x /anun-tracer/setup.sh
                echo '/anun-tracer/setup.sh ...'
                ps -aux
                sleep 1
                sleep 1
                echo $$
                ls -al /tmp/
                sleep 1
                sleep 1
                sleep 1
                sleep 1
                cat /tmp/anun.*.log
            }
        }
    }
}
