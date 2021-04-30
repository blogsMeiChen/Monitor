# Helm 部署

## 添加Cadvisor源地址
helm repo add ckotzbauer https://ckotzbauer.github.io/helm-charts
## 查看 Cadvisor list
helm  repo list
## 下载离线包
helm  fetch  ckotzbauer/cadvisor
tar -zxvf cadvisor-1.2.2.tgz
## Install chart
helm install ckotzbauer/cadvisor --version 1.2.2 --generate-name
helm install --name my-release ckotzbauer/cadvisor
