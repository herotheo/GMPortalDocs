1. 首先我们打开国密版Wireshark，过滤条件为"**tls&&ip.addr==网关地址**",用于抓取浏览器访问“新渡-国密安全WEB网关（GMSWG）”的数据

   ![Wireshark](../image/Wireshark.png ':size=75%')

2. 先使用"奇安信安全浏览器"访问"新渡-国密安全WEB网关（GMSWG）",由图可见成功访问

   ![gm_cbc](../image/gm_cbc.png ':size=75%')

3. 然后使用"谷歌浏览器"访问"新渡-国密安全WEB网关（GMSWG）",由图可见成功访问

   ![google](../image/google.png ':size=75%')

4. 查看国密版Wireshark抓取的数据包，由图可以看出即成功建立了国密通信又成功建立了国际通信

   ![Wireshark_gmgj](../image/Wireshark_gmgj.png ':size=75%')

至此，"新渡-国密安全WEB网关（GMSWG）"国际国密访问自适应测试完毕，测试结果为支持国际国密访问自适应。
