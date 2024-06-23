pipeline {
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        git url: 'https://github.com/Krackern/test', branch: 'master', credentialsId: 'b174cbcc-46e1-4068-a9c1-9dc6e15354d2'
      }
    }

    stage('OWASP DependencyCheck') {
      steps {
        dependencyCheck(additionalArguments: '--format HTML --format XML', odcInstallation: 'Default')
      }
    }

  }
  post {
    success {
      dependencyCheckPublisher(pattern: 'dependency-check-report.xml')
    }

  }
}
