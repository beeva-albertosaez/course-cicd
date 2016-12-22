
node('master') {
  stage('Checkout') {
    deleteDir()
    git credentialsId: 'Jenkins RSA', url: 'git@github.com:beeva-albertosaez/course-cicd.git'
  }

  stage('Test') {
    sh './simplehttpserver/tests/unittests.sh ./simplehttpserver/'
  }

  stage('Package and publish') {
    sh "tar -zcvf simplehttpserver-${env.JOB_NAME}-${env.BUILD_ID}.tar.gz ./simplehttpserver"
    sh "aws s3 cp simplehttpserver-${env.JOB_NAME}-${env.BUILD_ID}.tar.gz s3://clase-gendevops2-cicd-ci/"
  }
}
