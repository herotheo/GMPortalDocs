# 1.1 国密套件

### 产品指标

新渡-国密安全WEB网关与客户端建立国密通信时支持的国密套件有:

> * ECC_SM4_CBC_SM3 （0xE013）
> * ECC_SM4_GCM_SM3（0xE053）
> * ECDHE_SM4_CBC_SM3（0xE011）
> * ECDHE_SM4_GCM_SM3（0xE051）

### 指标演示

* 演示项目：配置网关与客户端通信时使用的国密套件（以ECC_SM4_CBC_SM3和ECC_SM4_GCM_SM3为例）

* 预期结果：使用支持国密协议的客户端访问“新渡-国密安全WEB网关”成功建立国密通信，并通过分析抓包数据可以看出使用的密码套件为我们配置的国密套件。

* 演示过程：

  1. 首先我们打开"[商用密码应用与检测工具箱](https://www.ailawuyou.com/micetoolbox/)"，进入流量分析，选择网络接口，过滤条件为"**host 网关地址**",然后我们勾选"SSL|VPN交互过程分析"，然后点击开始按钮，抓取客户端访问“新渡-国密安全WEB网关”的数据

     ![image-20220602164019887](../image/MiCeZhua.png ':size=75%')

  2. 然后我们使用"奇安信安全浏览器"访问“新渡-国密安全WEB网关”，由图可看出成功建立国密连接，并且使用SM4_CBC进行加密

     ![gm_cbc](../image/gm_cbc.png ':size=75%')

     

  3. 我们通过抓取的数据包可以看到，此次通讯使用的国密套件为：ECC_SM4_CBC_SM3（0xE013）

     ![image-20220602164249274](../image/MiCe_CBC.png ':size=75%')

  4. 然后我们将“新渡-国密安全WEB网关”默认使用的国密套件从：ECC_SM4_CBC_SM3 更改为：ECC_SM4_GCM_SM3,使用浏览器再次访问，由图可看出成功建立国密连接，并且使用SM4_GCM进行加密

     ![gm_gcm](../image/gm_gcm.png ':size=75%')

  5. 再次查看抓取的数据包，由图可以看到此次通讯使用的国密套件为：ECC_SM4_GCM_SM3（0xE053）

     ![image-20220602164502186](../image/MiCe_GCM.png ':size=75%')

     

     至此，"新渡-国密安全WEB网关"演示国密套件：ECC_SM4_CBC_SM3和ECC_SM4_GCM_SM3，演示完毕，结果与预期结果相同。

     

