pipeline{
  agent any
  stages{
    stage('git-clone'){
     steps{
       checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github_id', url: 'https://github.com/jenkinsserver1/multi-branch-para.git']]])
     } 
    }
    stage('actions1 and actions2'){
      parallel {
        stage('actions1'){
          steps{
            echo "actions1"
          }
        }
        stage('action2'){
          steps{
            echo "action2"
            echo "ls"
          }
        }
        stage('user-checks'){
          steps{
            sh 'cat /etc/passwd | grep ubuntu'
          }
        }
      }
    }
    stage('version-check'){
      steps{
        echo "end of parallel job"
      }
    }
    stage('webhook-fix'){
      steps{
        echo "webhook fix"
      }
    }
    stage('2-parallel'){
      parallel {
        stage('to-test-muti-build'){
          steps{
            sh 'lscpu'
            sh 'free -m'
          }
        }
      }
    
    }
  }
}
