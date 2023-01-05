node {
    def WORKSPACE = "/var/lib/jenkins/workspace/SpringApp"
    def dockerImageTag = "SpringApp${env.BUILD_NUMBER}"

    try{
         stage('Clone Repo') {
            // for display purposes
            // Get some code from a GitHub repository
            git url: 'https://github.com/AlankritSrivastava/DockerJenkinsSpring.git',
                branch: 'master'
         }
          stage('Build docker') {
                 dockerImage = docker.build("SpringApp:${env.BUILD_NUMBER}")
          }

          stage('Deploy docker'){
                  echo "Docker Image Tag Name: ${dockerImageTag}"
                  sh "docker stop SpringApp || true && docker rm SpringApp || true"
                  sh "docker run --name SpringApp -d -p 8080:8080 SpringApp:${env.BUILD_NUMBER}"
          }
    }catch(e){
        throw e
    }
}
