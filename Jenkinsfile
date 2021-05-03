// Sample script for batch install build step using manifest file with default name: now_batch_manifest.json
// ServiceNow API: POST /sn_cicd/app/batch/install

pipeline {
  agent any

  environment {
    CREDENTIALS = 'f15c53d0-25d0-41ab-adce-3f60e6bc9217'
    PRODENV = 'https://chiarngqdemoauthor.service-now.com'
  }

  stages {
    stage('release') {
      steps {
        snBatchInstall(
          url: "${PRODENV}"
          ,credentialsId: "${CREDENTIALS}"
          ,useFile: true
//        ,file: "now_batch_manifest.json" // default file name localized in workspace,
                                           // required if there is a file with different name
                                           // or in different localization than default one
          )
      }
    }
  }
}
