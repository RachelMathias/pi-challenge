pipeline {
    agent any
    options {
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
        timeout(time: 12, unit: 'HOURS')
        timestamps()
    }
    stages {
        stage('Requirements') {
            steps {
                // Using Git Bash to make the script executable
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c "chmod +x $WORKSPACE/algorithm.sh"'
            }
        }
        stage('Build') {
            steps {
                // Using Git Bash to execute the script
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c "$WORKSPACE/algorithm.sh"'

                // Archiving the report
                archiveArtifacts allowEmptyArchive: true,
                    artifacts: '*.txt',
                    fingerprint: true,
                    onlyIfSuccessful: true
            }
        }
    }
}
