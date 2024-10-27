## A List of Kubernetes Commands To Know
**These commands will enable you to manage the Kubernetes Cluster.**

### Cluster Management 
* ***kubectl version***        # Check the version of kubectl
* ***kubectl cluster-info***  # Get the cluster information
* ***kubectl get nodes*** # Get the nodes in the cluster
* ***kubectl get pods*** # Get the pods in the cluster
* ***kubectl get services*** # Get the services in the cluster
* ***kubectl cordon/uncordon <node>*** # To mark node as unschedulable/schedulable
* ***kubectl drain <node>*** # Safely evict all pods from a node

### Namespace Management
* ***kubectl get namespaces*** # Get the namespaces in the cluster
* ***kubectl create namespace mynamespace*** # Create a namespace
* ***kubectl delete namespace mynamespace*** # Delete a namespace
* ***kubectl get pods -n mynamespace*** # Get the pods in a namespace

### Pod Management
* ***kubectl get pods*** # Get the pods in the cluster
* ***kubectl describe pod mypod*** # Describe a pod
* ***kubectl logs mypod*** # Get the logs of a pod
* ***kubectl exec -it mypod -- /bin/bash*** # Execute a command in a pod
* ***kubectl delete pod mypod*** # Delete a pod

### Deployment Management
* ***kubectl get deployments*** # Get the deployments in the cluster
* ***kubectl describe deployment mydeployment*** # Describe a deployment
* ***kubectl scale deployment mydeployment --replicas=3*** # Scale a deployment
* ***kubectl delete deployment mydeployment*** # Delete a deployment

### Service Management
* ***kubectl get services*** # Get the services in the cluster
* ***kubectl describe service myservice*** # Describe a service
* ***kubectl delete service myservice*** # Delete a service

### Ingress Management
* ***kubectl get ingress*** # Get the ingresses in the cluster
* ***kubectl describe ingress myingress*** # Describe an ingress
* ***kubectl delete ingress myingress*** # Delete an ingress

### ConfigMap Management
* ***kubectl get configmaps*** # Get the configmaps in the cluster
* ***kubectl describe configmap myconfigmap*** # Describe a configmap
* ***kubectl delete configmap myconfigmap*** # Delete a configmap

### Secret Management
* ***kubectl get secrets*** # Get the secrets in the cluster
* ***kubectl describe secret mysecret*** # Describe a secret
* ***kubectl delete secret mysecret*** # Delete a secret
* ***kubectl create secret generic <secret-name> --from-literal+<key>=<value>*** # Create a secret

### Role Management
* ***kubectl get roles*** # Get the roles in the cluster
* ***kubectl describe role myrole*** # Describe a role
* ***kubectl delete role myrole*** # Delete a role

### RoleBinding Management
* ***kubectl get rolebindings*** # Get the rolebindings in the cluster
* ***kubectl describe rolebinding myrolebinding*** # Describe a rolebinding
* ***kubectl delete rolebinding myrolebinding*** # Delete a rolebinding

### ServiceAccount Management
* ***kubectl get serviceaccounts*** # Get the serviceaccounts in the cluster
* ***kubectl describe serviceaccount myserviceaccount*** # Describe a serviceaccount
* ***kubectl delete serviceaccount myserviceaccount*** # Delete a serviceaccount

### PersistentVolume Management
* ***kubectl get persistentvolumes*** # Get the persistentvolumes in the cluster
* ***kubectl describe persistentvolume mypersistentvolume*** # Describe a persistentvolume
* ***kubectl delete persistentvolume mypersistentvolume*** # Delete a persistentvolume

### PersistentVolumeClaim Management
* ***kubectl get persistentvolumeclaims*** # Get the persistentvolumeclaims in the cluster
* ***kubectl describe persistentvolumeclaim mypersistentvolumeclaim*** # Describe a persistentvolumeclaim
* ***kubectl delete persistentvolumeclaim mypersistentvolumeclaim*** # Delete a persistentvolumeclaim

### StorageClass Management
* ***kubectl get storageclasses*** # Get the storageclasses in the cluster
* ***kubectl describe storageclass mystorageclass*** # Describe a storageclass
* ***kubectl delete storageclass mystorageclass*** # Delete a storageclass

### PodSecurityPolicy Management
* ***kubectl get podsecuritypolicies*** # Get the podsecuritypolicies in the cluster
* ***kubectl describe podsecuritypolicy mypodsecuritypolicy*** # Describe a podsecuritypolicy
* ***kubectl delete podsecuritypolicy mypodsecuritypolicy*** # Delete a podsecuritypolicy

### NetworkPolicy Management
kubectl get networkpolicies # Get the networkpolicies in the cluster
kubectl describe networkpolicy mynetworkpolicy # Describe a networkpolicy
kubectl delete networkpolicy mynetworkpolicy # Delete a networkpolicy

### ResourceQuota Management
kubectl get resourcequotas # Get the resourcequotas in the cluster
kubectl describe resourcequota myresourcequota # Describe a resourcequota
kubectl delete resourcequota myresourcequota # Delete a resourcequota

### LimitRange Management
* ***kubectl get limitranges*** # Get the limitranges in the cluster
* ***kubectl describe limitrange mylimitrange*** # Describe a limitrange
* ***kubectl delete limitrange mylimitrange*** # Delete a limitrange

### CronJob Management
* ***kubectl get cronjobs*** # Get the cronjobs in the cluster
* ***kubectl describe cronjob mycronjob*** # Describe a cronjob
* ***kubectl delete cronjob mycronjob*** # Delete a cronjob

### Job Management
* ***kubectl get jobs*** # Get the jobs in the cluster
* ***kubectl describe job myjob*** # Describe a job
* ***kubectl delete job myjob*** # Delete a job

