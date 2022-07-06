pipeline {
    agent any 

    stages {
      
      stage('SCM') {
         steps {
            checkout scm
         }
      }
        
      stage('BUILD') {
         steps {
            sh 'chmod +x; chmod 777 mvnw'
            sh './mvnw clean build'
         }
      }
        
      stage('SAST') {
         steps {
            sh('set +x; ./mvnw sonarqube -Dsonar.login=2ae30d5987686cf2c4024bdc9945b2ef9c553974 -Dsonar.branch.name=feature-jenkins')
         }
      }
        
      stage('SCA') {
         steps {
            sh "$SCA --project 'spring-clinic' --scan '${WORKSPACE}/build/libs/pet-clinic-2.6.0.jar'"
         }
      }
        
   }
}
