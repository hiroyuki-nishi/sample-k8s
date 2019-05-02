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

**curlコマンド**
```
curl http://localhost \
-H 'Host: ch05.gihyo.local' \
-H 'User-Agent: Mozilla/5.0 (iPhone; CPU iPhone OS 11_0 like Mac OS X)a
AppleWebKit/604.1.38(KHTML, like Gecko) Version/11.0 Mobile/15A372 Safari/604.1'
```
