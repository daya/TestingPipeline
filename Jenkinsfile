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
    // checkpoint 'testing-complete' 
    stage('approve') {
      steps {
        mail body: "Approval needed for '${env.JOB_NAME}' at ${env.BUILD_URL}", subject: "${env.JOB_NAME} Approval", to: "daya+jenkins_approval_test@caringly.io" 
        timeout(time: 7, unit: 'DAYS') { 
          input message: 'Do you want to deploy?', parameters: [string(defaultValue: '', description: 'Provide any comments regarding decision.', name: 'Comments')], submitter: 'daya_test' 
        } 
      }
    } 
    // stage('approval') {
    //   input {
    //       message "Should the changes be deployed to production?"
    //       ok "Yes"
    //       submitter "daya_test"
    //       submitterParameter "APPROVER"
    //       parameters {
    //           string(name: 'PERSON', defaultValue: 'Mr Approver', description: 'Would you approve?')
    //       }
    //   }
    //   steps {
    //       echo "Hello, ${PERSON}, nice to meet you."
    //   }      
    // }
    stage('deploy') {
      steps {
        // sh 'rake'
        sh 'echo this is test deploy stage.'
      }   
    }
  }
}