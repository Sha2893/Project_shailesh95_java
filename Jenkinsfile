@Library('Jenkins_shared_Lib') _

pipeline{
    agent any
    
  stages{
         
     stage('Git Checkout'){
        step{

      gitCheckout(
        git branch: 'main' 
        url: 'https://github.com/Sha2893/Project_shailesh95_java.git'
      )
    }
    }

     stage ('Unit test maven')

     step{
        
        script{
            mvnTest()
        }
     }

}
   
}