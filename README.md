# KubernetesJenkinsCICDPipeline
- In this project Jenkins is installed using an ansible playbood, this creates the pv, pvc and services  required for jenkins

# Create 4 ec2 instances with an ansible controller and enough instances for a master and 2 nodes
# Create a kubernetes cluster using the Ansible-playbook-k8s-setup repo

## install jenkins in this cluster
# Create a namespace jenkins
- kubectl create ns jenkins

# clone the directory that has all the yaml files
- git clone https://github.com/nalapatt/AnsibleDeployJenkinsKubeCluster
- cd AnsibleDeployJenkinsKubeCluster
- 
# Install Jenkins on the jenkins master node
# Get all the files to create jenkins deployment, services, pv, pvc etc

- Apply the different yaml files to install jenkins and the services in the namespace
- kubectl -n jenkins apply -f jenkins-deployment.yaml
- kubectl -n jenkins apply -f pv.yaml
- kubectl -n jenkins apply -f pvc.yaml
- kubectl -n jenkins apply -f service.yaml
- kubectl -n jenkins apply -f rbac.yaml

# to see the pods
- kubectl -n jenkins get pods
 
# to see the services
- kubectl -n jenkins get svc

# to see the logs and get the password to get into jenkins
- kubectl -n jenkins logs jenkins-b4d464798-kgnd9 ( this is the name of the pod it will be different for you )

# you will see the password copy and paste in the browser
88af960bf4a54d24b82fb4aee4ddf6db
- 2a07abf46ba844299b32fae96b19aabe ( this will be different for you)

# portforward to port 8080 to go into the terminal
- kubectl -n jenkins port-forward jenkins-b4d464798-kgnd9 8080

# unlock with the password
- install the default plugins
- create your password
- continue
- start using jenkins

# install kubernetes plugin
- manage jenkins
- manage plugins
- available
- kubernetes
- install with downloading
- after downloading
- logout and login again

# install nodes and configure 
- manage jenkins
- manage clouds and nodes
- configure clouds

- add cloud kubernetes



