    pipeline{
    agent any
    stages{
    stage("create docker image"){
    steps{
    echo"===================start building image==============================="
    sh 'mvn -B -DskipTests clean package'
    sh 'docker build .'

    }
    }
    }
    }