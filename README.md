## offline centos yum repo

1. mkdir
```shell
mkdir /root/yum/
```

2. install createrepo
```shell
yum install -y createrepo
```

3. repotrack some lib
```shell
repotrack -a x86_64 -p /root/yum docker-ce docker-ce-cli containerd.io
repotrack -a x86_64 -p /root/yum htop
```

> lib in this repo

docker-ce docker-ce-cli containerd.io htop supervisor keepalived

4. createrepo
```shell
createrepo /root/yum
```

5. scp file && add a repo
> /etc/yum.repos.d/CentOS-Local.repo
```text
[Local] 
name=Local Yum    
baseurl=file:///root/yum/ 
gpgcheck=0
```

```shell
yum clean all
yum makecache
```
