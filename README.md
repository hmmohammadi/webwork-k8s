# [WeBWorK](http://webwork.maa.org) on K8s

## Information for Downloading
* Clone [repo](https://github.com/hmmohammadi/webwork-k8s) on host
```console 
$ cd
$ git clone https://github.com/hmmohammadi/webwork-k8s.git
$ cd webwork-k8s
```

## Deploying on Kubernetes Cluster
* Create required directories for PersistentVolume(pv) or change as you want. :D
```yaml
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: ww-mariadb-pv
  namespace: webwork2
spec:
  accessModes: [ "ReadWriteOnce" ]
  capacity:
    storage: "3Gi"
  hostPath:
    path: /mnt/db   ## <----------------- HERE
---
```
```yaml
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: ww-pv-course
  namespace: webwork2
spec:
  accessModes: [ "ReadWriteOnce" ]
  capacity:
    storage: "3Gi"
  hostPath:
    path: /mnt/courses  ## <----------------- HERE
---
```
```yaml
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: ww-pv-htdocs
  namespace: webwork2
spec:
  accessModes: [ "ReadWriteOnce" ]
  capacity:
    storage: "3Gi"
  hostPath:
    path: /mnt/htdocs ## <----------------- HERE
---
```
* Create namespace on k8s cluster
```console 
 $ kubectl create -f webWork2.yml
```
* Deploy mariadb
```console 
 $ kubectl create -f mariadb-ww2-deploy.yml
```
* Deploy ww2
```console 
 $ kubectl create -f ww2-deploy.yaml
```
