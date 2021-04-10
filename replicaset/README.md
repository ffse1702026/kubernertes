# get all
kubectl get all -o wide

#watch all
watch -n 1 kubectl get all -o wide

#deploy
kubectl rollout history deploy/deployapp -revision=<number revision>

# cack to deploy
kubectl rollout undo deploy/deployapp --to-revision=<number revision>

# describe
kubectl describe replicaset.app/

# auto scale
kubectl scale deploy/deployapp -replicas=10

# auto scale min max
kubectl autoscale deploy/deployapp --min=6 --max=10