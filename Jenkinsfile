pipeline{
    agent any 
        stages{
              stage('clone repository'){
                steps{
                    checkout([$class:'GitSCM',
                    branches:[[name:'*/main']],
                    userRemoteConfigs: [[url:'https://github.com/Shrey-sa/PES2UG21CS500_SHREY.git']]])
                }
              }
              stage('Build'){
                steps{
                    build 'PES2UG21CS500-1'
                    sh 'g++ Jenkins.cpp -o output'
                    sh 'mvn clean install'
                    echo 'Build Stage Successful'
                }
              }
              stage('Test'){
                steps{
                    sh './output'
                    sh 'mvn test'
                    echo 'test stage successfully'
                    post{
                        always{
                            junit 'target/surefire-reports/*.xml'
                        }
                    }
                }
              }
              stage('Deploy'){
                steps{
                    sh 'mvn deploy'
                    echo 'deployment successfull'
                }
              }
        }
        post{
            failure{
                echo 'pipeline failed'
            }
        }
    }
