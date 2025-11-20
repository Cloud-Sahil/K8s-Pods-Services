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
#### Ex. nginx (image)

## 2. Apply (create/update) YAML file or directory.

~~~sh
kubectl apply -f <file-name>.yaml
~~~

#### Ex. 1. Apply a single YAML file
~~~sh
kubectl apply -f pod.yaml
~~~
#### Ex. 2.Apply multiple YAML files
~~~sh
kubectl apply -f pod.yaml -f service.yaml
~~~
#### Ex. 3.Apply with namespace
~~~sh
kubectl apply -f pod.yaml -n dev
~~~


## 3. Check Pods 
~~~sh
kubectl get pods
~~~

## 4. Write Service File =

### 1. ClusterIP Yaml File
~~~sh
nano service.yaml
~~~
~~~sh
apiVersion: v1
kind: Service
metadata:
  name: clusterip
spec:
  selector:
     app: nginx
  ports:
     - protocol: TCP
       port: 80
       targetPort: 80
~~~

### 2. NodePort Yaml File 
~~~sh
nano service.yaml
~~~
~~~sh
apiVersion: v1
kind: Service
metadata:
  name: np
spec:
  selector:
     app: nginx
  ports:
     - protocol: TCP
       port: 80
       targetPort: 80
       nodePort: 31111
  type: NodePort
~~~

### 3. LoadBalancer
~~~sh
nano service.yaml
~~~
~~~sh
apiVersion: v1
kind: Service
metadata:
  name: my-lb-service
spec:
  type: LoadBalancer
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
~~~
