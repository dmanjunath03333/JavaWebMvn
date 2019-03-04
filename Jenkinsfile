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
   
    
    stage ('Deploy') {
      steps {
        sh "java -jar target/JavaWeb.war"
      }
    }
    
    stage ('Upload') {
     
      steps { 
       
        sh 'curl -X PUT -u admin:password -T target/JavaWeb.war "http://34.220.250.148:8081/artifactory/libs-snapshot-local/JavaWeb.war" '
      }
    }
      
 
          
          
  }

}
