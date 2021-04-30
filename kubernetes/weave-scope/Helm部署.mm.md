## Ubuntu18.04 

### snap 安装Helm
```bash
sudo snap install helm --classic
```

### 报错
```bash
Helm ls
# 这两行警告信息意思是当前使用的kubernetes的配置文件不安全，同用户组的用户和其他用户都可以读取这个文件
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /home/user/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /home/user/.kube/config
Error: repo stable not found

查看/home/user/.kube/config 的权限
ll /home/user/.kube/config
# 解决方法
sudo chmod g-rw ~/.kube/config
sudo chmod o-r ~/.kube/config
# 再次执行helm命令,告警信息已经没有了：
helm ls
```
### 下载 weave-scope
```bash
helm fetch stable/weave-scope
# ls 会看到 文件已经下载到本地了
weave-scope-1.1.11.tgz
# 解压
tar -zxvf weave-scope-1.1.11.tgz
# 修改访问方式
sed -i "s@\ type:\ \"ClusterIP\"@ type: \"NodePort\"@" weave-scope/values.yaml
```
### 创建命令空间
```bash
kubectl create namespace weave-scope
```
### 安装
```bash
helm install  weave-scope --namespace weave-scope -f weave-scope/values.yaml weave-scope/
```
### 查看
```bash
helm list -n weave-scope
```
### 查看服务状态
```bash
helm status common-service -n weave-scope
```
