    pipeline{
        agent any

        tools {
                maven "Maven 3.8.4"
        }

        stages{
            stage('Initialize'){
               steps{
                   echo "PATH = ${M2_HOME}/bin:${PATH}"
                   echo "M2_HOME = /opt/maven"
               }
            }

            stage("create docker image"){
                steps{
                    echo"===================start building image==============================="
                    sh 'mvn -B -DskipTests clean package'
                    sh 'docker build -t demo .'
                }
            }

//             stage("run docker image"){
//                 steps{
//                     echo"===================run docker image==============================="
//                     sh 'docker container rm -f test'
//                     sh 'docker run --name test -p 8083:8080 -d demo'
//                     echo"===================container run==============================="
//                 }
//             }

            stage("push docker image into docker hub"){
            steps{
            echo "===========================pushing docker image============================"
            sh 'docker login -u maximen -p 22beacfa-2298-4c12-8431-49fa0fca2b32'
            sh 'docker image tag demo maximen/test:test'
            sh 'docker push maximen/test:test'
            }
            }
        }
    }