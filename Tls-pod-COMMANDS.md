tls secret >>>>>
# tls secret stores certificates and their key

# create the key using folloeing commands 
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=example.com/O=demo"

# This command creates a secret with the name "my-tls-access" and stores the certificate and key
** kubectl create secret tls my-tls-secret --cert=/path/certificatefile.crt --key=/path/certificatekeyfile.key ** 

# get secret
kubectl get secret

# to get the details of the secret
kubectl describe secret my-tls-secret

# Creating a pod with tls secret
kubectl create -f tls-pod.yml

# to get the pod details with IP address and other details
kubectl get po -o wide 

# to get the environment variable of the pod
** kubctl exec -it tls-pod -- printenv **
/
kubectl exec tls-pod -- env 

# to get data from configmap in pod-3
kubectl exec tls-pod -- ls /etc/cert-data
/
kubectl exec tls-pod -- cat /etc/cert-data/tls.crt <AND> kubectl exec tls-pod -- cat /etc/cert-data/tls.key
/
# to get the shell of the pod
# after entering go to the path > where certificatefile and keyfile are located
kubctl exec -it tls-pod -- /bin/bash 
*>>>/ cd /etc/cert-data
*>>>/ ls 

