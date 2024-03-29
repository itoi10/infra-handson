## k8sダッシュボードをデプロイするまでの手順

- 前提

Mac

Docker for Mac をインストールしてKubernetesを有効化

kubectlの向き先がdocker-desktopになっていること
```
$ kubectl config get-contexts
```




- ダッシュボードインストール

```
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
```

- サービスアカウント作成
```
$ kubectl apply -f dashboard-adminuser.yaml
```
認証トークン取得
```
$ kubectl -n kubernetes-dashboard create token admin-user
```

- アクセス
```
$ kubectl proxy
```
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/.



- Reference

https://github.com/kubernetes/dashboard
https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md
https://matsuand.github.io/docs.docker.jp.onthefly/desktop/kubernetes/
