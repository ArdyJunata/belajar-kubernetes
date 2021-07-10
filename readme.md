# Kubernetes Basic

## Node

view all node

> kubectl get node

view detail node

> kubectl describe node nodename

## Pod

view all pod

> kubectl get pod
> kubectl get pord -o wide

view detail pod

> kubectl describe pod podname

create pod

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
        - containerPort: 80
```

> kubectl create -f filename.yml

create pod to specific namespace

> kuectl create -f filename.yml --namespace namespace

accessing pod

> kubectl port-forward podname accessPord:portPod

delete pod

```
kubectl delete pod podname
kubectl delete pod podname1 podname2 podname3
```

delete pod by label

> kubectl delete pod -l key=value

delete all pod in namespace

> kubectl delete pod --all --namespace namespace

## Label

create label

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx-with-labels
  labels:
    label-key1: label-value1
    label-key2: label-value2
    label-key3: label-value3
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
        - containerPort: 80
```

> kubectl -f create filename.yml

show labels

> kubectl get pods --show-labels

adding new labels to exist pod

> kubectl label pod podname key=value

changing label

> kubectl label pod podname key=value --overwrite

finding label

```
kubectl get pods -l key
kubectl get pods -l key=value
kubectl get pods -l '!key'
kubectl get pods -l key!=value
kubectl get pods -l 'key in (value1,value2)'
kubectl get pods -l 'key notin (value1,value2)'
kubectl get pods key,key2=value
kubectl get pods key=value,key2=value
```

## Annotation

create annotation
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx-with-labels
  labels:
    label-key1: label-value1
    label-key2: label-value2
    label-key3: label-value3
  annotations:
    annotation-key1: annotation-value
    annotation-key1: very long annotation, with many word
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
        - containerPort: 80
```

> kubectl -f create filename.yml

adding annotation to pod

> kubectl annotate pod podname key=value

replacing annotation in pod

> kubectl annotate pod podname key=value --overwrite

## Namespace

show namespane
```
kubectl get namespaces
kubectl get namespace
kubectl get ns
```

show pod in namespace
```
kubectl get pod --namespace namespace
kubectl get pod -n namespace
```

create namespace
```
apiVersion: v1
kind: Namespace
metadata:
  name: finance
```
> kubectl create -f filename.yml

delete namespace

> kubectl delete namespace namespace



