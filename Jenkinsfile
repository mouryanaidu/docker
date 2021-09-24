node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       app = docker.build("mouryanaidu/test")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://10.20.3.10:5000, 'git') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
