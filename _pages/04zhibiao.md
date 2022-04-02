---
title: 1.产品指标验证
author: 张雄飞
date: 2022-3-29
category: Jekyll
layout: post
---

## 国密套件

这里使用"奇安信安全浏览器"访问新渡-国密WEB应用安全网关(https://home.hccie.com:21443)，使用国密版Wireshark抓包分析。

通过密版Wireshark抓包可以看到，通讯使用国密套件：ECC_SM4_GCM_SM3，成功建立国密通信连接。

<div>
    <img src="{{ site.baseurl}}/image/toajian1.png" width="950" height="400">
</div>

第二次更换国密套件进行访问 此处使用国密套件：ECC_SM4_CBC_SM3并且也成功建立国密通信

<div>
    <img src="{{ site.baseurl}}/image/toajian2" width="950" height="400">
</div>









## 国密TLS的单向认证和双向认证

todo 添加国密证书吊销CRL地址（说一下就行）

## 支持http1 和http2 、支持grpc

todo

## 配置多域名等参数

todo 关键图放在这里



## 使用Keepalived提供高可用功能

todo

## 负载均衡

todo

## 性能测试

todo

## 国际TLS自定义密码套件过滤

todo

## 后面就是对yarp的一些配置 这里不知道怎么写

todo
