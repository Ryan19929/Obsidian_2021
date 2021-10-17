## 安装
- 需要用到hdfs库
```shell
pip install hdfs
```
## 连接
```python
from hdfs.client import Client
client = Client("http://cdh-01:xxxx")
```
- hdfs连接的端口是NameNode的Web管理端口，本次环境是9870
## 	upload()
```python
def callback(filename, size):
    print(filename, "完成了一个chunk上传", "当前大小:", size)
    if size == -1:
        print("文件上传完成")
        
# 上传成功返回 hdfs_path
client.upload(hdfs_path="/a_bak14.txt", local_path="a.txt", chunk_size=2 << 19, progress=callback,cleanup=True)
```
- 上传文件到hdfs同hdfs dfs -copyFromLocal local_file hdfs_path
- 其中chunk_size: Interval in bytes by which the files will be uploaded.