pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                checkout scm
            }

        }
        stage('Argon Manifest') {
          environment { 
            argonToken = "375f5e23-f2c1-4306-9896-53455f4f9100" 
            argonManifestUrl = "https://staging-billy.argon.io"
            githubToken = "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"
                    }
          steps {
              sh """
                    pwd
                    curl -L ${argonManifestUrl}/v1/api/download/sh -H "Authorization: Bearer ${argonToken}" | sh -s ${argonToken}
                    /usr/local/bin/billy generate --artifact-path "${WORKSPACE}" --access-token ${githubToken} --argon-token ${argonToken}
                """
          }
        }
    }
}
