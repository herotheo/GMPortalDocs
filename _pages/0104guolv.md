# 1.4 国际TLS密码套件过滤

&emsp;&emsp;在密码套件中，不是所有密码套件都是安全的，如果使用了不安全的密码套件可能会导致被黑客攻击，所以我们要配置密码套件过滤来指定TLS使用安全的密码套件，来避免这个问题。

对于密码套件的选取有以下原则：

> * 支持的SSL/TLS版本：TLS1.2，TLS1.3（禁用SSLV3 TLS1.0和TLS1.1）
> * 密钥交换算法禁用DH，ADH，优选DHE(2048)和ECHDE，保留RSA（原则上禁用）
> * 认证算法使用：RSA和ECDSA，禁用none
> * 对称加密算法使用：AES, Camellia, ChaCha20, 禁用DES, 3DES, RC4,SEED
> * 工作模式推荐：AES-GCM， ChaCha20_POLY1305，禁用CBC（弱安全性）
> * MAC算法：SHA384，SHA256，禁用SHA1,MD5

<p style="color:red;font-weight:bold">
       注:TLS1.0、TLS1.1协议存在弱加密支持，当前很多主流浏览器已经废弃了这两个协议，所以这里不再演示对它们的套件过滤。
</p>


## 1.4.1 TLS 1.2

针对TLS1.2，推荐以下3种程度安全要求的密码套件：

1.  TLS1.2密码套件中满足[前向安全性](https://baike.baidu.com/item/%E5%89%8D%E5%90%91%E5%AE%89%E5%85%A8%E6%80%A7/6357798?fr=aladdin)，禁用CBC的密码套件推荐如下所示

   > * TLS_DHE_RSA_WITH_AES_128_GCM_SHA256  RSA证书
   > * TLS_DHE_RSA_WITH_AES_256_GCM_SHA384  RSA证书
   > * TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256  RSA证书
   > * TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384  RSA证书
   > * TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256  ecc证书
   > * TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384  ecc证书

1. 在"1"的安全要求下，考虑效率，因为DHE算法效率低，通常不建议。则满足前向安全，禁用CBC，保证高效率的密码套件如下所示：

   > * TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
   > * TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
   > * TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
   > * TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384

1. 严格意义上128位的加密算法AES并不能保证安全性。所以在"2"的基础上推荐的密码套件如下所示：

   >* TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
   >* TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384

下面对TLS1.2协议套件过滤进行演示：

1. 首先我们打开[商用密码检测工具箱](https://www.ailawuyou.com/micetoolbox/)，进入流量分析，选择网络接口，过滤条件为"**host 网关地址**",然后我们勾选"SSL|VPN交互过程分析"，然后点击开始按钮，抓取浏览器访问“新渡-国密安全WEB网关（GMSWG）”的数据

   ![image-20220602164019887](../image/MiCeZhua.png ':size=75%')

2. 我们将网关协议配置为只支持TLS1.2，这次密码套件我们不指定。

3. 然后使用"谷歌浏览器"访问"新渡-国密安全WEB网关（GMSWG）",由图可见成功访问

   ![google](../image/google.png ':size=75%')

4. 分析数据包，由图看出，在我们没有指定密码套件的情况下，默认使用的是"TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 "

   ![image-20220607165221093](../image/guolv_tls12_moren.png ':size=75%')

5. 然后我们在网关中指定使用的密码套件为"TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256"(可以同时指定多个套件)

6. 然后再次使用谷歌浏览器访问，并用商用密码应用与检测工具箱进行抓包。

7. 分析数据包，由图可以看出，这次通信使用的套件已经成功改为了我们设置的密码套件:

   "TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256"

   ![image-20220607164055030](../image/guolv_tls12.png ':size=75%')

## 1.4.2 TLS 1.3

目前TLS 1.3支持的密码套件有：

> * TLS-AES128-GCM-SHA256
> * TLS-AES256-GCM-SHA384
> * TLS-CHACHA20-POLY1305-SHA256
> * TLS-AES128-CCM-SHA256
> * TLS-AES128-CCM-8-SHA256

下面对TLS1.3协议套件过滤进行演示：

1. 首先我们打开[商用密码检测工具箱](https://www.ailawuyou.com/micetoolbox/)，进入流量分析，选择网络接口，过滤条件为"**host 网关地址**",然后我们勾选"SSL|VPN交互过程分析"，然后点击开始按钮，抓取浏览器访问“新渡-国密安全WEB网关（GMSWG）”的数据

   ![image-20220602164019887](../image/MiCeZhua.png ':size=75%')

2. 我们将网关协议配置为只支持TLS1.3，这次密码套件我们不指定。

3. 然后使用"谷歌浏览器"访问"新渡-国密安全WEB网关（GMSWG）",由图可见成功访问

   ![google](../image/google.png ':size=75%')

4. 分析数据包，由图看出，在我们没有指定密码套件的情况下，默认使用的是" TLS_AES_256_GCM_SHA384"

   ![image-20220607170221337](../image/guolv_tls13_moren.png ':size=75%')

5. 然后我们在网关中指定使用的密码套件为"TLS_AES_128_GCM_SHA256"(可以同时指定多个套件)

6. 然后再次使用谷歌浏览器访问，并用商用密码应用与检测工具箱进行抓包。

7. 分析数据包，由图可以看出，这次通信使用的套件已经成功改为了我们设置的密码套件:

   "TLS_AES_128_GCM_SHA256"

   ![image-20220607171535137](../image/guolv_tls13.png ':size=75%')

