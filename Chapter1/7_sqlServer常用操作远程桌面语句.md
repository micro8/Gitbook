
# SqlServer 常用操作远程桌面语句

### 1、是否开启远程桌面
* 1：表示关闭
* 0：表示开启
```sql
EXEC master..xp_regread 'HKEY_LOCAL_MACHINE',
'SYSTEM\CurrentControlSet\Control\Terminal Server',
'fDenyTSConnections'
```
![](media/f01ea9712b6f116b14c9b9e75b7d49cd.jpg)

### 2、读取远程桌面端口

```sql
EXEC master..xp_regread 'HKEY_LOCAL_MACHINE',
'SYSTEM\CurrentControlSet\Control\TerminalServer\WinStations\RDP-Tcp',
'PortNumber'
```  
![](media/061010d0371ed380f50bbb96911c6d80.jpg)

### 3、开启远程桌面
```sql
EXEC master.dbo.xp_regwrite'HKEY_LOCAL_MACHINE',
'SYSTEM\CurrentControlSet\Control\TerminalServer',
'fDenyTSConnections','REG_DWORD',0;
```

**reg 文件开启远程桌面：**

```ini
Windows Registry Editor Version 5.00HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TerminalServer]
"fDenyTSConnections"=dword:00000000[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TerminalServer\WinStations\RDP-Tcp]
"PortNumber"=dword:00000d3d
```
////
保存 micropoor.reg，并执行 regedit /s micropoor.reg

**注：如果第一次开启远程桌面，部分需要配置防火墙规则允许远程端口。**

```bash
netsh advfirewall firewall add rule name="Remote Desktop" protocol=TCP
dir=in localport=3389 action=allow
```

### 4、关闭远程桌面
```sql
EXEC master.dbo.xp_regwrite'HKEY_LOCAL_MACHINE',
'SYSTEM\CurrentControlSet\Control\TerminalServer',
'fDenyTSConnections','REG_DWORD',1;
```

<p align="right">--By  Micropoor </p>
