---
title: 1.2国密TLS的单向认证和双向认证
author: 张雄飞
date: 2022-3-29
category: Jekyll
layout: post
---

* **国密单向认证**

  1. 首先我们打开国密版Wireshark，过滤条件为"**tls&&ip.addr==网关地址**",用于抓取浏览器访问“新渡-国密安全WEB网关（GMSWG）”的数据

     <div>
         <img src="{{ site.baseurl}}/image/Wireshark.png" width="950" height="400">
     </div>

  2. 然后我们使用"奇安信安全浏览器"访问“新渡-国密安全WEB网关（GMSWG）”，由图可看出成功建立国密连接
  
     <div>
         <img src="{{ site.baseurl}}/image/gm_cbc.png" width="950" height="550">
     </div>
  
  3. 查看国密版Wireshark抓取的数据包，由图可以看到此次通讯为标准的单项认证过程
  
     <div>
         <img src="{{ site.baseurl}}/image/danxiang.png" width="950" height="500">
     </div>
     
     


* **国密双向认证**

  1. 首先开启"新渡-国密安全WEB网关（GMSWG）"的请求客户端证书功能

  2. 然后准备用于存放国密证书的硬件key，并将国密证书导入

  3. 连接硬件key，然后我们使用"奇安信安全浏览器"访问“新渡-国密安全WEB网关（GMSWG）”，由图可以看到弹出了选择证书的页面，选择相应的国密证书，并输入硬件key的密码后点击确定

     <div>
         <img src="{{ site.baseurl}}/image/shuangxiang.png" width="950" height="500">
     </div>

  4. 成功访问

     <div>
         <img src="{{ site.baseurl}}/image/gm_cbc.png" width="950" height="550">
     </div>

  5. 查看国密版Wireshark抓取的数据包，由图可以看到此次通讯为标准的双向认证过程

     <div>
         <img src="{{ site.baseurl}}/image/shuang_wireshark.png" width="950" height="550">
     </div>

至此，"新渡-国密安全WEB网关（GMSWG）"的国密单向认证和双向认证测试完毕，测试结果为均成功连接
