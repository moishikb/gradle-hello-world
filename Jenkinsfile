node('slave1')
{
  def gradle4 = tool 'gradle4'
  stage('GET_RPO_FROM_GIT')
  {
    checkout scm
  }
  stage('BUILD')
  {
    sh '"${gradle4}"/bin/gradle build --info'
  }
}
