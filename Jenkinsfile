pipeline {
  agent any
  stage {
    stage('checkout SCM') 
    steps {

      git branch: 'master', url: 'git@github.com:brandonjones085/plantSim.git'
    }
  stage {
    stage('Install') 
      steps { sh 'npm install' }
    }

    stage('Test') {
      parallel {
        stage('Static code analysis') {
            steps { sh 'npm run-script lint' }
        }
        stage('Unit tests') {
            steps { sh 'npm run-script test' }
        }
      }
    }

    stage('Build') {
      steps { sh 'npm run-script build' }
    }
  }
}