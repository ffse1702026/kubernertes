# kubectl
kubectl [command] [TYPE] [NAME] [flags]
Trong đó:

[command] là lệnh, hành động như apply, get, delete, describe ...
[TYPE] kiểu tài nguyên như ns, no, po, svc ... - kubectl api-resources
[NAME] tên đối tượng lệnh tác động
[flags] các thiết lập, tùy thuộc loại lệnh

# kubectl descrive node master.txl

# gan nhan node
kubectl label node worker1.txl <ten nhan>=<gia tri nhan>

#get node by bale
kubectl get node -l "nodeabc=dechayungdungphp"

#xoa nha
kubectl label node worker1.txl <tennhan>-

# run o node master
kubectl taint nodes --all node-role.kubernetes.io/master-

# phan tich pod

kind: loai(pod)
metadata: (mota pod)
	lable: nhan~

spec:
	containers
	-name: C1
	image:
	resources:
		memory 
		cpu

# delete pod
kubectl delete pod <name>

# get su kien xay ra
kubectl get ev

# edit pod
kubectl edit po/<pod name>

# logs pod
kubectl logs pod/<pod name>

# thi hanh lenh trong pod
kubectl exec <podname> <COMMAND>
kubectl exec -it <podname> <COMMAND>(tools bash)
kubectl exec -it <podname> <COMMAND> -c <Container name>(tools bash)

# pod nhieu container

# helthy check
 livenessProbe:
      httpGet:
        path: /healthycheck
        port: 8085
      initialDelaySeconds: 10
      periodSeconds: 10
	  
# Tao pod tren node
them node selector
spec:
	nodeSelector:
		labels:kubernetes.id/hostname=worker1.xtl



