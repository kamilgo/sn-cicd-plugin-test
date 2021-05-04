pipeline {
  agent any
//  parameters {
    // ServiceNow Parameters should be created by selecting the option 'This build is parameterized' in job configuration.
    // Otherwise it won't be possible to pass variables between publish -> install steps.
    // snParam(...)
//  }
  environment {
    BRANCH = "master"
    APPSYSID = 'a5116141d0835010f8770be4e4ff53b0'
    CREDENTIALS = '7b4ca59e-8486-486c-895e-f044a5297447'
    DEVENV = 'https://chiarngqdemoauthor.service-now.com'
    TESTENV = 'https://chiarngqdemoauthor.service-now.com'
    PRODENV = 'https://chiarngqdemoclient.service-now.com'
    TESTSUITEID = 'b1ae55eedb541410874fccd8139619fb'
    snParam = "${params.snParam}"
  }
  stages {
    stage('Build') {
      steps {
        //snApplyChanges(appSysId: "${APPSYSID}", branchName: "${BRANCH}", url: "${DEVENV}", credentialsId: "${CREDENTIALS}")
        snPublishApp(credentialsId: "${CREDENTIALS}", url: "${DEVENV}", appSysId: "${APPSYSID}",
          isAppCustomization: true, obtainVersionAutomatically: false, appVersion: "4.3.25")
      }
    }
    stage('Install') {
      steps {
        snInstallApp(credentialsId: "${CREDENTIALS}", url: "${TESTENV}", appSysId: "${APPSYSID}", baseAppAutoUpgrade: false)
        //snRunTestSuite(credentialsId: "${CREDENTIALS}", url: "${TESTENV}", testSuiteSysId: "${TESTSUITEID}", withResults: true)
      }
    }
    stage('Deploy to Prod') {
      when {
        branch 'master'
      }
      steps {
        snInstallApp(credentialsId: "${CREDENTIALS}", url: "${PRODENV}", appSysId: "${APPSYSID}", baseAppAutoUpgrade: false)
      }
    }
  }
}
