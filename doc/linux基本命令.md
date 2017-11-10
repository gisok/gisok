# linux 基本命令

[查询命令使用方法的网站](http://man.linuxde.net/)

##  sudo

这个SuperUserDo是Linux新手要使用的最重要的命令。需要根权限的每一个命令都需要这个sudo命令。你可以在需要根权限的每个命令之前使用sudo。

    $ sudo su 

## ls(list)

就跟别人一样，你常常想要看到目录里面的任何内容。借助list命令，终端就会显示你正在处理的那个目录里面的所有文件和文件夹。假设我在/home文件夹里面，想查看/home里面的目录和文件。

    /home$ ls 

/home中的ls返回下列结果：

    imad lost+found 

## cd

更改目录(cd)是始终在终端中使用的主要命令。它是最基本的Linux命令之一。使用这个命令很简单。只要输入你想要从当前目录进入到的那个文件夹的名称。如果想要返回上一级，只要将双圆点(..)作为参数。

假设我在/home目录中，想进入到始终在/home里面的usr目录。下面是我可以使用cd命令的方法：

    /home $ cd usr      
    /home/usr $ 

## mkdir

仅仅更改目录还不全面。有时候，你想要创建一个新的文件夹或子文件夹。可以使用mkdir命令来做到这一点。只要在终端中将你的文件夹名称放在mkdir命令的后面即可。

    ~$ mkdir folderName 

##  cp

拷贝粘贴是我们为了组织整理文件而需要完成的重要任务。使用cp将帮助你从终端拷贝粘贴文件。首先，你确定想要拷贝的那个文件，然后输入目的地位置，即可粘贴文件。

    $ cp src des 

注意：如果你将文件拷贝到任何新文件都需要根权限的目录，那么你就需要使用sudo命令。

##  rm

rm这个命令可以移除你的文件，甚至移除你的目录。如果文件需要根权限才能移除，可以使用-f。你还可以使用-r来进行递归移除，从而移除你的文件夹。

    $ rm myfile.txt 

##  apt-get

就不同的发行版而言，这个命令各不相同。在基于Debian的Linux发行版中，想安装、移除和升级任何软件包，我们可以使用高级包装工具(APT)软件包管理器。apt-get命令可帮助你安装需要在Linux中运行的软件。这是个功能强大的命令行工具，可以执行安装、升级、甚至移除软件这类任务。

在其他发行版(比如Fedora和Centos)中，有不同的软件包管理器。Fedora过去有yum，但现在它有dnf。

    $ sudo apt-get update 
     
    $ sudo dnf update 

##  grep

你需要找到一个文件，但是又记不得它的确切位置或路径。grep可以帮助你解决这个问题。你可以使用grep命令，根据给定的关键字帮助找到文件。

    $ grep user /etc/passwd 

##  cat

作为用户，你常常需要查看来自脚本的一些文档或代码。同样，其中一个Linux基本命令是cat命令。它会为你显示文件里面的文本。

    $ cat CMakeLists.txt 

##  poweroff

最后一个命令是poweroff。有时候，你需要直接从终端来关机。这个命令就能完成这项任务。别忘了在命令的开头添加sudo，因为它需要根权限才能执行poweroff。

    $ sudo poweroff 


##  wget
下载文件的命令

安装

    yum install wget

使用
    
    ?    

## scp

本地有bash时，拷贝文件到服务器比如上传公钥
    
    scp -r ~/.ssh/id_rsa.pub git@192.168.1.104:~/