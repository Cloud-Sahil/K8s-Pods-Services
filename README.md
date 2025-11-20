# Kubernetes-Pods

## 1. Write Pod File =
~~~sh
nano pod.yaml
~~~
~~~sh
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
      app: nginx
spec:
  containers:
    - name: nginx
      image: nginx
      ports: 
        - containerPort: 80
~~~
### Ex. nginx (image)

## 2. Check Pods 
~~~sh
kubectl get pods
~~~
