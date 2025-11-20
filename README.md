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

## 2. Apply Pod Yaml File

~~~sh
kubectl apply -f pod.yaml
~~~


## 3. Check Pods 
~~~sh
kubectl get pods
~~~

## 4. Check All Pods In Details
~~~sh
kubectl get pods -o wide
~~~

## 5. Write Service File =
~~~sh
nano service.yaml
~~~
#### Ex.1. ClusterIP Yaml File

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

#### Ex.2. NodePort Yaml File 

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

#### Ex.3. LoadBalancer

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

## 6. Apply Service Yaml File
~~~sh
kubectl apply -f service.yaml
~~~
## 7. Check Services
~~~sh
kubectl get svc
~~~
