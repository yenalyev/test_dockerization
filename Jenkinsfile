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
                    sh 'docker build .'
                }
            }

            stage("run docker image"){
                steps{
                echo"===================run docker image==============================="
                sh 'docker run --name demo -p 8083:80 openjdk'

                }
            }
        }
    }