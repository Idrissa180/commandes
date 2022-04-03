node{

    stage("SCM Checkout"){
        git credentialsId: 'git-credentials', url: 'https://github.com/enoch180/commandes.git'
    }

    stage("Build Docker Image"){
        sh "docker build -t enoch180/commandes:1.0 ."
    }

    stage("Push Docker Image"){
        withCredentials([string(credentialsId: 'docker-pwd', variable: 'pwd')]) {
            sh "docker login -u enoch180 -p ${pwd}"
        }
        sh "docker push enoch180/commandes:1.0"
    }
    
}
