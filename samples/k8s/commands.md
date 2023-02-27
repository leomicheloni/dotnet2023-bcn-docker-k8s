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

``` yaml

apiVersion: v1
kind: Pod
spec:
  containers:
  - image: nginx
    imagePullPolicy: Always
    name: nginx
```

## Deployments

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

```

``` bash
