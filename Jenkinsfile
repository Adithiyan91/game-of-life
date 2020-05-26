node('master'){
stage('scm'){
git changelog: false, credentialsId: 'goluser1', poll: false, url: 'https://github.com/Adithiyan91/game-of-life.git'
}
stage('build'){
    sh 'mvn package'
     dir('/var/lib/jenkins/workspace/ansiblejob/gameoflife-web/target/'){
    stash name: 'war', includes: '*.war'
     }
}
}

node('ansiblemaster'){
    echo "unstash coverage path"
stage('copy war to ansible server'){
    dir('/home/ansible/opt/webapps'){
        unstash name: 'war'

    }
    echo'execute ansible playbook'
    sh 'ansible --version '
    stage('execute ping cmd to all hosts'){
        echo "become a root user"
        become: true
        becomeUser: 
        dir('/etc/ansible'){
                        
             sh 'ansible all -m ping -i /etc/ansible/hosts -u ansible'
        }
    }
    echo 'ansible slave contacted...'
   

  }
}

