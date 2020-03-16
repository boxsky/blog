---
title: git仓库文件权限修改导致文件版本更新发生冲突
date: 2019-10-21 11:42:40   
tags:
- git
categories:
- 运维
- git
---

#### 在开发项目的时候常常会遇到这样的问题,比如开发环境用的是windows,线上代码环境是linux,因为在windows和linux的文件权限系统体制不同,会导致在测试环境中的文件夹权限上线到linux环境中需要修改文件夹权限（如runtime文件夹,uploads文件夹需要写入权限,比默认权限要高）,这时候一旦修改文件夹权限的话(如设置当前目录为 755)
```bash
chmod -R 755 ./
```
#### 会导致git版本变动,此时可以通过
```git
git status
```
#### 查看git状态，发现该文件夹所有的文件都需要提交,这样每次发布线上版本会非常麻烦，可以通过git命令或者修改git配置文件来忽略掉这个文件权限变动引起的git版本变动
```git
git config core.filemode false
```
#### 这样的话就不用关心文件权限的变更引起的版本状态变更


