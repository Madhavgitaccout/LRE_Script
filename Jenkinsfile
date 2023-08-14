pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from Git repository
                checkout scm
            }
        }
        
        stage('Run LoadRunner Script') {
            steps {
                script {
                    // Example: Run LoadRunner script using LRE API
                    def response = httpRequest(
                        url: 'https://lre-server/api/v3/projects/PROJECT_ID/scripts/SCRIPT_ID/runs',
                        authentication: 'LRE_API_CREDENTIALS',
                        contentType: 'APPLICATION_JSON',
                        httpMode: 'POST',
                        requestBody: '{"duration": 3600}'
                    )
                    
                    echo "LoadRunner script run status: ${response.status}"
                }
            }
        }
    }
}
