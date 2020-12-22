pipeline{
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }
    agent none
        stages{
            stage('checkout'){
                agent any
                steps{
                    git 'https://github.com/Sushmith350/DevOpsClassCodes.git'
                }
            }
             stage('compile'){
                agent any
                steps{
                    sh 'mvn compile'
                }
                
            }
            stage('codereview'){
                agent any
                steps{
                    sh 'mvn pmd:pmd'
                }
                
            }
            stage('unittest'){
                agent any
                steps{
                    sh 'mvn test'
                }
                
            }
            stage('metricheck'){
                agent any
                steps{
                    sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
                }
               post{
                   always{
                       cobertura coberturaReportFile: 'target/site/cobertura/coverage.xml'
                   }
               }
            }
            stage('package'){
                agent any
                steps{
                    sh 'mvn package'
                }
            }
            
        }
    
    }
