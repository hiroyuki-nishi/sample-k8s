### **ローカルでの動作確認**
```
// deploymentの作成
kubectl apply -f lspan-spa-deployment.yaml
// 作成されたpodとdeploymentの確認
kubectl get pod --watch
kubectl get deployment spa


// NodePort Serviceの作成
kubectl apply -f lspan-spa-node-port-sercie.yaml
// Portの確認
kubectl get svc spa
```


### **EKSのデプロイ方法**
参考：　https://docs.aws.amazon.com/ja_jp/eks/latest/userguide/getting-started.html#eks-create-cluster

1. EKSクラスターの作成
https://console.aws.amazon.com/eks/home#/clusters

2. kubeconfigの作成
```
aws eks --region <region> update-kubeconfig --name <1.のcluster_name>
// kubectrl実行時に作成したkubeconfigファイルを参照するようにする。
export KUBECONFIG=~/.kube/config-spa-eks-cluster-it
// クラスターの接続確認 Re
kubectl get svc
```

3. Amazon EKS ワーカーノードを起動して設定する
Cloudformationからworker-node.yamlを流してワーカーノードを作成する。

4. ワーカーノードとクラスターを結合する
**[NodeInstanceRole]の値は手順.3で出力された値を使用する。
```
kubectl apply -f aws-auth-cm.yaml
// Nodeのステータスの確認
kubectl get nodes --watch
```

5. アプリケーションの実行
```
// deploymentの作成
kubectl apply -f lspan-spa-deployment.yaml
// 作成されたpodとdeploymentの確認
kubectl get pod --watch
kubectl get deployment spa


// LoadBalancer Serviceの作成
kubectl apply -f lspan-spa-loadbalancer-service.yaml
// Serviceの確認
kubectl get svc spa
```

6. ブラウザで接続するURLの確認
```
kubectl describe services
```

7. クリーンアップ
```
// Serviceの削除
kubectl delete -f lspan-spa-loadbalancer-service.yaml

// Deploymentの削除
kubectl delete -f lspan-spa-deployment.yaml

// kubeconfigの設定を元に戻す
export KUBECONFIG=~/.kube/config
```

