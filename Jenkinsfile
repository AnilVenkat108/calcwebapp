node {
   def mvnHome
   stage('Git-Checkout') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/AnilVenkat108/calcwebapp.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'localMaven'
      }
   stage('Maven Compile & Unit Test') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Deploy') {
      
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
      sh 'cp target/*.war /opt/tomcat/apache-tomcat-9.0.14/webapps'
   }
}
