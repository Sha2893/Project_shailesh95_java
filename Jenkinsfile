@Library('Jenkins_shared_Lib') _

pipeline{
    agent any

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }
    
  stages{
         
     stage('Git Checkout'){

        when { expression {  params.action == 'create' } }
        steps{ 

      gitCheckout(
        branch: "main",
        url: "https://github.com/Sha2893/Project_shailesh95_java.git"
      )
    }
    }

     stage('Unit test maven'){

        when { expression {  params.action == 'create' } }

     steps{
        
        script{
            mvnTest()
        }
     }
     }

      stage('Integration maven testing '){

        when { expression {  params.action == 'create' } }

     steps{
        
        script{
            mavenIntegrationTest()
        }
     }

}

stage('Static code analysis: Sonarqube'){
         when { expression {  params.action == 'create' } }
            steps{
               script{
                   
                   def SonarQubecredentialsId = 'sonarqube-api'
                   StaticCodeAnalysis(SonarQubecredentialsId)
               }
            }
        }
   
stage('Quality Gate Status Check : Sonarqube'){
         when { expression {  params.action == 'create' } }
            steps{
               script{
                   
                   def SonarQubecredentialsId = 'sonarqube-api'
                   QualityGate(SonarQubecredentialsId)
               }
            }
        }
        stage('Maven Build : maven'){
         when { expression {  params.action == 'create' } }
            steps{
               script{
                   
                   mavenBuild()
               }
            }
        }
  }
}