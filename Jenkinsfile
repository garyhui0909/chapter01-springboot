node {
  stage("Clone the project") {
    git branch: 'main', url: 'https://github.com/garyhui0909/chapter01-springboot.git'
  }

  stage("Code Scan") {
    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=test -Dsonar.host.url=http://host.docker.internal:9000 -Dsonar.login=sqp_b2d7639079bd37eb9c3379ae0e3de85dab888e26"
  }

  stage("Compilation") {
    sh "mvn clean install -DskipTests"
  }

  stage("Tests and Deployment") {
    stage("Runing unit tests") {
      sh "mvn test -Punit"
    }
    stage("Deployment") {
      sh 'mvn spring-boot:run -Dserver.port=8081 &'
    }
  }
}