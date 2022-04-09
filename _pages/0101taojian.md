1. 首先我们打开国密版Wireshark，过滤条件为"**tls&&ip.addr==网关地址**",用于抓取浏览器访问“新渡-国密安全WEB网关（GMSWG）”的数据

   <div>
       <img src="image/Wireshark.png" width="650" height="400">
   </div>

2. 然后我们使用"奇安信安全浏览器"访问“新渡-国密安全WEB网关（GMSWG）”，由图可看出成功建立国密连接，并且使用SM4_CBC进行加密

   <div>
       <img src="image/gm_cbc.png" width="850" height="650">
   </div>

3. 我们通过国密版Wireshark抓取的数据包可以看到，此次通讯使用国密套件为：ECC_SM4_CBC_SM3（0xE013）

   <div>
       <img src="image/Wireshark_cbc.png" width="850" height="650">
   </div>

4. 然后我们将“新渡-国密安全WEB网关（GMSWG）”默认使用的国密套件从：ECC_SM4_CBC_SM3 更改为：ECC_SM4_GCM_SM3,使用浏览器再次访问，由图可看出成功建立国密连接，并且使用SM4_GCM进行加密

   <div>
       <img src="image/gm_gcm.png" width="850" height="650">>
   </div>

5. 再次查看国密版Wireshark抓取的数据包，由图可以看到此次通讯使用国密套件为：ECC_SM4_GCM_SM3（0xE053）

   <div>
       <img src="image/Wireshark_gcm.png" width="850" height="650">>
   </div>

6. 至此，"新渡-国密安全WEB网关（GMSWG）"测试国密套件：ECC_SM4_CBC_SM3和ECC_SM4_GCM_SM3，测试完毕，均成功建立国密通信（注:还有两个国密套件没有测试）
