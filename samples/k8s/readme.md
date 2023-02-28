# Demo
- [1]
  - [Run nginx pod](#run-nginx-pod)
  - [Create nginx pod from yaml](#create-nginx-pod-from-yaml)
- [2]
  - [Nginx Deployment](#nginx-deployment)
- [3]
  - [wordpress](#wordpress)


## Run nginx pod
``` bash
kubectl run nginx --image=nginx
```

``` bash
kubectl get pods
```

``` bash
kubectl get pods -o wide
```

``` bash
kubectl port-forward pod/nginx 8080:80
```

http://localhost:8080

## Create nginx pod from yaml

``` yaml

apiVersion: v1
kind: Pod
spec:
  containers:
  - image: nginx
    imagePullPolicy: Always
    name: nginx
```

## Nginx Deployment

``` yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-nginx
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

``` bash
kubectl apply -f nginx-deployment.yaml
```

``` bash
kubectl get pods -o wide
```

``` bash
kubectl delete pod my-nginx-5c8b9f4b74-2xq5n
```

``` bash
kubectl get pods -o wide
```

``` bash	
kubectl get deployments
```

## wordpress

``` bash
kubectl apply -f .
```

http://loclahost:8080

``` bash
kubectl describe node docker-desktop
```


