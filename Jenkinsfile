pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Detect') {
            steps {
                script {
                    checkout scm

                    def currentVersion = readCurrentVersion()
                    def previousVersion = readPreviousVersion()

                    if (currentVersion != previousVersion) {
                        changeInfo = getSemVerChangeInfo(previousVersion, currentVersion)
                        echo "${changeInfo}"
                    } else {
                        echo "No version change detected"
                    }
                }
            }
        }
    }
}

def readCurrentVersion() {

    def pyProject = readFile('pyproject.toml')
    def matcher = pyProject =~ /version\s*=\s*"([^"]+)"/
    return matcher ? matcher[0][1] : null 
}

def readPreviousVersion() {

    def prevContent = sh(
        script: 'git show HEAD~1:pyproject.toml',
        returnStdout: true
        ).trim()
    def matcher = prevContent =~ /version\s*=\s*"[^"]+)"/
    return matcher ? matcher[0][1] : null
}

def getSemVerChangeInfo(oldVer, newVer) {

    def (oldMajor, oldMinor, oldPatch) = oldVer.tokenize('.').collect { it as int }
    def (newMajor, newMinor, newPatch) = newVer.tokenize('.').collect { it as int }

    if (newMajor > oldMajor) return 'Major version changed from ${oldMajor} to ${newMajor}'
    if (newMinor > oldMinor) return 'Minor version changed from ${oldMinor} to ${newMinor}'
    if (newPatch > oldPatch) return 'Patch version changed from ${oldPatch} to ${newPatch}'
    return 'Version has been changed improperly'
}
