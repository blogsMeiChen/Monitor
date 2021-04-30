# Helm 部署

## 添加Cadvisor源地址
helm repo add ckotzbauer https://ckotzbauer.github.io/helm-charts
## 查看 Cadvisor list
helm  repo list
## Install chart
helm install ckotzbauer/cadvisor --version 1.2.2 --generate-name
