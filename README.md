bypy - Python client for Baidu Yun (Personal Cloud Storage) 百度云/百度网盘Python客户端

====

[![alt text](https://travis-ci.org/houtianze/bypy.svg "Build status")](https://travis-ci.org/houtianze/bypy)

[![Join the chat at https://gitter.im/houtianze/bypy](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/houtianze/bypy?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

===

中文说明 (English readme is at bottom)
---
这是一个百度云/百度网盘的Python客户端。主要的目的就是在Linux环境下（Windows下应该也可用，但没有仔细测试过）通过命令行来使用百度云盘的2TB的巨大空间。比如，你可以用在Raspberry Pi树莓派上。它提供文件列表、下载、上传、比较、向上同步、向下同步，等操作。

**由于百度PCS API权限限制，程序只能存取百度云端`/apps/bypy`目录下面的文件和目录。**

**特征: 支持Unicode/中文；失败重试；递归上传/下载；目录比较; 哈希缓存。**

界面是英文的，主要是因为这个是为了Raspberry Pi树莓派开发的。

程序依赖
---
**重要：想要支持中文，你要把系统的区域编码设置为UTF-8。（参见：http://perlgeek.de/en/article/set-up-a-clean-utf8-environment)**

**重要：你需要安装[Python Requests 库](http://www.python-requests.org/). 在 Debian / Ubuntu / Raspbian** 环境下，只需执行如下命令一次：
```
sudo pip install requests
```

安装
---
`git clone`到任意目录。（为了运行方便，可以把`bypy.py`和`bypygui.pyw`拷贝至`/usr/bin/`目录）

运行
---
cd 到clone的目录，运行：
`./bypy.py`
可见命令行支持的全部命令和参数。

简单的图形界面：
`./bypygui.pyw`

基本操作
---
显示使用帮助和所有命令（英文）:
```
bypy.py
```

第一次运行时需要授权，只需跑任何一个命令（比如 `bypy.py info`）然后跟着说明（登陆等）来授权即可。授权只需一次，一旦成功，以后不会再出现授权提示.

更详细的了解某一个命令：
```
bypy.py help <command>
```

显示在云盘（程序的）根目录下文件列表：
```
bypy.py list
```

把当前目录同步到云盘：
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

**比较本地当前目录和云盘（程序的）根目录（个人认为非常有用）：**
```
bypy.py compare
```

更多命令和详细解释请见运行`bypy.py`的输出。

调试
---
- 运行时添加`-v`参数，会显示进度详情。
- 运行时添加`-d`，会显示一些调试信息。
- 运行时添加`-ddd`，还会会显示HTTP通讯信息（**警告：非常多**）


===
Introduction
---
This is a Python client for Baidu Yun (a.k.a PCS - Personal Cloud Storage), an online storage website offering 2 TB (fast) free personal storage. This main purpose is to be able to utilize this stoarge service under Linux environment (console), e.g. Raspberry Pi.

**Due to Baidu PC permission restrictions, this program can only access your `/apps/bypy` directoy at Baidu PCS**

**Features: Unicode / Chinese support; Retry on failures; Recursive down/up-load; Directory comparison; Hash caching.**

Prerequisite
---
**Important: You need to set you system locale encoding to UTF-8 for this to work (You can refere here: http://perlgeek.de/en/article/set-up-a-clean-utf8-environment)**

**Important: You need to install the [Python Requests library](http://www.python-requests.org/).** In Debian / Ubuntu / Raspbian, you just run the following command:
```
sudo pip install requests
```

Installation
---
`git clone` to any directory. (You can copy `bypy.py` and `bypygui.pyw` to `/usr/bin/` for easier command execution)


Usage
---
cd to the directory where it is cloned, and run:
`./bypy.py`
You will see all the commands and parameters it supports

Simple GUI:
`./bypygui.pyw`


Getting started
---
To get help and a list of available commands:
```
bypy.py
```

To authorize for first time use, run any commands e.g. `bypy.py info` and follow the instructiongs (login etc). This is a one-time requirement only.

To get more details about certain command:
```
bypy.py help <command>
```

List files at (App's) root directory at Baidu PCS:
```
bypy.py list
```

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

**To compare the current directory to (App's) root directory at Baidu PCS (which I think is very useful):**
```
bypy.py compare
```

To get more information about the commands, check the output of `bypy.py`.

Debug
---
- Add in `-v` parameter, it will print more details about the progress.
- Add in `-d` parameter, it will print some debug messages.
- Add in `-ddd`, it will display HTTP messages as well (**Warning: A lot**）




---
If you encounter `UnicodeDecodeError` while syncing up/down a directory, it's probably due the encoding of the directory / file names not being UTF-8 (especially if these files are copied from Windows to Unix / Linux). You can fix this using the `convmv` utility (to be issued in the directory to sync):
```
convmv -f GBK -t UTF-8 -r * (to see what renamings are going to happen)
convmv -f GBK -t UTF-8 --notest -r * (performing the actual renaming)
```
Thanks to [@zm1990s](https://github.com/zm1990s) for providing this fix. (The orginal post from him is at [#62](../../issues/62), his blog post detailing the `convmv` usage is here: http://blog.sina.com.cn/s/blog_4b3646350100kugp.html All are in Chinese though)

如果同步/比较是出现`UnicodeDecodeError`错误，很可能是因为目录/文件名编码不是UTF-8（特别是在文件是从Windows拷贝到Unix / Linux的情况下），解决方案是用`convmv`工具来修正编码，在要同步/比较的目录下输入如下命令:
```
convmv -f GBK -t UTF-8 -r * （查看将会将文件改名）
convmv -f GBK -t UTF-8 --notest -r * （实际的改名操作）
```
感谢 [@zm1990s](https://github.com/zm1990s) 提供解决方案. 他原帖在这里：[#62](../../issues/62)，博客具体讲述`convmv`用法的文章在这里： http://blog.sina.com.cn/s/blog_4b3646350100kugp.html

---
About a bug of Baidu that's affecting syncup。

Please refer to [#43](../../issues/43) 和 [#47](../../issues/47)

Basically: After a big file uploaded using slices and then combined, Baidu will return the wrong MD5. This will affect comparision (as MD5 is used to assert if the files local and remote are equal), thus will force syncup / syncdown transfer a second time.

**Workaround: syncup twice (For the second time, the big files are "rapidly uploaded", which is very fast. Small files that are the same will be skipped. After this, Baidu will return the correct MD5)**


关于百度的一个bug造成的syncup的一点问题。

参见 [#43](../../issues/43) 和 [#47](../../issues/47)

简单说就是：大文件分片上传合并后，百度会返回错误的MD5值。这会导致文件比较失败（本地和远程同样的大文件被认为是不同的文件，因为拿到MD5不一样），进而导致syncup / syncdown重复上传下载。

**曲线解决方法：syncup两次。（第二次大文件算是秒传，很快的；小文件不会再传。然后百度云端返回的MD5值都是正确的了）**






---
**Add in [wiki](../../wiki), for easier sharing / communicating.**

**加入了[wiki](../../wiki)，方便分享/交流。**

---
Copyright 2013 - 2015: Hou Tianze (GitHub: houtianze)
License: GPL v3
