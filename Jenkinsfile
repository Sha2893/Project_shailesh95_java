@Library('Jenkins_shared_Lib') _

pipeline{
    agent any
    
  stages{
         
     stage('Git Checkout'){
        steps{

      gitCheckout(
        branch: 'main' 
        url: 'https://github.com/Sha2893/Project_shailesh95_java.git'
      )
    }
    }

     stage ('Unit test maven')

     steps{
        
        script{
            mvnTest()
        }
     }

     stage ('maven intgration test')

     steps{
        
        script{
            mavenIntegrationTest()
        }
     }

}
   
}