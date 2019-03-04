pipeline {
agent any
  tools {
   maven 'maven3.6.0'
    jdk 'java1.8.0'
  }
    
  stages {
    stage('Build') {
          steps {
            sh "mvn -B -DskipTests clean package"
          }
          }
    
    stage ('UnitTest'){
      steps {
        sh "mvn test" 
      }
      post {
        always {
        junit 'target/surefire-reports/*.xml'
        }
      }
    }
    
    stage ('Deploy') {
      steps {
        sh "java -jar target/JavaWeb-0.0.1-SNAPSHOT.war"
      }
    }
    
    stage ('Upload') {
     
      steps { 
       
        sh 'curl -X PUT -u admin:password -T target/JavaWeb-0.0.1-SNAPSHOT.war "http://34.220.250.148:8081/artifactory/libs-snapshot-local/JavaWeb-0.0.1-SNAPSHOT.war" '
      }
    }
      
 
          
          
  }

}
