node('master')
    {
stage('scm'){
git changelog: false, credentialsId: 'goluser1', poll: false, url: 'https://github.com/Adithiyan91/game-of-life.git'
}
stage('build'){
    sh 'mvn package'
     dir('/var/lib/jenkins/workspace/ansiblejob/gameoflife-web/target/'){
    stash name: 'war', includes: '*.war'
     }
}

node('ansiblemaster'){
stage('copy war to ansible server'){
    dir('/home/ansible/opt/webapps'){
        unstash: 'war'
    }

  }
}
}
