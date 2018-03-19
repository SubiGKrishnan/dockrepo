pipeline{
  agent any
  
  stages{
  
    stage('build'){
      
      steps{
            sh(script:'mvn clean install')
      
           }

        }
    stage('build docker image'){

      steps{
          sh(script:'docker build --tag subigkrishnan/dockrepo .')

           }
    }
    
    stage('tag and push docker image'){

      steps{
          sh(script:'docker login -u subigkrishnan -p Subi9999')
          sh(script:'docker tag subigkrishnan/dockrepo subigkrishnan/dockrepo:1.0.2')
          sh(script:'docker push subigkrishnan/dockrepo:1.0.2')
          }

    }

     stage('Run and test container'){

       steps{
          sh(script:'docker run -it -d --name devops-test subigkrishnan/dockrepo:1.0.2')
          sh(script:'docker exec -it devops-test ls /')

            }

     }
    
      }

}
