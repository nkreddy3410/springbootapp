
 //def environment = "SIT"
 //def buildCmd =" mvn clean install"
def envs = loadEnvs()

def loadEnvs(){
 //echo "${params.mainEnvironment}"
 if(params.mainEnvironment=='SIT'){
 return ['SIT1', 'SIT2', 'SIT3']
 }else if(params.mainEnvironment=='UAT'){
 return ['UAT1', 'UAT2', 'UAT3']
 }else if(params.mainEnvironment=='PROD'){
  return ['PROD1', 'PROD2', 'PROD3']
 }
}

def envs1 = loadEnvs1()

def loadEnvs1(){
 
 return "a\nb\nc"
}
properties([ 
          parameters([

[$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', description: 'Select a choice', filterLength: 1, filterable: true, name: 'choice1', randomName: 'choice-parameter-7601235200970', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: 'return ["ERROR"]'], script: [classpath: [], sandbox: false, script: 'return[\'aaa\',\'bbb\']']]], 
[$class: 'CascadeChoiceParameter', choiceType: 'PT_SINGLE_SELECT', description: 'Active Choices Reactive parameter', filterLength: 1, filterable: true, name: 'choice2', randomName: 'choice-parameter-7601237141171', referencedParameters: 'choice1', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: 'return ["error"]'], script: [classpath: [], sandbox: false, script: 'if(choice1.equals("aaa")){return [\'a\', \'b\']} else {return [\'aaaaaa\',\'fffffff\']}']]]
])
])

pipeline {
    agent any

  parameters {
        string(defaultValue: " mvn clean install", description: 'What command?', name: 'buildCmd')
        choice(choices: ['SIT', 'UAT', 'PROD'], description: 'What Environment ?', name: 'mainEnvironment')
        choice(choices: envs, description: 'What Environment ?', name: 'environment')
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
