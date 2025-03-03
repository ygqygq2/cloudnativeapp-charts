# hexo

## 功能介绍

利用 Ingress 运行自己的 hexo 博客

## 安装使用

```shell
		helm install ../hexo \
		--name myhexo \
		--set fullnameOverride=myhexo  \
		--set hexo_host=blog.zeusro.tech \
		--set ingress.hosts={blog.zeusro.tech} \
    --set public_hexo_github_url=https://github.com/zeusro/docker-hexo.git
```

运行后看到输出：

```shell
NAME:   myhexo
LAST DEPLOYED: Tue Jul 23 12:10:42 2019
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1beta1/Ingress
NAME              HOSTS             ADDRESS  PORTS  AGE
blog.zeusro.tech  blog.zeusro.tech  80       0s

==> v1/Pod(related)
NAME                     READY  STATUS   RESTARTS  AGE
myhexo-85454f9b86-xtmr9  0/1    Pending  0         0s

==> v1/Service
NAME    TYPE       CLUSTER-IP    EXTERNAL-IP  PORT(S)   AGE
myhexo  ClusterIP  172.30.5.164  <none>       4000/TCP  0s

==> v1beta2/Deployment
NAME    DESIRED  CURRENT  UP-TO-DATE  AVAILABLE  AGE
myhexo  1        0        0           0          0s

NOTES:
设置 DNS 解析指向 ingress 公网IP,URL 如下:
    http://blog.zeusro.tech/
```

执行完 NOTES 中提示命令的命令即可在浏览器中访问 `http://127.0.0.1:8080` 查看。

## 使用参数

参数名|意义
--|--
name|release 名称
fullnameOverride|资源(service,deploy)名称
hexo_host |博客公网 URL
ingress.hosts|博客公网 URL
public_hexo_github_url|hexo 源代码路径(不一定要GitHub,但需要能够支持公开拉取)