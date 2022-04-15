# 1.1 国密套件

* 演示项目：国密套件演示

* 预期结果：WEB应用在国密环境下使用国密套件ECC_SM4_CBC_SM3（0xE013）或ECC_SM4_GCM_SM3（0xE053）访问“新渡-国密安全WEB网关（GMSWG）”均成功建立国密通信

* 演示过程：

  1. 首先我们打开国密版Wireshark，过滤条件为"**tls&&ip.addr==网关地址**",用于抓取浏览器访问“新渡-国密安全WEB网关（GMSWG）”的数据

     ![Wireshark](../image/Wireshark.png ':size=75%')

  2. 然后我们使用"奇安信安全浏览器"访问“新渡-国密安全WEB网关（GMSWG）”，由图可看出成功建立国密连接，并且使用SM4_CBC进行加密

     ![gm_cbc](../image/gm_cbc.png ':size=75%')

     

  3. 我们通过国密版Wireshark抓取的数据包可以看到，此次通讯使用的国密套件为：ECC_SM4_CBC_SM3（0xE013）

     ![Wireshark_cbc](../image/Wireshark_cbc.png ':size=75%')

  4. 然后我们将“新渡-国密安全WEB网关（GMSWG）”默认使用的国密套件从：ECC_SM4_CBC_SM3 更改为：ECC_SM4_GCM_SM3,使用浏览器再次访问，由图可看出成功建立国密连接，并且使用SM4_GCM进行加密

     ![gm_gcm](../image/gm_gcm.png ':size=75%')

  5. 再次查看国密版Wireshark抓取的数据包，由图可以看到此次通讯使用的国密套件为：ECC_SM4_GCM_SM3（0xE053）

     ![Wireshark_gcm](../image/Wireshark_gcm.png ':size=75%')

     至此，"新渡-国密安全WEB网关（GMSWG）"演示国密套件：ECC_SM4_CBC_SM3和ECC_SM4_GCM_SM3，演示完毕，结果与预期结果相同。（注:还有两个国密套件没有演示）

     

