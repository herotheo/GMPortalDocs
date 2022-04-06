---
title: 1.产品指标验证
author: 张雄飞
date: 2022-3-29
category: Jekyll
layout: post
---

<p>
    <b style="color:red">
       注:以下测试均使用"奇安信安全浏览器"访问“新渡-国密WEB应用安全网关”(https://home.hccie.com:21443)，使用国密版Wireshark抓包分析。
    </b>
</p>
## 1. 国密套件

通过密版Wireshark抓包可以看到，通讯使用国密套件：ECC_SM4_GCM_SM3，成功建立国密通信连接。

<div>
    <img src="{{ site.baseurl}}/image/toajian1.png" width="950" height="400">
</div>

第二次更换国密套件进行访问 此处使用国密套件：ECC_SM4_CBC_SM3并且也成功建立国密通信

<div>
    <img src="{{ site.baseurl}}/image/toajian2.png" width="950" height="400">
</div>

## 2. 国密TLS的单向认证和双向认证

#### 1. 国密单向认证

使用"国密数字证书"自签证书。

<div>
    <img src="{{ site.baseurl}}/image/danxiang.png" width="950" height="550">
</div>


#### 2. 国密双向认证

1. 准备将密钥证书写入的硬件key

2. 准备好硬件Key后，访问“新渡-国密WEB应用安全网关”(https://home.hccie.com:21443)，并使用国密版Wireshark抓包记录

   <div>
       <img src="{{ site.baseurl}}/image/shuangxiang1.png" width="950" height="550">
   </div>


   成功访问

   <div>
       <img src="{{ site.baseurl}}/image/shuangxiang2.png" width="950" height="400">
   </div>

3. 查看Wireshark抓包记录，可以看到网关发送的客户端证书请求和客户端返回的证书请求

   <div>
       <img src="{{ site.baseurl}}/image/shuangxiang3.png" width="950" height="550">
   </div>



## 3. 国密国际自适应



## 4. 支持http1 和http2 、支持grpc

todo

## 5. 配置多域名等参数

todo 关键图放在这里



## 6. 使用Keepalived提供高可用功能

todo

## 7. 负载均衡

todo

## 8. 性能测试

todo

## 9. 国际TLS自定义密码套件过滤

todo

## 后面就是对yarp的一些配置 这里不知道怎么写

todo
