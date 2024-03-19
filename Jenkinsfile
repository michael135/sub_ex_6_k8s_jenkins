pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                // Clean the workspace before cloning
                deleteDir()
            }
        }
        stage('delete all deployments') {
            steps {
                sh 'kubectl delete deployments --all'
            }
        }

        stage('get pods') {
            steps {
                
                sh 'kubectl get pods'
                }
            }

        stage('apply deploymet') {
            steps {
                dir('/home/michaeld/devops_course/big_ex1/sub_ex_6_k8s_jenkins') {
                sh 'kubectl apply -f ex5-deployment.yaml'
            }
        }

           stage('apply service') {
            steps {
                sh 'kubectl apply -f ex5-service.yaml'
            }
        }

        stage('Verify K8S') {
            steps {
                sh 'kubectl get pods'
            }
        }


        stage('Check IP') {
            steps {
                sh 'minikube ip'
            }
        }
    }
}