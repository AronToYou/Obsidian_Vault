Server for building, testing, and deploying software.
# Components
## Nodes
A machine capable of executing Pipelines or jobs.
### Jenkins Controller
A single Node which executes tasks, stores configuration / plugins, and renders user interfaces.
### Agents
Node employed by Controller to execute jobs: builds, etc.
### Executor
A slot of execution defined by a Pipeline or job on a Node

# Plugins
### Pyenv Pipeline
Allows execution of `sh` or `bat` Pipeline step commands within a Python virtualenv
# Examples
```groovy
/* Jenkinsfile */
pipeline {  // Requires Docker Pipeline Plugin
    agent { docker { image 'php:8.3.9-alpine3.20' } }
    stages {
        stage('build') {
            steps {
                sh 'php --version'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('Test') {
		    steps {
			    sh './gradlew check'
		    }
	    }
        stage('Deploy') {
	        when {
		        branch 'production'
	        }
            steps {
                retry(3) {
                    sh './flakey-deploy.sh'
                }
                timeout(time: 3, unit: 'MINUTES') {
                    sh './health-check.sh'
                }
            }
        }
    }
    environment {
	    DISABLE_AUTH = 'true'
	    DB_ENGINE = 'sqlite'
    }
    post {
        always {
	        archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
            junit 'build/reports/**/*.xml'
            deleteDir()
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
```