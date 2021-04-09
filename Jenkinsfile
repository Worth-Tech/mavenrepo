

pipeline{
agent { label 'dev' }
stages{
stage('checkout'){
steps{
checkout([$class: 'GitSCM', 
    branches: [[name: '*/master']], 
    userRemoteConfigs: [[credentialsId: '9a7ff67e-43e0-4e28-8dc3-2a1a104aab3c', url: 'https://github.com/Worth-Tech/mavenrepo.git']]
])


     }
   }
stage('build'){
steps{
sh "mvn package"
}
                    }
stage('sonar'){
steps{
withSonarQubeEnv('hari9'){
sh "mvn sonar:sonar"
}
      }
   }
stage('deploy'){
steps{

sh "scp target/*.war 52.15.82.150:/var/lib/tomcat/webapps" 

}
}
  }
}
