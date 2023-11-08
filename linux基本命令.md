#### Linux 命令

##### 文件的压缩和解压

```bash
linux 解压zip文件
unzip 压缩文件.zip -d 解压的文件路径

压缩为zip文件
zip -p -r 要压缩的文件 压缩后的文件路径

1-1 将tgz文件解压到指定目录
#使用tar zxvf -C 命令指定解压目录,将test.tgz解压到source目录下
tar zxvf test.tgz  -C /root/source/

1-2 将指定目录的文件压缩到指定文件
#使用czvf命令进行压缩，将source中的文件压缩到test.tgz压缩包中
tar czvf test.tgz /root/source/

```

##### 文件的修改和创建

```bash
vi/vim 文件名称
```

