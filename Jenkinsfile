node('master'){
stage('scm'){
git changelog: false, credentialsId: 'goluser1', poll: false, url: 'https://github.com/Adithiyan91/game-of-life.git'
}
stage('build'){
    sh 'mvn package'
    stash name: 'war', includes: 'x.war'
}
}
node('ansible_control_server'){
stage('copy war to ansible server'){
    dir('/home/ansible/opt/webapps'){
        unstash: 'war'
    }
  }
}