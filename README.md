# KubernetesJenkinsCICDPipeline
In this project I am creating a kubernetes cluster with a jenkins master, I will use jenkins to deploy to dockerhub and slaves

Create a kubernetes cluster with one slave node

Create a namespace jenkins
kubectl create ns jenkins

Install Jenkins on the jenkins master node

Get all the files to create jenkins deployment, services, pv, pvc etc

Apply the different yaml files to install jenkins and the services in the namespace
kubectl -n jenkins apply -f jenkins-deployment.yaml
kubectl -n jenkins apply -f jenkins-pv.yaml
kubectl -n jenkins apply -f pvc.yaml
kubectl -n jenkins apply -f service.yaml
kubectl -n jenkins apply -f rbac.yaml

to see the pods
kubectl -n jenkins get pods
 
to see the services
kubectl -n jenkins get svc

to see the logs and get the password to get into jenkins
kubectl -n jenkins logs jenkins-b4d464798-kgnd9 

you will see the password copy and paste in the browser
2a07abf46ba844299b32fae96b19aabe

portforward to port 8080 to go into the terminal
kubectl -n jenkins port-forward jenkins-b4d464798-kgnd9 8080

unlock with the password
install the default plugins
create your password
continue
start using jenkins

manage jenkins
manage plugins
available
kubernetes
install with downloading
after downloading
logout and login again

manage jenkins
manage clouds and nodes
configure clouds

add cloud kubernetes


