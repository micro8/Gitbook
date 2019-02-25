### windows 全平台自带ftp，在实战中需要考虑两点：  
* 数据传输的完整性。  
* 代码得精简

### ftp文件的传输方式：  
* Binary ，二进制传输  
* Ascii ，ascII传输

在 FTP 文件传输过程中，ASCII 传输 HTML 和文本编写的文件，而二进制码传输可以传送文本和非文本（执行文件，压缩文件，图片等），具有通用性，二进制码传输速度比 ASCII 传输要快。所以在建立 bat 脚本时，一般输入 bin 命令，启用二进制传输。如果用 ASCII 模式传输非文本文件，可能会显示一堆乱码。ASCII 和binary 模式的区别是回车换行的处理。binary 模式不对数据进行任何处理，ASCII 模式将回车换行转换为本机的回车字符，比如Unix 下是 `\n`, Windows 下是`\r\n`，Mac 下是`\r`。Unix 系统下行结束符是一个字节，即十六进制的 `0A`，而 ms 的系统是两个字节，即十六进制的 `0D0A`。

```bash
echo open 192.168.1.115 21> ftp.txt
echo 123>> ftp.txt //user
echo 123>> ftp.txt //password
echo binary >> ftp.txt //bin模式
echo get robots.txt >> ftp.txt
echo bye >> ftp.txt
```

![](media/c5c7ac3159ec54aebb31f66d8de10af7.jpg)

![](media/c165fc58678e3ce58625166bd8a2b927.jpg)


>   Micropoor
