# WinSockDemo

**1.网络基础：**
    
    1.网络是当前信息技术的第一推动力
    2.每个计算设备上都有若干个网卡
    3.每个网卡上都有单独的硬件地址，mac地址，全球唯一
        mac地址：全称Media Access Control Address
        介质访问地址，又名硬件地址
        每个网卡都有全球唯一的mac地址，跟mac电脑不是一个意思
    4.ip地址：每个网卡、机器都有一个或多个ip地址
        -IPV4：192.168.0.100 每段0-255
        -IPV6:128bit长，分成8段，每段4个16进制数
        -查询:
            win     ipconfig
            linux   ifconfig
    5.port端口：0-65535
        -0-1023已经被占用：80是web，23是telnet
        -1024-65535一般程序可使用
    6.机器通讯：ip+port
    7.查询：netstat -an
    8.保留ip：127.0.0.1 指本机
    9.公网（万维网，互联网）和内网（区域网）：
        -网络是分层的
        -最外层是公网
        -底下每层都是内网
        -ip地址可以在每个层次的网重用
        -tracert看当前机器和目标机器的访问中继：tracert ip （通过多少个网关或交换机才能到目标机器）
            C:\Users\Administrator>tracert www.baidu.com
            通过最多 30 个跃点跟踪
            到 www.a.shifen.com [61.135.169.125] 的路由:
              1     1 ms     1 ms     2 ms  XiaoQiang [192.168.31.1]
              2     2 ms     2 ms     2 ms  192.168.1.1
              3     4 ms     3 ms     3 ms  10.70.0.1
    10.通信协议：TCP/UDP qq的udp为主，tcp为辅
        TCP: Transmission COntrol Protocol
            -传输控制协议，面向连接的协议
            -两台机器的可靠无差错的数据传输
            -双向字节流传递
        UDP：User Datagram Protocol
            -用户数据报协议，面向无连接协议
            -不保证可靠地数据传输
            -速度快，也可以在较差网络下使用

**2.UDP编程：**
    
    1.计算机通讯：数据从一个ip:port出发，运输到另一个ip:port【发送方->接收方】
    2.udp:无连接无状态的通讯协议：
        -发送方发送消息，如果接收方刚好在，则可以接受，否则消息丢失
        -发送方也无法知道是否发送成功
        -UDP好处：简单，节省，经济
    3.udp实现：
        -DatagramSocket：通讯的数据管道
            -send和receive方法
            -可选，多网卡绑定一个ip和port
        -DatagramPacket
            -集装箱：封装数据
            -地址标签：目的地ip+port
        -实例：
            -无主次之分
            -接收方必须早于发起方执行
    
