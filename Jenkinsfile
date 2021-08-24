pipeline{
  agent{label 'minikube-agent'}
  stages{
      stage('Create Secret'){
          steps{
            git branch: 'main', url: 'https://github.com/lolverae/warehouse-deploy.git'
            sh 'kubectl create secret generic db-user-pass --from-literal=username=username --from-literal=password=password'
          }
      }
      
      stage('K8s apply'){
          steps{
              script{
                  sh'''!#/bin/bash
                  kubectl apply -f ./kubernetes/api/,./kubernetes/database/
                  sleep 10
                  kubectl get svc
                  '''
              }
          }
      }
      stage('k8s clean up'){
          steps {
            sh 'kubectl delete -f ./kubernetes/api/,./kubernetes/database/'
          }
      }
          
  }
// post {
//       always {
//         echo 'One way or another, I have finished'
//         deleteDir() /* clean up our workspace */
//       }
//       success {
//         echo 'I succeeded! ✔✔'
//       }
//       unstable {
//         echo 'I am unstable :/'
//       }
//       failure {
//         echo 'I failed :('
//       }
//     }
}