```
sudo yum -y update
sudo yum -y install epel-release
sudo yum -y install docker-io
```
如果出现错误提示：“未找到匹配参数：docker-io”或错误：没有任何匹配：docker-io，则尝试输入命令`sudo yum -y install docker`

执行docker ps命令，出现
```
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```
错误
此时已确定Docker本身已经安装正常。
问题原因是因为docker服务没有启动，所以在相应的/var/run/ 路径下找不到docker的进程。
执行
```
service docker start 
```
命令，启动docker服务，返回docker start/running, process 2662
此时进程启动成功，再执行`docker ps`，问题解决