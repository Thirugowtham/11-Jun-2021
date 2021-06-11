node() {
   def mvnHome
   stage('Preparation') { 
      
      git 'https://github.com/devopsguru91/simple-maven-project-with-tests'
                
      mvnHome = tool 'Maven 3.6.3' 
   }
   stage('Build') {
      
       sh '"$mvnHome/bin/mvn" -Dmaven.test.failure.ignore clean package' 
      
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
