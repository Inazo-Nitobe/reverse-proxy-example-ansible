This document describes how to setup our development environment.

1. setup source code on your vagrant synced folders.
```
yourhost$ cd ./vagrant
yourhost$ git clone git@github-repo-taka:Inazo-Nitobe/reverse-proxy-example.gita
```

2. Launch your vagrants.
```
yourhost$ cd ./vagrant
yourhost$ vagrant up proxy web1 web2
```
3. Login to your vagrants and get gpg key to authenticate when you install openresty.
```
yourhost$ vagrant ssh proxy 
vagrant$ sudo yum install -y https://openresty.org/package/pubkey.gpg
```
4. Run ansible script.
```
yourhost$ ansible-playbook -i hosts bootstrap.yml 
```
5. You will fail to install openresty by gpg key issue. you may do inside vagrant and redo ansible script.
```
vagrant$ sudo yum install openresty

yourhost$ ansible-playbook -i hosts bootstrap.yml 
```
6. Add some resolvers to your hosts file.
```
192.168.33.60   mypx.app-visor.com myapi.app-visor.com
192.168.33.61   mypxd.app-visor.com
```
