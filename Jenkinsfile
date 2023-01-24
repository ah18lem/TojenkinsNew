pipeline {
  agent any
  stages {
    stage("test") {
      steps {
      bat 'gradlew test'
      junit 'build/test-results/test/TEST-Matrix.xml'
         cucumber buildStatus: 'UNSTABLE',
                reportTitle: 'My report',
                fileIncludePattern: 'target/*.json',
           
           trendsLimit: 10
        }
       stage('Code Analysis') {
          steps {
            withSonarQubeEnv('sonar') {
              bat 'gradle sonar'
            }
          }
        }
    
    }
    
    
    
    
}

}
