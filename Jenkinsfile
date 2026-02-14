pipeline {
    agent any
    triggers {
        cron('H/15 * * * *')
        pollSCM('* * * * *') 
        upstream(upstreamProjects: 'Upstream-Job', threshold: hudson.model.Result.SUCCESS)
    }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Deepsundar-Das/maven_practical_14_feb-2026.git'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Building declarative pipeline..." > build_output.txt'
            }
        }
        stage('Echo Build Status') {
            steps {
                echo "Build Stage Completed Successfully!"
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build_output.txt'
            }
        }
    }
}
