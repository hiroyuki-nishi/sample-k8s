## Start Dashbord
https://github.com/kubernetes/dashboard

**kubectlのGUIの立ち上げ方法**
```
kubectl proxy
http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy/#!/overview?namespace=default
```

**踏み台デバッグコンテナの起動方法**
```
kubectl run -i --rm --tty debug --image=gihyodocker/fundamental:0.1.0 --restart=Never -- bash -il
```
