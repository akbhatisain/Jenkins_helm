
# Jenkins Helm Charts

Helm must be installed to use the charts. Please refer to Helm's documentation to get started.
https://helm.sh/docs/


# Building weekly releases

The default charts target Long-Term-Support (LTS) releases of Jenkins. To use other versions, the easiest way is to update the image tag to the version you want. You can also rebuild the chart if you want the appVersion field to match.

#  Helm-Jenkins on running K8s Cluster

- Whenever you trigger a Jenkins job, the Jenkins Kubernetes plugin will make an API call to create a Kubernetes agent pod. Then, the Jenkins agent pod gets deployed in the kubernetes with few environment variables containing the Jenkins server details and secrets.

- When the agent pod comes up, it used the details in its environment variables and talks back to Jenkins using the JNLP method.

# Jenkins Install

    git clone https://github.com/tinkusaini13/Jenkins_helm.git
    cd Jenkins_helm


- After clone reposistory , entered into the  directory, you'll find values.yaml file. Disable the persistence with false if true.

- If your cluster on-premise does not support storage class (like our multipass VM cluster), PVC and PV, disable persistence. But if you are working on minikube, minikube supports PVC and PV automatically.

- If you don't disable persistence, you'll encounter that your PODs will not run (wait pending). You can inspect PVC, PV and Pod with kubectl describe command.

# Install Helm Jenkins Release:

    helm install j1 Jenkins_helm
    helm list
    kubectl get pods
    kubectl get svc
    kubectl get pods -o wide

- To get Default Jenkins username and password:

   - username : admin 
   - password : admin

# Jenkins Configuration

Helm also downloads automatically some of the plugins.

If you need install more plugins then you can define in value.yaml find the installPlugins option and add your plugins for example:


     installPlugins:
       - kubernetes:4186.v1d804571d5d4
       - workflow-aggregator:596
       - git:5.2.1
       - configuration-as-code:1775



Reference another github repo: https://github.com/omerbsezer/Fast-Kubernetes/blob/main/K8s-Helm-Jenkins.md
