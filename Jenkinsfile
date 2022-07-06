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
            sh 'set +x; chmod 777 mvnw'
            sh './mvnw clean build'
         }
      }
        
      // stage('SAST') {
      //    steps {
      //       withCredentials([string(credentialsId: 'sonarcloud', variable: 'SONARPAT')]) {
      //            figlet 'SAST'
      //            sh('set +x; ./mvnw sonarqube -Dsonar.login=$SONARPAT -Dsonar.branch.name=feature-jenkins')
      //       }
      //    }
      // }
        
      stage('SCA') {
        steps {
            figlet 'SCA'
            //sh "$SCA --project 'spring-clinic' --scan '${WORKSPACE}/build/libs/pet-clinic-2.6.0.jar'"
            echo '************* SBOM CYCLONEDX *************'
            //sh "./gradlew cyclonedxBom -info"
        }
     }
        
   }
}
