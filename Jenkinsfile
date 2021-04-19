pipeline { 
  agent none
  stages {
    stage('Test unitaire') {
      agent {
        label 'agent_java'
      }
      steps {
        sh 'mvn test'
      }
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }
      }
    }
    stage('Compilation') {
      agent {
        label 'agent_java'
      }
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Publication') {
      agent {
        label 'Linux'
      steps {
        sh 'echo " hello world "'
        sh "curl -u admin:admin --upload-file target/*.jar 'http://10.10.20.31:8081/repository/depot_test/test.jar'"
      //sh "curl -u admin:Shaymin122 --upload-file target/*.war 'http://84.39.43.46:8081/repository/depot_test/rondoudou${BUILD_NUMBER}.war'"     
      }
    }
  }
}
 
