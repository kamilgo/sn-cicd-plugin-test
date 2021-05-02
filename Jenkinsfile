pipeline {
  agent any
  parameters {
    snParam(credentialsForPublishedApp: "88dbbe69-0e00-4dd5-838b-2fbd8dfedeb4", instanceForPublishedAppUrl: "https://cicdjenkinsapppublish.service-now.com", sysId: "a5116141d0835010f8770be4e4ff53b0")
  }
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
          isAppCustomization: true, obtainVersionAutomatically: true, incrementBy: 2)
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
