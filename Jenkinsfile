node('slave1')
{
   gradle4 = tool 'gradle4'
  stage('GET_RPO_FROM_GIT')
  {
    checkout scm
  }
  stage('BUILD')
  {
    sh "${gradle4}/bin/gradle build --info"
  }
   stage('unit-test')
   {
       sh "${gradle4}/bin/gradle test"
   }
   stage('func-test')
   {
      def taskstorun =[:]
      tests = ["one":{sh "test-data/int-test.sh build/libs/oto-gradle-1.0.jar otoMato 'Hello Otomato!'"},"two":{sh "test-data/int-test.sh build/libs/oto-gradle-1.0.jar mosheBoim 'Hello Mosheboim!'"},"three":{sh "test-data/int-test.sh build/libs/oto-gradle-1.0.jar davidSalkin 'Hello Davidsalkin!'"}]
      for (int i =0; i < 3; i++)  {     
         taskstorun["${i}"] = {
            node ()
            {
               stage("step_${i}")
               {
                  tests["${i}"]
               }
           }
         }
      }
      parallel taskstorun
   }
}
