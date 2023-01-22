pipeline {
  agent any
  stages {
    stage("test") {
      steps {
      bat 'gradlew test'
         junit 'build/test-results/test/TEST-Matrix.xml'
        
      }
    
    }
    
    
    
}

}
