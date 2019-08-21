#!/usr/bin/env groovy

env.AWS_PROFILE = 'eu-west-1'

node('aws') {
  ansiColor('xterm') {

    stage('Checkout') {
      git([
        url: 'https://github.com/bitbar/cloud-testdroid-info-page.git',
        branch: 'master',
        poll: true
      ])
    }

    stage('Publish') {
      sh('aws s3 sync src s3://cloud-testdroid-info-page')
    }
  }
}
