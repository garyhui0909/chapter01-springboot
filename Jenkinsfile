node {
  stage("Clone the project") {
    git branch: 'main', url: 'https://github.com/garyhui0909/chapter01-springboot.git'
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