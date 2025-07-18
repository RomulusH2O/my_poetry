pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Git Show Test') {
            steps {
                script {
                    checkout scm
                    def gitShow = sh(
                    script: 'git show HEAD~1:pyproject.toml',
                    returnStdout: true
                    ).trim()
                    echo "PyProject contents: ${gitShow}"
                }
            }
        }
    }
}
