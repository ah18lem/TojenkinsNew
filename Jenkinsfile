pipeline {
  agent any
  stages {
    stage("test") {
      steps {
      bat 'gradlew test'
      junit 'build/test-results/test/TEST-Matrix.xml'
         cucumber buildStatus: 'SUCCESS',
                reportTitle: 'My report',
                fileIncludePattern: 'target/*.json',
           
           trendsLimit: 10
      }}
       stage('Code Analysis') {
          steps {
            withSonarQubeEnv('sonar') {
              bat 'gradlew sonar'
              
            }
          }
        }
    
     stage("Code Quality") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true }
            }
        }
    
    stage('build') {
      steps {
        bat(script: 'gradle build', label: 'gradle build')
        bat 'gradle javadoc'
        archiveArtifacts 'build/libs/*.jar'
        junit(testResults: 'build/reports/tests/test', allowEmptyResults: true)

      }
    }
    
    
    }
    
    
    
    
}


