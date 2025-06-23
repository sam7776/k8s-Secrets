Docker-registry Secret >>>>>
# docker-registry stores email, username, password , and other information to access the docker.

# Creating a secret with username and password
** kubectl create secret docker-registry docker-secret --docker-email=sonu1@gmail.com --docker-username=sonu --docker-password=Pass@123 **

# get secret
kubectl get secret

# to get the details of the secret
kubectl describe secret docker-secret

# Creating a pod with generic secret
kubectl create -f docker-pod.yml

# to get the pod details with IP address and other details
kubectl get po -o wide 

# to get the environment variable of the pod
** kubctl exec -it docker-pod -- printenv **
/
kubectl exec docker-pod -- env 

