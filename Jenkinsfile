pipeline{
  agent{label 'minikube-agent'}
  stages{
      stage('Create Secret'){
          steps{
            git branch: 'main', url: 'https://github.com/lolverae/warehouse-deploy.git'
                
                script{
                    sh'''#!/bin/bash
                    kubectl create ns warehouse-ns
                    kubectl create secret generic db-user-pass --from-literal=username=username --from-literal=password=password -n warehouse-ns
                    '''
                }
          }
      }
      
      stage('K8s apply'){
          steps{
              script{
                  sh'''#!/bin/bash
                  kubectl apply -f ./api/,./database/
                  sleep 10
                  kubectl get svc
                  '''
              }
          }
      }
    //   stage('k8s clean up'){
    //       steps {
    //           script{
    //               sh'''#!/bin/bash
    //               kubectl delete -f ./api/,./database/
    //               kubectl delete ns warehouse-ns
    //                kubectl delete secrets db-user-pass
    //               '''
    //           }}
    //   }
          
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
