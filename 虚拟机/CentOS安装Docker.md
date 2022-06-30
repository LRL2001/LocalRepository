```
sudo yum -y update
sudo yum -y install epel-release
sudo yum -y install docker-io
```
如果出现错误提示：“未找到匹配参数：docker-io”或错误：没有任何匹配：docker-io，则尝试输入命令`sudo yum -y install docker`