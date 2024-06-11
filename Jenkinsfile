pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')

    }
   

    stages {
        stage('read the version'){
            steps{
                def packageJson = readJson file: 'package.json'
                def appVersion = packageJson.version
            }
        }
        stage('Install dependencies') {
            steps {
                sh """
                   npm install
                   ls -ltr
                   echo $appVersiion
                """

            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()

        }
        success { 
            echo 'I will run when pipeline is success'
        }
        failure { 
            echo 'I will run when pipeline is failure'
        }
    }
}