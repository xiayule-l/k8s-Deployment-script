 K8S集群搭建教程
一、	硬性要求
1、	服务器数量： 至少两台。只有一台主控节点，工作节点最少一台。
2、	镜像要求：CentOS-7-x86_64-Everything-1810。
3、	内存要求：最少2G。
4、	CPU要求：最少两核。
5、	硬盘要求：最少30G。

二、	服务器准备工作
1、	配置ip和主机名。
使用命令：nmtui
2、	编写hosts文件添加主机映射。
使用命令：vi /etc/hosts
3、	主控节点生成秘钥。
使用命令：ssh-keygen(一直回车)
4、	主控节点分发秘钥。
使用命令：ssh-copy-id root@节点主机名

三、	安装主控节点
1、	上传k8s.tar到/root/目录下。
使用Xftp即可。
2、	解压k8s.tar。
使用命令：tar -xvf k8s.tar
3、	进入k8s/目录
使用命令：cd k8s
4、	运行master.sh脚本。
使用命令：./master.sh
5、	刷新令牌。
使用命令：kubeadm token create --print-join-command

6、	验证集群状态。
使用命令：kubectl get pod -A和kubectl get nodes

四、	安装工作节点
1、上传k8s.tar到/root/目录下。
使用Xftp即可。
2、解压k8s.tar。
使用命令：tar -xvf k8s.tar
3、进入k8s/目录
使用命令：cd k8s
4、运行node.sh脚本。
使用命令：./node.sh
5、	加入集群。
将主控节点的新令牌输入
6、	验证。
在主控节点使用命令：kubectl get nodes
