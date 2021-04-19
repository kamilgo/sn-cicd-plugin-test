// Sample script for batch install using manifest default file with default name: now_batch_manifest.json
// ServiceNow API: POST /sn_cicd/app/batch/install

pipeline {
    agent any

    parameters {
            snParam(
                description: "ServiceNow Parameters",
                credentialsForPublishedApp: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                instanceForPublishedAppUrl: "https://chiarngqdemoauthor.service-now.com",
                credentialsForInstalledApp:"f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                instanceForInstalledAppUrl:"https://chiarngqdemoclient.service-now.com",
                sysId:'',
                appScope: "x_fxi_afioristore2",
                publishedAppVersion: '4.3.10',
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
        stage('install-batch') {
             steps {
                 snBatchInstall(
                     url: 'https://chiarngqdemoclient.service-now.com'
                    ,credentialsId: 'f15c53d0-25d0-41ab-adce-3f60e6bc9217'
                    ,useFile: true
                    //,file: 'now_batch_manifest.json' // not required if this is default file name
                    )

                echo "ServiceNow Parameters after Batch Install: ${params.snParam}"
             }
        }
        
    }
}
