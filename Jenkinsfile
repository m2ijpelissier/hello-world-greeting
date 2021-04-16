pipeline { 
  stages {
    stage('Test unitaire') {
      agent {
        label 'agent_java'
      }
      step {
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
      step {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Publication') {
      step {
      //sh "curl -u admin:Shaymin122 --upload-file target/*.war 'http://84.39.43.46:8081/repository/depot_test/rondoudou${BUILD_NUMBER}.war'"     
      }
    }
  }
}
 
