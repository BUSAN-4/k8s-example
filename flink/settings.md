# 기동 순서

```bash
kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.18.2/cert-manager.yaml
helm install flink-kubernetes-operator flink-operator-repo/flink-kubernetes-operator -n flink-kubernetes-operator --create-namespace # 실행 (helm 설치 필요)
kubectl create namespace flink
kubectl apply -f flink-rbac.yaml -n flink
kubectl apply -f flink-serviceaccount.yaml -n flink
kubectl apply -f flink-session-cluster.yaml -n flink
kubectl apply -f flink-sql-gateway.yaml -n flink
```


# 삭제

```bash
kubectl delete -f flink-sql-gateway.yaml -n flink
kubectl delete -f flink-session-cluster.yaml -n flink
kubectl delete -f flink-serviceaccount.yaml -n flink
kubectl delete -f flink-rbac.yaml -n flink
kubectl delete namespace flink
helm delete flink-kubernetes-operator flink-operator-repo/flink-kubernetes-operator -n flink-kubernetes-operator
kubectl delete -f https://github.com/jetstack/cert-manager/releases/download/v1.18.2/cert-manager.yaml
```