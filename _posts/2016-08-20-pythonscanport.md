---
layout: post
title:  "python多进程端口扫描" 
date:   2016-08-20
---
##### 公司的智能硬件（多台设备），需要通过ip远程连接，但又不能确认这些设备的ip具体是什么，最开始的想法是ping，简直too young，直接利用socket.connect_ex方法，尝试连接相应的端口，就能判断设备的具体ip了，直接上代码

```python
rom multiprocessing import Pool

import socket


def test_port(ip):
    port = 5555
    s = socket
    s.setdefaulttimeout(1)  # timeout
    ss = s.socket(socket.AF_INET, socket.SOCK_STREAM)

    indicator = ss.connect_ex((ip, port))
    if indicator == 0:
        print(ip + ":" + str(port))
    ss.close()


if __name__ == '__main__':

    ipList = []
    for i in xrange(1, 255):
        ip = '192.168.3.%s' % i
        ipList.append(ip)

    pool = Pool(100)
    pool.map(test_port, ipList)
    pool.close()
    pool.join()
```

加了多进程，约2秒钟执行完毕，输出结果

```
192.168.3.72:5555
192.168.3.86:5555
192.168.3.99:5555
192.168.3.169:5555
```

结语：陌生wifi不要连接。。秒秒钟扫出你的端口
