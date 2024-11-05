pipeline {
    agent any

triggers{
pollSCM('*****')
}

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
      
stage("Couverture de code") {
            steps {
                sh "./gradlew jacocoTestReport"
                publishHTML(target: [
                    reportDir: 'build/reports/jacoco/test/html',
                    reportFiles: 'index.html',
                    reportName: "Rapport JaCoCo"
                ])
                sh "./gradlew jacocoTestCoverageVerification"
            }
   }
 stage("Analyse statique du code") {
      steps {
           sh "./gradlew checkstyleMain"
           publishHTML (target: [
           reportDir: 'build/reports/checkstyle/',
           reportFiles: 'main.html',
           reportName: "Checkstyle Report"
])
           }
        }
 }
}
