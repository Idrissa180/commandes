node{

    stage("SCM Checkout"){
        git credentialsId: 'git-credentials', url: 'https://github.com/enoch180/commandes.git'
    }

    stage("Build Docker Image"){
        sh "docker build -t enoch180/commandes:1.0 ."
    }

    stage("Push Docker Image"){
        withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
            sh "docker login -u dall49 -p ${dockerHubPwd}"
        }
        sh "docker push enoch180/commandes:1.0"
    }
    
    stage("Run Container on Dev Server"){
        sh "docker run -d -p 8081:8080 --name commandes_v1 enoch180/commandes:1.0"
    }
    
}
