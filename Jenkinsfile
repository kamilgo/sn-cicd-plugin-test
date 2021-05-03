// Sample script for batch install build step eg. for release deployment.
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
          url: "${PRODENV}",
          credentialsId: "${CREDENTIALS}",
          batchName: 'Release 2.2 Deployment',
          packages: '[
                        {
                          "id": "syd_id_abcefghi",
                          "type": "application",
                          "load_demo_data": false,
                          "requested_version": "1.0.2",
                          "notes": "User specific text to describe this application install"
                        },
                        {
                          "id": "syd_id_defabcde",
                          "type": "application",
                          "requested_version": "1.0.0",
                          "requested_customization_version": "2.0.7",
                          "notes": "Customization for CSM App1"
                        },
                        {
                          "id": "com.glide.some.plugin",
                          "type": "plugin",
                          "load_demo_data": true,
                          "notes": "Plugin related notes"
                        }]
                      }',
          notes: 'User specified additional notes'
      }
    }
  }
}
