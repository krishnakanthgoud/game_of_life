pipeline {
    agent any  

    tools {
        maven 'MVN_3.6'  
        jdk 'JDK_8'          
    }

     stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/krishnakanthgoud/game_of_life'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('SonarQube Analysis') {
            steps {
                 tools {
                 jdk 'JDK_8'
                }
                withSonarQubeEnv('mysonarsever') {  // Replace 'SonarQube' with your server name
                    sh """
                        mvn sonar:sonar \
                       -Dsonar.projectKey=gameoflife \
                       -Dsonar.host.url=http://18.60.216.4:9000 \
                       -Dsonar.login=sqp_ddf540b21aa645968a265f975302033f3db387ed
                    """
                }
            }
        }


        
          }
}