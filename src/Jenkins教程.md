---
title: Jenkins教程
---
 linux查询占用端口并Kill进程（记录遇到的端口占用问题）
``` javascript?fancy=2,3&linenums=true
#查看占用端口情况
netstat -anp|grep 8080
#杀死进程
kill -9 10355
```
![enter description here](./images/2018-12-03_155421.png)
### 安装
我们选择War包的方式进行安装
下载地址：https://jenkins.io/download/
![enter description here](./images/2018-12-03_152410.png)
下载下来后进行解压
方法一：直接放到tomcat webapps 直接访问进行解压
方法二：运行java -jar jenkins.war 进行解压
![enter description here](./images/2018-12-03_155515.png)
2.查看密码
``` javascript?fancy=2,3&linenums=true
vim  /root/.jenkins/secrets/initialAdminPassword
#查询文件
find / -name [文件名]
```
3.安装
![enter description here](./images/2018-12-03_161434.png)
![enter description here](./images/2018-12-03_161528.png)
### 开始创建
1.配置jdk,maven
![enter description here](./images/2018-12-03_162314.png)
2.安装maven插件
![enter description here](./images/2018-12-03_165057.png)
选择可选插件搜索Maven Integration
3.创建项目
![enter description here](./images/2018-12-03_165245.png)
4.设置编译的版本号号等信息
![enter description here](./images/2018-12-03_165703.png)
5.设置代码地址
![enter description here](./images/2018-12-03_165823.png)
6.开始构建
![enter description here](./images/2018-12-03_173915.png)
7.版本提交触发构建
``` javascript?fancy=2,3&linenums=true
构建触发器: 只选中 Poll SCM，可指定检查 SVN 代码是否有提交的时间：
H/10  *  *  *  *  ## 任何时候，每隔 30 分钟就检测一次 SVN，如果有提交就启动构建
```
![enter description here](./images/2018-12-03_182935.png)
打包失败，问题Jenkins内存溢出
可能因为是虚拟机的限制 暂时无处理方法
问题原因：检查全局配置的maven java配置是否正确
![enter description here](./images/2018-12-05_095430.png)
![enter description here](./images/2018-12-05_095341.png)