### PodDisruptionBudget Management
* ***kubectl get poddisruptionbudgets*** # Get the poddisruptionbudgets in the cluster
* ***kubectl describe poddisruptionbudget mypoddisruptionbudget*** # Describe a poddisruptionbudget
* ***kubectl delete poddisruptionbudget mypoddisruptionbudget*** # Delete a poddisruptionbudget

### HorizontalPodAutoscaler Management
* ***kubectl get horizontalpodautoscalers*** # Get the horizontalpodautoscalers in the cluster
* ***kubectl describe horizontalpodautoscaler myhorizontalpodautoscaler*** # Describe a horizontalpodautoscaler
* ***kubectl delete horizontalpodautoscaler myhorizontalpodautoscaler*** # Delete a horizontalpodautoscaler

### PriorityClass Management
* ***kubectl get priorityclasses*** # Get the priorityclasses in the cluster
* ***kubectl describe priorityclass mypriorityclass*** # Describe a priorityclass
* ***kubectl delete priorityclass mypriorityclass*** # Delete a priorityclass

### PodPreset Management
* ***kubectl get podpresets*** # Get the podpresets in the cluster
* ***kubectl describe podpreset mypodpreset*** # Describe a podpreset
* ***kubectl delete podpreset mypodpreset*** # Delete a podpreset

### CustomResourceDefinition Management
* ***kubectl get customresourcedefinitions*** # Get the customresourcedefinitions in the cluster
* ***kubectl describe customresourcedefinition mycustomresourcedefinition*** # Describe a customresourcedefinition
* ***kubectl delete customresourcedefinition mycustomresourcedefinition*** # Delete a customresourcedefinition

### ClusterRole Management
* ***kubectl get clusterroles*** # Get the clusterroles in the cluster
* ***kubectl describe clusterrole myclusterrole*** # Describe a clusterrole
* ***kubectl delete clusterrole myclusterrole*** # Delete a clusterrole

### ClusterRoleBinding Management
* ***kubectl create rolebinding <binding-name> --role-<role-name> --user=<user>*** # Bind a role to a user
* ***kubectl get clusterrolebindings*** # Get the clusterrolebindings in the cluster
* ***kubectl describe clusterrolebinding myclusterrolebinding*** # Describe a clusterrolebinding
* ***kubectl delete clusterrolebinding myclusterrolebinding*** # Delete a clusterrolebinding

### PodSecurityPolicy Management
* ***kubectl get podsecuritypolicies*** # Get the podsecuritypolicies in the cluster
* k***ubectl describe podsecuritypolicy mypodsecuritypolicy*** # Describe a podsecuritypolicy
* ***kubectl delete podsecuritypolicy mypodsecuritypolicy*** # Delete a podsecuritypolicy

### NetworkPolicy Management
* ***kubectl get networkpolicies*** # Get the networkpolicies in the cluster
* ***kubectl describe networkpolicy mynetworkpolicy*** # Describe a networkpolicy
* ***kubectl delete networkpolicy mynetworkpolicy*** # Delete a networkpolicy

### ResourceQuota Management
* ***kubectl get resourcequotas*** # Get the resourcequotas in the cluster
* ***kubectl describe resourcequota myresourcequota*** # Describe a resourcequota
* ***kubectl delete resourcequota myresourcequota*** # Delete a resourcequota

### LimitRange Management
* ***kubectl get limitranges*** # Get the limitranges in the cluster
* ***kubectl describe limitrange mylimitrange*** # Describe a limitrange
* ***kubectl delete limitrange mylimitrange*** # Delete a limitrange

### Kubectl Configuration
* ***kubectl config view*** # View the kubectl configuration
* ***kubectl config get-contexts*** # Get the kubectl contexts
* ***kubectl config use-context mycontext*** # Use a kubectl context
* ***kubectl config set-context mycontext --namespace=mynamespace*** # Set the namespace for a kubectl context
* ***kubectl config delete-context mycontext*** # Delete a kubectl context
* ***kubectl config set-cluster mycluster --server=https://myserver:6443 --certificate-authority=myca.crt --embed-certs=true*** # Set a cluster for a kubectl context
* ***kubectl config set-credentials myuser --client-certificate=myuser.crt --client-key=myuser.key --embed-certs=true*** # Set a user for a kubectl context

### YAML Configuration
* ***kubectl apply -f myconfig.yaml*** # Apply a configuration from a file
* ***kubectl get -f myconfig.yaml*** # Get a configuration from a file
* ***kubectl describe -f myconfig.yaml*** # Describe a configuration from a file
* ***kubectl delete -f myconfig.yaml*** # Delete a configuration from a file

### Kubectl Plugins
* ***kubectl krew install get-all*** # Install the get-all plugin
* ***kubectl get all*** # Get all resources in the cluster
* ***kubectl krew uninstall get-all*** # Uninstall the get-all plugin
* ***kubectl krew install get-all-namespaces*** # Install the get-all-namespaces plugin

### Debugging 
* ***kubectl logs <pod-name>*** # To view logs from a pod
* ***kubectl get events*** # Get the events in the cluster
* ***kubectl get logs mypod*** # Get the logs of a pod
* ***kubectl exec -it mypod -- /bin/bash*** # Execute a command in a pod
* ***kubectl describe pod mypod*** # Describe a pod
* ***kubectl get pods --all-namespaces*** # Get the pods in all namespaces
* ***kubectl get pods -n mynamespace*** # Get the pods in a namespace
* ***kubectl port-forward <pod-name> <local-port>:<container-port>*** # To forward port from Pod to Localhost. 

