### Using kubectl
```bash
kubectl get pods #return a list of the pods running in the default namespace
                 #-A or --all-namespaces (list pods running in all namespaces)
                 #-o wide (show more information about the pods running)
                 #-o yaml (display the yaml definition of the pod)
kubectl delete [podname]       #or --all
kubectl config current-context #display the name of the current context
kubectl describe pod [podname] #describe the structure of the pod 
							   #showing it's history status
kubectl edit pod [podname] #opens the yaml definition of the pod to be edited
kubectl run [podname] --image=[imagename] #start pod with the container specified
										  #--dry-run=client -o yaml
										  #    (get base yaml definition for pod)
kubectl create -f [yamlfile]    #create a pod using the specification provided
kubectl apply -f [yamlfile]     #apply pod detecting the changes within the spec
kubectl exec [podname] -- echo Hello      #exec command into the pod
kubectl exec -it [podname] -- /bin/bash   #exec interactive shell in the pod
```

### Using k9s
```bash
0                # list all the pods currently running on the cluster
:q               # close k9s
```

### Vim
```bash
:set paste       # change mode to make pasting easy
```