# HPA-Demo

Enable metrics server:

minikube addons enable metrics-server
minikube addons list

kubectl create -f nginx.yaml
kubectl create -f nginx-hpa.yaml

Confirm:

kubectl get pods
kubectl get hpa

Expose the service:
kubectl expose deployment nginx --type=LoadBalancer --name=nginx-service

Get the URL:
minikube service nginx-service

#Generate load:
kubectl run --generator=run-pod/v1 -it --rm load-generator --image=busybox /bin/sh
while true; do wget -q -O- http://192.168.99.101:30726; done

