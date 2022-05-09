node('maven') {
   stage('checkout sonar')
   git url: 'https://github.com/rajumukkisa1/sonar.git'

   stage('change to working dir')
   dir('sonar'){

       stage('execute sonar') {

       SONARQUBE_PWD = sh (
         script: 'oc env dc/sonarqube --list | awk  -F  "=" \'/SONARQUBE_ADMINPW/{print $2}\'',
         returnStdout: true
          ).trim()
       echo "SONARQUBE_PWD: ${SONARQUBE_PWD}"

       SONARQUBE_URL = sh (
           script: 'oc get routes -o wide --no-headers | awk \'/sonarqube/{ print match($0,/edge/) ?  "http://"$2 : "https://"$2 }\'',
           returnStdout: true
              ).trim()
       echo "SONARQUBE_URL: ${http://localhost:9000/}"

       sh "./gradlew sonarqube -Dsonar.host.url=\"${http://localhost:9000}\" -Dsonar.verbose=true --stacktrace"

       }
   }
}
