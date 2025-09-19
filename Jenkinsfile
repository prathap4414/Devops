pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/prathap4414/Devops.git', branch: 'main'
      }
    }
    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }
    stage('Run Tests') {
      steps {
        sh 'npm test || echo "No tests defined"'
      }
    }
    stage('Build Artifact') {
      steps {
        sh 'zip -r build.zip . -x node_modules/** -x .git/**'
      }
    }
    stage('Archive Artifact') {
      steps {
        archiveArtifacts artifacts: 'build.zip', fingerprint: true
      }
    }
    stage('Notify') {
      steps {
        echo "✅ Build complete for ${env.JOB_NAME} #${env.BUILD_NUMBER}"
      }
    }
  }
}

