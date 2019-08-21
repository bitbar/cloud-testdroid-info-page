#!/usr/bin/env groovy

@Library('CloudOrchestrationLibrary')
import com.bitbar.Config

env.AWS_PROFILE = 'eu-west-1'

node('aws') {
  ansiColor('xterm') {

    stage('Checkout') {
      git([
        url: 'git@github.com:bitbar/documentation.git',
        branch: 'master',
        credentialsId: Config.github.credentialsId,
        poll: true
      ])
    }

    stage('Publish') {
      sh('aws s3 sync src s3://cloud-testdroid-info-page')
    }
  }
}
