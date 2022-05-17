# docker安装mySQL
分别执行以下命令
```
sudo docker run -itd -p 3306:3306  \
    -e MYSQL_ALLOW_EMPTY_PASSWORD="root" \
    --name mysql \
    mysql \
    --character-set-server=utf8 \
    --collation-server=utf8_general_ci \
    --default-authentication-plugin=mysql_native_password
```
验证是否启动成功

执行以下命令
```
sudo docker ps
```
看到终端输出mysql相关信息，即安装完毕

进入服务
```
sudo docker exec -it mysql bash
```
看到显示以下内容即进入成功
```
:/#
```
此时输入以下命令来登录MySQL
```
mysql -uroot
```
此时显示的界面```mysql>```后面是可以继续输入sql语句的

### 登出MySQL的命令：

输入```\quit```后显示Bye
再输入```exit```回到终端

