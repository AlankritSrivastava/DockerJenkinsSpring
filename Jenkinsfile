node {
    def WORKSPACE = "/var/lib/jenkins/workspace/SpringApp"
    def dockerImageTag = "springdocker${env.BUILD_NUMBER}"

    try{
         stage('Clone Repo') {
            // for display purposes
            // Get some code from a GitHub repository
            git url: 'https://github.com/AlankritSrivastava/DockerJenkinsSpring.git',
                branch: 'master'
         }
          stage('Build docker') {
                 dockerImage = docker.build("springdocker:${env.BUILD_NUMBER}")
          }

          stage('Deploy docker'){
                  echo "Docker Image Tag Name: ${dockerImageTag}"
                  bat "docker stop springdocker || exit 0 && docker rm springdocker || exit 0"
                  bat "docker run --name springdocker -d -p 8081:8080 springdocker:${env.BUILD_NUMBER}"
          }
    }catch(e){
        throw e
    }
}
