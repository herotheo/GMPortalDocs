## 1.2.1 国密单向认证

* 演示项目：国密单向认证演示

* 预期结果：WEB应用在国密环境下访问“新渡-国密安全WEB网关（GMSWG）”成功建立国密通信，并且通过Wireshark分析访问过程为标准的TLS单向认证过程

* 演示过程：

  1. 首先我们打开国密版Wireshark，过滤条件为"**tls&&ip.addr==网关地址**",用于抓取浏览器访问“新渡-国密安全WEB网关（GMSWG）”的数据

     ![Wireshark](../image/Wireshark.png ':size=75%')

  2. 然后我们使用"奇安信安全浏览器"访问“新渡-国密安全WEB网关（GMSWG）”，由图可看出成功建立国密连接

     ![gm_cbc](../image/gm_cbc.png ':size=75%')

  3. 查看国密版Wireshark抓取的数据包，由图可以看到此次通讯为标准的单向认证过程

     ![danxiang](../image/danxiang.png ':size=75%')

## 1.2.2 国密双向认证

* 演示项目：国密双向认证演示

* 预期结果：WEB应用载国密环境下访问“新渡-国密安全WEB网关（GMSWG）”成功建立国密通信，并且通过Wireshark分析访问过程为标准的TLS双向认证过程

* 演示过程：

  1. 首先开启"新渡-国密安全WEB网关（GMSWG）"的请求客户端证书功能

  2. 然后准备用于存放国密证书的硬件key，并将国密证书导入

  3. 连接硬件key，然后我们使用"奇安信安全浏览器"访问“新渡-国密安全WEB网关（GMSWG）”，由图可以看到弹出了选择证书的页面，选择相应的国密证书，并输入硬件key的密码后点击确定

     ![shuangxiang](../image/shuangxiang.png ':size=75%')

  4. 成功访问

     ![gm_cbc](../image/gm_cbc.png ':size=75%')

  5. 查看国密版Wireshark抓取的数据包，由图可以看到此次通讯为标准的TLS双向认证过程

     ![shuang_wireshark](../image/shuang_wireshark.png ':size=75%')

  至此，"新渡-国密安全WEB网关（GMSWG）"的国密单向认证和双向认证演示完毕，结果与预期结果相同。

