pipeline {
  agent { docker { image 'iamdaya/ruby:2.4.1-apline-rubyracer' } }
  stages {
    stage('requirements') {
      steps {
        // sh 'gem install bundler -v 2.0.1'
        sh 'This is requirements stage'
      }
    }
    stage('build') {
      steps {
        // sh 'bundle install'
        sh 'this is build stage'
      }
    }
    stage('test') {
      steps {
        // sh 'rake'
        sh 'this is test stage'
      }   
    }
    stage('deploy') {
      steps {
        // sh 'rake'
        sh 'this is test deploy stage.'
      }   
    }
  }
}