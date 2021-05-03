// Sample script for instance scan feature. Execute all types of instance scan with sample parameters.
// ServiceNow API:
//   api/sn_cicd/instance_scan/[full_scan | point_scan | suite_scan/combo/{comboSysId} | suite_scan/{suiteSysId}/scoped_apps | instance_scan/suite_scan/{suiteSysId}/update_sets]

pipeline {
  agent any
  
  environment {
    CREDENTIALS = 'f15c53d0-25d0-41ab-adce-3f60e6bc9217'
    DEVENV = 'https://chiarngqdemoauthor.service-now.com'
  }

  stages {
    stage('full-scan') {
      steps {
        snInstanceScan(
          url: "${DEVENV}",
          credentialsId: "${CREDENTIALS}",
          scanType: 'fullScan')
      }
    }
    stage('point-scan') {
       steps {
         snInstanceScan(
           url: "${DEVENV}",
           credentialsId: "${CREDENTIALS}",
           scanType: 'pointScan',
           targetTable: 'incident',
           targetRecordSysId: '5b793a6e1bcb6810b54e85d5604bcb09')
       }
    }
    stage('combo-scan') {
      steps {
        snInstanceScan(
          url: "${DEVENV}",
          credentialsId: "${CREDENTIALS}",
          scanType: 'scanWithCombo',
          comboSysId: '12ff94c51b9fa050b54e85d5604bcbc6')
      }
    }
    stage('suite-scan-scoped-apps') {
      steps {
        snInstanceScan(
          url: "${DEVENV}",
          credentialsId: "${CREDENTIALS}",
          scanType: 'scanWithSuiteOnScopedApps',
          suiteSysId: 'fc8d84891b5fa050b54e85d5604bcb6f',
          requestBody: '{app_scope_sys_ids:["9058fcaa1bc36810b54e85d5604bcb12","4de70218db3a6810f0eb52c8dc961979"]}')
      }
    }
    stage('suite-scan-update-sets') {
      steps {
        snInstanceScan(
          url: "${DEVENV}",
          credentialsId: "${CREDENTIALS}",
          scanType: 'scanWithSuiteOnUpdateSets',
          suiteSysId: 'fc8d84891b5fa050b54e85d5604bcb6f',
          requestBody: '{update_set_sys_ids: ["0f4ccd0ddb9f10108552ff561d961923","3dfac1fddbf9a4d0f0eb52c8dc9619b2"]}')
      }
    }
  }
}
