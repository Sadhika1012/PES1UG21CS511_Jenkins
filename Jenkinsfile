pipeline {
    agent any
    stages {
       stage('Clone repository') {
          steps {
            checkout([$class: 'GitSCM',
            branches: [[name: '*/main']],
            userRemoteConfigs: [[url:'https://github.com/sadhika1012/PES1UG21CS511_Jenkins']]])
         }
   }
stage('Build') {
    steps {
         build 'PES1UG21CS511'
         sh 'g++ main.cpp -o output'
     }
  }
stage('Test') {
    steps {
        sh './output'
     }
}
stage('Deploy') {
    steps {
        echo 'deploy'
      }
   }
}
 post {
      always{ 
         script {
           if (currentBuild.result == 'FAILURE') {
                echo 'Pipeline failed!'
         }
        }

        }
    }
 }
