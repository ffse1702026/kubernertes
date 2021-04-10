# run dashboard
kubectl apply -f dashboard-v2-beta6.yaml

# get pod
kubectl get pod -n kubernetes-dashboard (-n : namespace)

# build docker
docker build -t myopenssl -f Dockerfile .

# Add cert
mkdir certs
docker run --rm -v ${PWD}/certs:/certs/ myopenssl req -nodes -newkey rsa:2048 -keyout /certs/dashboard.key -out /certs/dashboard.csr -subj "/C=/ST=/L=/O=/OU=/CN=kubernetes-dashboard"
docker run --rm -v ${PWD}/certs:/certs/ myopenssl x509 -req -sha256 -days 365 -in /certs/dashboard.csr -signkey /certs/dashboard.key -out /certs/dashboard.crt

# Create secret
kubectl create secret generic kubernetes-dashboard-certs --from-file=certs -n kubernetes-dashboard

# get secret
kubectl get secret -n kubernetes-dashboard

#check secret
kubectl describe secret/<name> -n <namespace name>
get token: kubectl describe secret/admin-user-token-4zw2q -n kubernetes-dashboard

#get node with output
kubectl get nodes -o wide

# apply user admin
kubectl apply -f admin-user.yaml