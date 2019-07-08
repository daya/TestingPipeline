pipeline {
  agent { 
    docker { 
      label 'slave-docker'
      image 'iamdaya/ruby:2.4.1-apline-rubyracer' 
    } 
  }
  stages {
    stage('requirements') {
      steps {
        // sh 'gem install bundler -v 2.0.1'
        sh 'echo This is requirements stage'
      }
    }
    stage('build') {
      steps {
        // sh 'bundle install'
        sh 'echo this is build stage'
      }
    }
    stage('test') {
      steps {
        // sh 'rake'
        sh 'echo this is test stage'
      }   
    }
    stage('approval') {
      input {
          message "Should the changes be deployed to production?"
          ok "Yes"
          submitter "daya_test"
          submitterParameter "APPROVER"
          parameters {
              string(name: 'PERSON', defaultValue: 'Mr Approver', description: 'Would you approve?')
          }
      }
      steps {
          echo "Hello, ${PERSON}, nice to meet you."
      }      
    }
    stage('deploy') {
      steps {
        // sh 'rake'
        sh 'echo this is test deploy stage.'
      }   
    }
  }
}