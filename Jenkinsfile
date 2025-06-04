pipeline{
  agent any
  tools{
    maven 'Maven'
  }
  stages{
    stage('checkout'){
      steps{
        git 'https://github.com/Akashmishra1421/AnsibleWebApp.git'
      }
    }
    stage('build'){
      steps{
        sh 'mvn clean package'
      }
    }
    stage('archive'){
      steps{
        archiveArtifacts artifacts:'target/*.war', fingerprint=true
      }
    }
    stage('deploy'){
      steps{
        sh 'mvn clean package'
        ansiblePlaybook playbook:'ansible/deploy.yml', inventory:'hosts.ini'
      }
    }
  }
}
