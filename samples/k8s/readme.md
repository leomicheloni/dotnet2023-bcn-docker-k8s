# Demo
- [1]
  - [Run nginx pod](#run-nginx-pod)
  - [Create nginx pod from yaml](#create-nginx-pod-from-yaml)
- [2]
  - [Nginx Deployment](#nginx-deployment)
  - [Ngin service](#nginx-service)
- [3]
  - [wordpress](#wordpress)


## Run nginx pod
``` powershell
kubectl run nginx --image=nginx
```

``` powershell
kubectl get pods
```

``` powershell
kubectl get pods -o wide
```

``` powershell
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

``` powershell
kubectl apply -f nginx-deployment.yaml
```

``` powershell
kubectl get pods -o wide
```

``` powershell
kubectl delete pod my-nginx-5c8b9f4b74-2xq5n
```

``` powershell
kubectl get pods -o wide
```

``` powershell	
kubectl get deployments
```

## Ngin service

``` powershell
kubectl apply -f nginx-service.yaml
```

``` powershell
kubectl get services -o wide
```




## wordpress

``` powershell
kubectl apply -f .
```

http://loclahost:8080

``` powershell
kubectl describe node docker-desktop
```


