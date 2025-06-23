tls secret >>>>>
# tls secret stores certificates and their key

# create the key using folloeing commands 
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=example.com/O=demo"

# This command creates a secret with the name "my-tls-access" and stores the certificate and key
** kubectl create secret tls my-tls-secret --cert=/path/certificatefile.crt --key=/path/certificatekeyfile.key ** 

# Creating a pod with tls secret
kubectl create -f tls-pod.yml

# to get the pod details with IP address and other details
kubectl get po -o wide 

# to get the details of the secret
kubectl describe secret my-tls-secret

# to get the environment variable of the pod
** kubctl exec -it tls-pod -- printenv **

# to get the shell of the pod
# after entering go to the path > where certificatefile and keyfile are located
kubctl exec -it tls-pod -- /bin/bash 
*>>>/ cd /etc/cert-data
*>>>/ ls 

