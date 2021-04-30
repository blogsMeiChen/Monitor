# kubernetes 安装weave scop
# 下载并启动 weave scop
kubectl apply -f "https://cloud.weave.works/k8s/scope.yaml?k8s-version=$(kubectl version | base64 | tr -d '\n')"

# 修改svc 为NodePort
kubectl patch svc $(kubectl get svc -n weave |grep weave-scope-app |awk '{print $1}') -p '{"spec":{"type": "NodePort"}}' -n weave

kubectl get svc -n weave |grep weave-scope-app

# 查看pods 与 网络信息
kubectl get pod -n weave -o wide
