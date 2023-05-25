pipeline {
    agent any
    stages {
        stage ('Git Checkout') {
              steps {
                  git branch: 'main',  url: 'https://github.com/anjukshrestha/postmanapiautomation'
                }
        }
        stage('Run') {
            steps {
                sh 'newman run petstoretest.postman_collection.json -d inputdata.json -r htmlextra --reporter-htmlextra-export ./report.html'
            }
        } 
        
        stage('Report') {
            steps {
                publishHTML (target : [allowMissing: false,
                     alwaysLinkToLastBuild: true,
                     keepAll: true,
                     reportDir: '',
                     reportFiles: 'report.html',
                     reportName: 'My Reports',
                     reportTitles: 'The Report'])
            }
        }
    }
}
