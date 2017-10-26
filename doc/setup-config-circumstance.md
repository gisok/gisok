# 配置开发环境
---

## 下载Vmware workstation并安装

## 下载CentOS

1. 访问[CentOS管网](https://www.centos.org/)，或者 baidu --> CentOS project
1. 菜单 --> GET CENTOS
1. DVD
1. Actual country -
1. 选择一个，我选择阿里云 aliyun
1. 下载到本地。文件4.2G。本次下载时间为 18:34~18:52，网速达到5.4M/s。中间中断2次。

## 安装CentOS

[指导文档](https://jingyan.baidu.com/article/eae0782787b4c01fec548535.html)

1. 打开VMware workstation,版本为 11.1.2 build-2780323
1. 菜单-->文件-->新建虚拟机->自定义
1. 硬件兼容性选择 11.0
1. 稍后安装操作系统
虚拟机名称 "gisok develop - centos7 64",位置 1. "D:\DocLibrary\gisok-develop-virtual-machine"
1. 我有CPU八核，分给虚拟机2核
1. 我的内存为8G，分给它2G
1. 使用网络地址转换，不提供专门IP地址
1. 磁盘分配给他32G
1. 立即分配空间
1. 拆分为多个文件
1. 自定义硬件-->DVD->选择ISO文件
1. 点完成，19:25，等待，19:29,分配磁盘结束
1. 启动虚拟机
1. 选择 install centos,开始安装
1. 选择 中文 简体中文
1. 软件选择-我选择 开发及生成工作站
附加选项选择：开发工具，电子邮件服务器，emacs，KDE桌面, 1. 办公套件和生产率，postgresql，python
1. 开始安装19:43，设置root密码 atx165, 创建用户全名wangzhiyong,index,atx165
1. 等待20:08，结束

解决问题：
1. [不能上网](https://jingyan.baidu.com/article/cd4c2979f7ac63756e6e60d1.html)
没解决

