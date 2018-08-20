# kubernetes101-workshop
## 安装Vagrant环境
- 下载安装 [virtualbox 5.2 for OSX](https://download.virtualbox.org/virtualbox/5.2.18/VirtualBox-5.2.18-124319-OSX.dmg)
- 下载安装 [vagrant 2.1.2 for OSX](https://releases.hashicorp.com/vagrant/2.1.2/vagrant_2.1.2_x86_64.dmg) 

## 启动vagrant初始化VM
1. clone 代码仓库
```
git clone https://github.com/iasonliu/kubernetes101-workshop.git
cd kubernetes101-workshop
```
2. 使用vagrant 启动VM
```
# 在 kubernetes101-workshop 目录下执行
vagrant up
```
vagrant 会下载系统镜像，更新系统，安装docker，和一些必要的kubernetes软件可能会持续很久...

请保持一个良好的网络环境

> Notes： 如果vagrant 初始化中途网络中断
> 
> 在下载box阶段中断可以直接 `vagrant up` 重新下载 box
> 
> 在shell脚本安装初始化系统阶段中断，可以使用 `vagrant up --provision` 重新初始化


3. 初始化完成后验证
```
# 查询VM状态
$ vagrant status
Current machine states:

master01                  running (virtualbox)
node01                    running (virtualbox)
# 登录master01 VM
$ vagrant ssh master01
Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-116-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

1 package can be updated.
0 updates are security updates.

*** System restart required ***
Last login: Mon Aug 20 03:30:01 2018 from 10.0.2.2
# 切换root用户
vagrant@master01:~$ sudo su -
# 验证docker
root@master01:~# docker version
# 验证 kubeadm
root@master01:~# kubeadm version
kubeadm version: &version.Info{Major:"1", Minor:"11", GitVersion:"v1.11.2", GitCommit:"bb9ffb1654d4a729bb4cec18ff088eacc153c239", GitTreeState:"clean", BuildDate:"2018-08-07T23:14:39Z", GoVersion:"go1.10.3", Compiler:"gc", Platform:"linux/amd64"}
# 验证 kubelet
root@master01:~# kubelet --version
Kubernetes v1.11.2
```

## vagrant管理VM
使用如下命令关闭VM
```
vagrant halt
```
启动VM
```
vagrant up
# 启动某个VM
vagrant up master01
vagrant up node01
```
摧毁VM
```
vagrant destroy
```


