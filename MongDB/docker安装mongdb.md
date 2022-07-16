# Docker安装MongoDB
安装MongoDB软件
```
sudo docker run -itd --name mongo -p 27017:27017 mongo
```
使用下列命令登陆进入MongoDB
```
sudo docker exec -it mongo mongo admin
```
安装成功后，可以执行以下命令来查看MongoDB的启动情况
```
sudo docker ps
```
```
use admin
db.createUser({
    user:'lrl',
    pwd:'123',
    roles:[
    {role:'userAdminAnyDatabase',db:'admin'},
    {role:'dbAdminAnyDatabase',db:'admin'},
    {role:'clusterMonitor',db:'admin'}
    ]
})
```
```
spring.data.mongodb.host=8.136.13.152
spring.data.mongodb.port=27017
spring.data.mongodb.database=practice
spring.data.mongodb.username=lrl
spring.data.mongodb.password=123

logging.level.root=info
```

