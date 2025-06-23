Generic Secret >>>>>
# to create generic secrete by storing username and password in a dictionary

# Creating a secret with username and password
** kubectl create secret generic generic-secret --from-literal=username=sonu --from-literal=password=Pass@123 **

# get secret
kubectl get secret

# to get the details of the secret
kubectl describe secret generic-secret

# Creating a pod with generic secret
kubectl create -f generic-pod.yml

# to get the pod details with IP address and other details
kubectl get po -o wide 

# to get the environment variable of the pod
** kubctl exec -it generic-pod -- printenv **
/
kubectl exec generic-pod -- env 