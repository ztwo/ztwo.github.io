---
layout: post
title:  "Android蠕虫分析报告" 
date:   2016-07-19
---
#### 年初跟进用户反馈问题，发现了几例蠕虫病毒扩散事件，当时写的跟进报告，报告主要是分析蠕虫的运作，详细反编译过程，请google。


## 疑似获取我司数据的病毒分析报告

#### 结论：针对疑似盗取我司数据的病毒进行分析，从病毒源码内未看到与公司相关的逻辑。类似蠕虫病毒，目前中毒人数约574人

##### 病毒的分析结论：

* 病毒url：b*****.cn/hkfmg
* 病毒apk：*（防止二次泄露，关键数据隐藏）
* 病毒反编译jar：*
* 病毒重要程序类：com.phone.stop.db.a.class(调用发送信息)，com.phone.stop.db.f.class(获取信息类，发送信息）
* 病毒制作人手机号：1371****，171 *****
* 病毒人制作人邮箱/密码：171****@sina.cn，
* 病毒人制作人邮箱内邮件：1147封，受害人约：574人
* 病毒人制作人邮件内容：获取宿主触发关键字的短信与全部电话簿
* 病毒机制：类似蠕虫病毒,获取宿主电话簿，传到服务器，服务器向目标人发送短信引导中毒
* 中毒后的结果办法：无法卸载，普通用户遇到只能重刷手机

注：以上信息是从病毒源码内获得

##### 病毒的分析过程：

1.用户反馈：收到一条短信，以为是我司发的，就点击安装，安装后无任何反馈（安装过程中申请了设备管理器权限）

![png](/assets/img/Androidworm/01.png)

2.针对病毒apk反编译，得到源码。针对源码进行分析

3.类名：com.phone.stop.db.f.class，可以看到针对字段进行了筛选，一旦用户短信触发了这些字段，就会往指定邮箱发送短信

![png](/assets/img/Androidworm/02.png)

4.类名：com.phone.stop.db.a.class，发送到制定手机号与邮箱的配置信息。

![png](/assets/img/Androidworm/03.png)

5.登录源码内的邮箱：17190****@sina.cn

![png](/assets/img/Androidworm/04.png)

6.病毒从宿主手机内获取到的短信内容

![png](/assets/img/Androidworm/05.png)

7.病毒从宿主手机内获取到的通讯录内容

![png](/assets/img/Androidworm/06.png)

### 结语：在分析过程中采集到了很多相似的蠕虫病毒，黑产已经批量化作业，普通用户与谨慎。作为企业更需保护好用户数据，防止泄露