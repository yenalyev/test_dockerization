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

            stage("run docker image"){
                steps{
                echo"===================run docker image==============================="
                sh 'docker container rm -f test'
                sh 'docker run --name test -p 8083:8080 demo'
                echo"===================container run==============================="
                }
            }
        }
    }