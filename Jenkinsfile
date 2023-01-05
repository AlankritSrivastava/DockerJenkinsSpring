node {
    def WORKSPACE = "/var/lib/jenkins/workspace/SpringApp"
    def dockerImageTag = "springapp${env.BUILD_NUMBER}"

    try{
         stage('Clone Repo') {
            // for display purposes
            // Get some code from a GitHub repository
            git url: 'https://github.com/AlankritSrivastava/DockerJenkinsSpring.git',
                branch: 'master'
         }
          stage('Build docker') {
                 dockerImage = docker.build("springapp:${env.BUILD_NUMBER}")
          }

          stage('Deploy docker'){
                  echo "Docker Image Tag Name: ${dockerImageTag}"
                  sh "docker stop springapp || true && docker rm springapp || true"
                  sh "docker run --name springapp -d -p 8080:8080 springapp:${env.BUILD_NUMBER}"
          }
    }catch(e){
        throw e
    }
}
