 def environment = "SIT"

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
               echo "${environment}"
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo \"${environment}\"
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
