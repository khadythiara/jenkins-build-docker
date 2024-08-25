pipeline{

agent any
def app
stages{
stage('clone'){
	checkout SCM
}

stage('build image'){ 
        app = docker.build("khady/ngnix")
}
stage('test image'){ 
        docker.image('khady/ngnix').withRun('-p 80:80') { c ->
	sh 'docker ps'
	sh 'curl localhost'


}
}

}

}
