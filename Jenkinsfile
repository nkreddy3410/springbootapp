
def environment
pipeline {
    agent any
    tools { 
        maven 'Maven 3.6' 
        jdk 'jdk 9.0' 
    }
    
    stages {
        stage ('Initialize') {
            steps {
                environment = "SIT"
                echo "${PATH}"
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    "${environment}"
                ''' 
            }
        }
    
        stage('Build') {
            steps {
                 echo 'This is a minimal pipeline.'
                 sh 'mvn clean install'
             
            }
    }
    }
}
