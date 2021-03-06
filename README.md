# node-tap
基于TypeScript实现的Tun2Shadowsocks.
目前可用于Windows平台.

# 测试实现特性
* 缩水TCP实现(⚠️)
* UDP转发(✅)
* UDP转发多倍发包(✅)
* 内建DNS解析转发(❌)
* 路由表境内/境外IP分流(❌)

# 使用

1) 从Releases中下载已经打包完的版本.
> Releases中版本均64位编译, 可能无法在32位平台使用.
2) 安装[OpenVPN Tap-windows](https://swupdate.openvpn.org/community/releases/tap-windows-9.21.2.exe)驱动.
3) 安装[Npcap](https://nmap.org/npcap/)来用于UDP多倍发包.
4) 使用管理员权限cmd或powershell中在已以下命令运行node-sstap.
```
.\sstap.exe --host [ss host] --port [ss port] --passwd [ss password] --xtudp [x times] --method [ss method]
```

* `host`: 默认 Shadowsocks地址(可选)
* `port`: 默认 Shadowsocks端口(可选)
* `passwd`: 默认 Shadowsocks密码(可选)
* `method`: 默认 Shadowsocks加密方式(可选)
* `tcphost`: TCP Shadowsocks地址(可选)
* `tcpport`: TCP Shadowsocks端口(可选)
* `tcppasswd`: TCP Shadowsocks密码(可选)
* `tcpmethod`: TCP Shadowsocks加密方式(可选)
* `udphost`: UDP Shadowsocks地址(可选)
* `udpport`: UDP Shadowsocks端口(可选)
* `udppasswd`: UDP Shadowsocks密码(可选)
* `udpmethod`: UDP Shadowsocks加密方式(可选)
* `xtudp`: UDP 多倍发包倍率(适用于游戏)
* `dns`: 指定DNS(默认8.8.8.8)
* `skipdns`: DNS不经过Shadowsocks转发(默认false)

> 启动添加路由时出现`对象已存在`或`找不到元素`为正常现象.

> 目前支持 `rc4-md5`, `aes-256-cfb`, `aes-128-gcm`, `aes-192-gcm`, `aes-256-gcm` 加密方式.

如果已经成功运行你应该会看到以下信息:
![snapshort.png](https://i.loli.net/2018/03/31/5abf7da82d4d1.png)

此时全部流量就全部转发到对应Shadowsocks服务器了.

# 框架图
![snapshort.png](https://i.loli.net/2018/03/31/5abf8255372bd.png)
> 该图来源: [http://blog.ucloud.cn/archives/3115](http://blog.ucloud.cn/archives/3115)

# 参考
* [net-speeder](https://github.com/snooda/net-speeder)
* [uIP](https://en.wikipedia.org/wiki/UIP_(micro_IP))
* [badvpn](https://github.com/ambrop72/badvpn)
* [gotun2socks](https://github.com/yinghuocho/gotun2socks)
* [blinksocks](https://github.com/blinksocks/blinksocks)
