@Library('shared-library') _

pipeline {
    agent any
    parameters {
        string(name: 'restore_from_backup_table_address', defaultValue: '', description: 'Address of the backup table')
        string(name: 'restore_from_backup_time', defaultValue: '', description: 'Time to restore the backup')
    }
    stages {
        stage('Restore DynamoDB Table') {
            when {
                expression {
                    return params.restore_from_backup_table_address?.trim() && params.restore_from_backup_time?.trim()
                }
            }
            steps {
                script {
                    restoreDynamoDBTable(env, params.restore_from_backup_table_address, params.restore_from_backup_time)
                }
            }
        }
    }
}
