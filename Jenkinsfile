// Sample script for /sn_cicd/app_repo/install for app customization feature

pipeline {
    agent any

    // parameters {
    //         snParam(
    //             credentialsForPublishedApp: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
    //             instanceForPublishedAppUrl: "https://chiarngqdemoauthor.service-now.com",
    //             credentialsForInstalledApp:"f15c53d0-25d0-41ab-adce-3f60e6bc9217",
    //             instanceForInstalledAppUrl:"https://chiarngqdemoclient.service-now.com",
    //             appScope: "x_fxi_afioristore2",
    //             publishedAppVersion: '4.3.9'
    //         )
    // }

    stages {
        // stage('publishing') {
        //     steps {
        //         snPublishApp appVersion: '4.3.9'
        //     }
        // }
        stage('installation') {
            steps {
                snInstallApp(
                    url: "https://chiarngqdemoclient.service-now.com",
                    credentialsId: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                    appScope: "x_fxi_afioristore2",
                    appVersion: "4.3.9",
                    baseAppAutoUpgrade: false)
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