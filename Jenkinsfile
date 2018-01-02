node('slave1')
{
  stage('GET_RPO_FROM_GIT')
  {
    checkout scm
  }
  stage('BUILD')
  {
    gradle build
  }
}
