pipeline{
    agent any
    stages{
        stage('version control'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/akudogithub/jenkins-test.git']])
            }
        }
    }
    stages{
        stage('parallel-job'){
            parallel{
                stage('sub-job1'){
                    steps{
                        sh 'lscpu'
                    }
                }
                stage('sub-job2'){
                    steps{
                        sh 'lsblk'
                    }
                }
            }
        }
    }
    stages{
        stage('unit-test'){
            steps{
                sh 'ps -ef'
            }
        }
        stage('unit-test2'){
            when{
                branch 'develop'
            }
            steps{
                sh 'date'
            }
        }
        stage('code-analysis'){
            steps{
                sh 'cal'
            }
        }
    }

    
}