pipeline {
    agent any

    tools {
        go 'golang'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/OT-MICROSERVICES/employee-api.git', branch: 'main'
            }
        }

        stage('Compile') {
            steps {
                sh 'go mod tidy'
                sh 'go build -o employee-api main.go'
            }
        }
    }
       post {
    success {
        emailext(
            to: 'sainiabhishek619@gmail.com',
            subject: "Build SUCCESS: ${currentBuild.fullDisplayName}",
            body: """Hello Abhishek,  

Your build has completed successfully. 
code has been compiled """
        )
    }
    failure {
        emailext(
            to: 'sainiabhishek619@gmail.com',
            subject: "Build FAILED: ${currentBuild.fullDisplayName}",
            body: """Hello Abhishek,  

Your build has failed.  """
        )
    }
}
 
}
