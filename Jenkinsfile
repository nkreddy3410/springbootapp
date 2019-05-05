
 //def environment = "SIT"
 //def buildCmd =" mvn clean install"
def envs = loadEnvs()

def loadEnvs(){
 //echo "${params.mainEnvironment}"
 if(params.mainEnvironment=='SIT'){
 
 }else if(params.mainEnvironment=='UAT'){
 
 }else if(params.mainEnvironment=='PROD'){
 }
}

pipeline {
    agent any
 
 parameters {
        string(defaultValue: " mvn clean install", description: 'What command?', name: 'buildCmd')
        choice(choices: ['SIT', 'UAT', 'PROD'], description: 'What Environment ?', name: 'mainEnvironment')
        //choice(choices: envs, description: 'What Environment ?', name: 'environment')
    }
 
    tools { 
        maven 'Maven 3.6' 
        jdk 'jdk 9.0' 
    }
    
    stages {
        stage ('Initialize') {
           
            steps {
               
                echo "${PATH}"
               echo "${params.environment}"
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo '''+params.environment+'''
                '''
            }
        }
    
        stage('Build') {
            steps {
                 echo 'This is a minimal pipeline.'
                 sh ''' '''+params.buildCmd+''' '''
             
            }
    }
    }
}
