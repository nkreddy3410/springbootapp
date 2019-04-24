pipeline {
    agent any
    tools { 
        maven 'Maven 3.6' 
        jdk 'jdk 9.0' 
    }
    
    stages {
        stage ('Initialize') {
            steps {
                echo "${PATH}"
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }
    
        stage('Build') {
            steps {
                 echo 'This is a minimal pipeline.'
                 sh 'mvn clean install'
             
            }
    }
        
        stage('Deploy') {
            steps {
                 echo 'Deploying started .'
                 sh connect 
                 sh deploy D:\workspace-sts-3.9.7.RELEASE\gs-serving-web-content-complete\target\gs-serving-web-content-0.1.0.war
             
            }
    }
    }
}
