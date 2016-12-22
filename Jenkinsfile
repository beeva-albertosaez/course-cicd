
node('master') {
  stage('Checkout') {
    deleteDir()
    git credentialsId: 'Jenkins RSA', url: 'git@github.com:beeva-albertosaez/course-cicd.git'
  }

  stage('Test') {
    sh './simplehttpserver/tests/unittests.sh ./simplehttpserver/'
  }
}
