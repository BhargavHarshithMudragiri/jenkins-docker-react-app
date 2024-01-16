node {   
    stage('Clone Github repository') {
        git credentialsId: 'github', url: 'https://github.com/BhargavHarshithMudragiri/jenkins-docker-react-app.git'
    }
    
    stage('Build image') {
       dockerImage = docker.build("react-app:v1")
    }
    
    stage('Push image') {
       withDockerRegistry([ credentialsId: "docker", url: "https://hub.docker.com/repositories/bhargavharshith" ]) {
       dockerImage.push()
        }
    }    

    stage('Stop and Kill existing container with same name if any') {
        sh "docker rm -f react-app"
    }
        
    stage('Run the container Locally on the Jenkins server') {
        sh "docker run -itd --name bhargav-app -p 80:80 react-app:v1"
     
    }
  }
