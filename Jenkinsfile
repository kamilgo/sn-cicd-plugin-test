// Sample script for /sn_cicd/app_repo/install for app customization feature
// without ServiceNow Parameters (snParams).

pipeline {
    agent any

 // Required only if we want to initialize ServiceNow Parameters. First build will always fail.
 // Works with 'Trigger builds remotely': http://[JENKINS_HOST]/job/[JOB_NAME]/buildWithParameters?token=[TOKEN]
    parameters {
            snParam(
                description: "ServiceNow Parameters",
                credentialsForPublishedApp: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                instanceForPublishedAppUrl: "https://chiarngqdemoauthor.service-now.com",
                credentialsForInstalledApp:"f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                instanceForInstalledAppUrl:"https://chiarngqdemoclient.service-now.com",
                sysId:'a5116141d0835010f8770be4e4ff53b0',
                appScope: "x_fxi_afioristore2",
                publishedAppVersion: '4.3.24',
                rollbackAppVersion: '',
                progressCheckInterval: null
            )
    }

    stages {
        stage('configuration') {
            steps {
                echo "ServiceNow Parameters: ${params.snParam}"
            }
        }
        stage('publishing') {
            steps {
                snPublishApp(
                    url: "https://chiarngqdemoauthor.service-now.com",
                    credentialsId: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                    appScope: "x_fxi_afioristore2",
                    obtainVersionAutomatically: true,
                    incrementBy: 2)

                echo "ServiceNow Parameters after publishing stage: ${params.snParam}"
            }
        }
        stage('installation') {
            steps {
                snInstallApp(
                    url: "https://chiarngqdemoclient.service-now.com",
                    credentialsId: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                    appScope: "x_fxi_afioristore2",
                    //appVersion: "4.3.11",
                    baseAppAutoUpgrade: false)

                echo "ServiceNow Parameters after installation stage: ${params.snParam}"
            }
        }
        stage('revert-changes') {
            steps {
                snRollbackApp(
                    url: "https://chiarngqdemoclient.service-now.com",
                    credentialsId: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                    appScope: "x_fxi_afioristore2"
                )
            }
        }
    }
}
