pipeline {
    agent any

    stages {
      
        stage("Compilation") {
            steps {
                // Compilation du code avec Gradle
                sh './gradlew compileJava' // Assurez-vous qu'un script Gradle est présent et exécutable
            }
        }
        stage("test unitaire"){
        steps {
        sh './gradlew test'
        }
      }
      
  stage("Couverture du code") {
    steps {
        sh "./gradlew jacocoTestReport"
        sh "./gradlew jacocoTestCoverageVerification"
    }
   }
 }
}
