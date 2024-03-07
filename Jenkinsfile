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
                    echo 'Build Stage Successful'
                }
              }
              stage('Test'){
                steps{
                    sh './output'
                    echo 'test stage successfully'
                }
              }
              stage('Deploy'){
                steps{
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
