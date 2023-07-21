### KUBECTL ###
kubectl version --client
kubectl cluster-info
kubectl run [pod name] --image [image name] > ex: kubectl run nginx --image --nginx. Create pod AND replicaset without YAML file

### READ ###
kubectl get [resource]
		pods
		pods -o wide
		replicaset
		deployment
		all
kubectl describe [resource] [resource name]

### CREATE AND DELETE ###
kubectl create -f [file name] (--save-config > save configuration to future "apply -f" commands)
		apply -f [file name]
kubectl delete [resource] [resource name]
kubectl replace -f [file name] > update cluster based on yaml file
kubectl scale --replicas=x -f [file name]

### DEPLOYMENT ###
kubectl create -f [file name] --save-config
							> --save-config > record configuration file, can be updated through apply
							> --record > deprecated, replaced by annotation
kubectl set image deployment [deployment name] [nome do container]=[imagem]
kubectl apply -f [file name]
kubectl scale deployment [deployment name] --replicas=[replica number]

kubectl annotate deployment  [deployment name]  description='[description]'
						kubernetes.io/change-cause="[description]"

kubectl rollout status deployment [deployment name]
		history deployment [deployment name] > show deployment revisions
kubectl rollout undo deployment [deployment name]
		undo deployment [deployment name] --to-revision=[revision number]

kubectl exec -it [pod name] -- bash > access container bash

---------------------------------------------------------------------------------------------

### MINIKUBE ###
minikube delete > delete minikube cluster created on Docker
minikube start > create minikube cluster on Docker
minikube config set driver [docker/etc] > set default container runtime
minikube service [service name] --url > gets service url:port