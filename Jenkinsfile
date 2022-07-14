node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("uder/nginx-foobar")
    }

#    stage('Test image') {
#        app.inside {
#            sh 'echo "Tests passed"'
#        }
#    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-creds') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
