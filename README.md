bypy
====

Python client for Baidu Yun 百度云盘的Python客户端

[English]

This is a Python client for Baidu Yun (a.k.a PCS - Personal Cloud Storage), an online storage website offering 2 TB (fast) free personal storage. This main purpose is to be able to utilize this stoarge service under Linux environment (console), e.g. Raspberry Pi.

This program uses the REST APIs to access the files at Baidu PCS. You can list, download, upload, compare, sync-up/down, etc.

Quick start:
```
bypy.py
```
to get help and a list of available commands

```
bypy.py help <command>
```
to get more details about certain command

```
bypy.py list
```
will give you the list of files at (App's) root directory at Baidu PCS

To sync up to the cloud (from the current directory):
```
bypy.py syncup
```
or
```
bypy.py upload
```

To sync down from the cloud (to the current directory):
```
bypy.py syncdown
```
or
```
bypy.py downdir /
```

To compare the current directory to (App's) root directory at Baidu PCS:
```
bypy.py compare
```

And there are more commands ...

Btw, hash caching is also implemented.

----
[中文]

这是一个百度云盘的Python客户端。主要的目的就是在Linux环境下（命令行）使用百度云盘的2TB的巨大空间。比如，你可以用在Raspberry Pi树莓派上。它提供文件列表、下载、上传、比较、向上同步、向下同步，等等。

界面是英文的，主要是因为这个是为了Raspberry Pi树莓派开发的。
第一次运行的时候要通过百度的网页进行授权（一次就好）

上手：
```
bypy.py
```
会显示使用帮助和所有命令（英文）

```
bypy.py help <command>
```
可以让你更详细的了解某一个命令

```
bypy.py list
```
显示在云盘（程序的）根目录下文件列表

把当前目录同步到云盘:
```
bypy.py syncup
```
or
```
bypy.py upload
```

把云盘内容同步到本地来：
```
bypy.py syncdown
```
or
```
bypy.py downdir /
```

比较本地当前目录和云盘（程序的）根目录:
```
bypy.py compare
```

还有一些其他命令 ...

顺道，哈希值的计算加入了缓存处理，使得第一次以后的计算速度有所提高。
