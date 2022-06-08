# 1.4 国际TLS密码套件过滤

### 产品指标

* 新渡-国密安全WEB网关支持TLS1.0、TLS1.1、TLS1.2、TLS1.3的官方RFC文档中提到的所有密码套件。

  &emsp;如：

  > * TLS_RSA_WITH_AES_256_CBC_SHA256
  >
  > * TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
  >
  > * TLS_CHACHA20_POLY1305_SHA256
  >
  >   ......

* 官方RFC文档如下

  > [RFC 3268](https://datatracker.ietf.org/doc/html/rfc3268)、[RFC 5932](https://datatracker.ietf.org/doc/html/rfc5932)、[ RFC 4162](https://datatracker.ietf.org/doc/html/rfc4162)、[RFC 4279](https://datatracker.ietf.org/doc/html/rfc4279)、[ RFC 4492](https://datatracker.ietf.org/doc/html/rfc4492)、[ RFC 4785](https://datatracker.ietf.org/doc/html/rfc4785)、[RFC 5054](https://datatracker.ietf.org/doc/html/rfc5054)、[RFC 5246](https://datatracker.ietf.org/doc/html/rfc5246)、[RFC 5288](https://datatracker.ietf.org/doc/html/rfc5288)、[RFC 5289](https://datatracker.ietf.org/doc/html/rfc5289)、
  >
  > [RFC 5487](https://datatracker.ietf.org/doc/html/rfc5487)、[ RFC 5489](https://datatracker.ietf.org/doc/html/rfc5489)、[ RFC 5746](https://datatracker.ietf.org/doc/html/rfc5746)、[RFC 6209](https://datatracker.ietf.org/doc/html/rfc6209)、[RFC 6367](https://datatracker.ietf.org/doc/html/rfc6367)、[ RFC 6655](https://datatracker.ietf.org/doc/html/rfc6655)、[RFC 7251](https://datatracker.ietf.org/doc/html/rfc7251)、[RFC 7905](https://datatracker.ietf.org/doc/html/rfc7905)、[RFC 8442](https://datatracker.ietf.org/doc/html/rfc8442)、[RFC 8446](https://datatracker.ietf.org/doc/html/rfc8446)

### 指标演示

<p style="color:red;font-weight:bold">
       注:由于TLS1.0、TLS1.1协议存在弱加密，当前很多主流浏览器已经废弃了这两个协议，所以这里不再对它们进行演示。
</p>
##### TLS 1.2

* 演示项目：为网关指定WEB应用使用TLS1.2协议访问网关时支持的密码套件。（以"TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256"为例）

* 预期结果："新渡-国密安全WEB网关"与WEB应用建立通信使用的密码套件为我们设置的密码套件。

* 演示过程：

  1. 首先我们打开[商用密码检测工具箱](https://www.ailawuyou.com/micetoolbox/)，进入流量分析，选择网络接口，过滤条件为"**host 网关地址**",然后我们勾选"SSL|VPN交互过程分析"，然后点击开始按钮，抓取WEB应用访问“新渡-国密安全WEB网关”的数据

     ![image-20220602164019887](../image/MiCeZhua.png ':size=75%')

  2. 我们将网关协议配置为只支持TLS1.2，这次密码套件我们不指定。

  3. 然后使用"谷歌浏览器"访问"新渡-国密安全WEB网关"。

  4. 分析数据包，由图看出，在我们没有指定密码套件的情况下，默认使用的是"TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 "

     ![image-20220607165221093](../image/guolv_tls12_moren.png ':size=75%')

  5. 然后我们将网关中使用的密码套件指定为"TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256"（**注：支持指定多个套件，这里为了方便演示只指定了一个密码套件**）

  6. 然后再次使用谷歌浏览器访问，并用商用密码应用与检测工具箱进行抓包。

  7. 分析数据包，由图可以看出，这次通信使用的套件已经成功改为了我们设置的密码套件:

     "TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256"

     ![image-20220607164055030](../image/guolv_tls12.png ':size=75%')

##### TLS 1.3

* 演示项目：为网关指定WEB应用使用TLS1.3协议访问网关时支持的密码套件。(以"TLS_CHACHA20_POLY1305_SHA256"为例)

* 预期结果："新渡-国密安全WEB网关"与WEB应用建立通信使用的密码套件为我们设置的密码套件。

* 演示过程：

  1. 首先我们打开[商用密码检测工具箱](https://www.ailawuyou.com/micetoolbox/)，进入流量分析，选择网络接口，过滤条件为"**host 网关地址**",然后我们勾选"SSL|VPN交互过程分析"，然后点击开始按钮，抓取浏览器访问“新渡-国密安全WEB网关”的数据

     ![image-20220602164019887](../image/MiCeZhua.png ':size=75%')

  2. 我们将网关协议配置为只支持TLS1.3，这次密码套件我们不指定。

  3. 然后使用"谷歌浏览器"访问"新渡-国密安全WEB网关"。

  4. 分析数据包，由图看出，在我们没有指定密码套件的情况下，默认使用的是" TLS_AES_256_GCM_SHA384"

     ![image-20220607170221337](../image/guolv_tls13_moren.png ':size=75%')

  5. 然后我们将网关中使用的密码套件指定为"TLS_CHACHA20_POLY1305_SHA256"（**注：支持指定多个套件，这里为了方便演示只指定了一个密码套件**）

  6. 然后再次使用谷歌浏览器访问，并用商用密码应用与检测工具箱进行抓包。

  7. 分析数据包，由图可以看出，这次通信使用的套件已经成功改为了我们设置的密码套件:

     "TLS_CHACHA20_POLY1305_SHA256"

     ![image-20220607171535137](../image/guolv_tls13.png ':size=75%')

至此，"新渡-国密安全WEB网关"国际TLS密码套件过滤演示完毕，结果与预期结果相同。
