pipeline {
    agent any
    
    stages {
        stage('Run Script') {
            steps {
                echo 'Synchronizing..'
                // Install AWS CLI if neccessary
                // sh 'curl "https://awscli.amazonaws.com/awscli.exe-linux-x86_64.zip" -o "awscliv2.zip"'
                // sh 'unzip awscliv2.zip'
                // sh './aws/install'
                script {
                    withCredentials([[
                        $class: 'AmazonWebServicesCredentialsBinding',
                        accessKeyVariable: 'AKIA3VRGDYORAB5L5SIE',
                        secretKeyVariable: '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',
                        credentialsId: 'gamut'
                    ]]) {
                        sh '''
                            aws s3 sync /var/jenkins_home s3://pycubetestbucket --exclude "workspace/*" --delete
                        '''
                    }
                }
            }
        }
        stage('Notification') {
            steps {
                echo 'Finished...'
            }
        }
    }
}
