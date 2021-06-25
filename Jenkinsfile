node() {
   def mvnHome
   stage('Preparation') { 
      
      git 'https://github.com/devopsguru91/simple-maven-project-with-tests'
                
      mvnHome = tool 'M3' 
   }
   stage('Build') {
      
       sh '"$mvnHome/bin/mvn" -Dmaven.test.failure.ignore clean package' 
      
   }
   
   stage('deploy') {
      
       sh 'curl -v --user admin:password  -X PUT  "http://13.212.250.35:8081/artifactory/mavenrepo1/simple-maven-project-with-tests-1.0-SNAPSHOT.jar"' 
      
   }
      
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
