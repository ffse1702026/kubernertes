# tai va cai dat Vagrant

# tai va cai dat https://www.virtualbox.org/

# khoi tao cluster
kubeadm init --apiserver-advertise-address=172.16.10.100 --pod-network-cidr=192.168.0.0/16

# plugin-network: Calio: 192.168.0.0/16
https://kubernetes.io/docs/concepts/cluster-administration/addons/    go to and choose

# run command
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
kubectl create -f https://docs.projectcalico.org/manifests/tigera-operator.yaml

#check cluster
kubectl cluster-info

#get node
kubectl get nodes

# Các pod đang chạy trong tất cả các namespace
kubectl get pods -A

# get token
kubeadm token create --print-join-command
->
kubeadm join 172.16.10.100:6443 --token av9yed.1me7umb2i0ddu5uw --discovery-token-ca-cert-hash sha256:95dcdea122f83d4e151efaf06ef45da0856b66d7e679d7ab3bd6389790e3d928

#check node
kubectl describe node/worker1.xtl

#view cluster
kubectl config view

# comppy file config of master
scp root@172.16.10.100:/etc/kubernetes/admin.conf C:/Users/Admin/.kube/config-mycluster

export KUBECONFIG=~/.kube/config:~/.kube/config-mycluster
kubectl config view --flatten > ~/.kube/config_temp
mv ~/.kube/config_temp ~/.kube/config

# get context
kubectl config get-contexts

# switach context
kubectl config use-context kubernetes-admin@kubernetes

#get pod
kubectl get pod





