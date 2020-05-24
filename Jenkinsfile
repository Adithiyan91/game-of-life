node('GOLnode'){
stage('scm'){
git changelog: false, credentialsId: 'goluser1', poll: false, url: 'https://github.com/Adithiyan91/game-of-life.git'
}
stage('build'){
    sh 'mvn package'
}
}
