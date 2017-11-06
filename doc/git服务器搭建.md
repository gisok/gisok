# Git服务器搭建

[教程](http://blog.csdn.net/hu8hong9/article/details/52851570)

    su
    yum install git -y
    git --version
        1.8.3.1
    yum remove git ;卸载

    groupadd git
    adduser git -g git
    passwd git
        atx165

    cd /
    mkdir data
    cd data
    mkdir git
    cd git
    git init --bare theRepo.git
    chown -R git:git theRepo.git

客户端Git bash
    cd /d/doclibrary/test_my_git_server
    git clone git@172.30.17.129:/data/git/therepo.git

已经可以使用了。

不知道为什么不用启动服务？

还需要 配置 密钥 和 封闭 用户登录

[教程](http://blog.csdn.net/wave_1102/article/details/47779401)
