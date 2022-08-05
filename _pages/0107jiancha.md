# 1.7后端服务器健康检查

### 产品指标

新渡-国密安全WEB网关支持检查后端服务器（集群）的健康情况。当后端服务器由于各种原因(如过载、资源泄漏、硬件故障等)而完全关闭后，网关会停止向这台服务器发送流量，并将流量发送至其它存活的后端服务器，直到这台服务器恢复为止。

新渡-国密安全WEB网关支持两种健康检查方式：主动检查和被动检查。

主动检查：

> 网关定期向后端服务器发送探测请求并分析响应情况来主动监测后端服务器的健康状况。

被动检查：

> 当网关访问后端服务器后，后端服务器的响应会被健康检查中间件拦截，然后分析该响应判断后端服务器的健康情况。

### 指标演示

<p style="color:red;font-weight:bold">
       注:此次演示以主动检查为例
</p>

* 演示项目：对后端服务器的主动健康检查

* 预期结果：在负载均衡的前提下，当我们没有添加主动健康检查时，关闭后端服务器A保留后端服务器B，访问网关时，网关依旧会先去尝试与后端服务器A建立连接，然后再与后端服务器B建立连接，会导致先提示无法与后端服务器A建立连接，然后再显示与后端服务器B建立通信，当配置主动健康检查后，无论访问多少次，在后端服务器A重新开启之前，网关都只与后端服务器B建立连接，当我们重新将后端服务器A开启之后，再次多次访问，网关又会分别与后端服务器A和后端服务器B建立连接。

* 演示过程：

  1. 首先我们不配置健康检查，然后关闭端口为5000的后端服务器A，保留端口为5001的后端服务器B。
  
  2. 然后使用"奇安信浏览器"多次访问网关，会先显示无法处理请求（因为端口为5000的后端服务器A关闭了），然后再成功与端口为5001后端服务器B建立连接。
  
     第一次访问：
  
     ![image-20220615164028463](../image/wu_jiankang.png ':size=75%')
  
     第二次访问：
  
     ![image-20220614162913667](../image/yarpfuzai5001.png ':size=75%')
  
  3. 然后我们配置主动健康检查，再次使用"奇安信浏览器"多次访问网关，会发现不管访问多少次，都只显示与端口为5001的后端服务器B建立连接，不会再显示与端口为5000的后端服务器A建立连接失败的提示。
  
  4. 当我们重新将端口为5000的后端服务器A开启之后，再次使用"奇安信浏览器"多次访问网关，会发现又会先显示与端口为5000的后端服务器A建立连接，然后显示与端口为5001的后端服务器B建立连接。
  
  至此，"新渡-国密安全WEB网关"的后端服务器健康检查功能演示完毕，结果与预期结果相同。
  
  ​	