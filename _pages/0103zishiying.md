1. 首先我们打开国密版Wireshark，过滤条件为"**tls&&ip.addr==网关地址**",用于抓取浏览器访问“新渡-国密安全WEB网关（GMSWG）”的数据

   <div>
       <img src="image/Wireshark.png" width="850" height="550">
   </div>

2. 先使用"奇安信安全浏览器"访问"新渡-国密安全WEB网关（GMSWG）",由图可见成功访问

   <div>
       <img src="image/gm_cbc.png" width="850" height="650">
   </div>

3. 然后使用"谷歌浏览器"访问"新渡-国密安全WEB网关（GMSWG）",由图可见成功访问

   <div>
       <img src="image/google.png" width="850" height="650">
   </div>

4. 查看国密版Wireshark抓取的数据包，由图可以看出即成功建立了国密通信又成功建立了国际通信

   <div>
       <img src="image/Wireshark_gmgj.png" width="850" height="650">
   </div>

至此，"新渡-国密安全WEB网关（GMSWG）"国际国密访问自适应测试完毕，测试结果为支持国际国密访问自适应。