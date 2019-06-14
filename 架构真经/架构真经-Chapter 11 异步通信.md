# Rule 43: 尽可能使用异步通信
**内容**：优先使用异步通信，而不是同步通信   
**原因**: 同步调用使整个程序停下来等待响应，它捆绑所有的服务和层，进而导致连锁性延迟或故障   

异步的麻烦之处：有的时候，异步操作完成后需要通知调用者操作的结果 (e.g. callback, 设计模式)  

故障的乘法效应： 
A，B，C模块 - 99%无故障  
放在一起：无故障99% x 99% x 99% = 97%  

如果必须用同步方式处理，设置超时  

### 何时使用异步调用：
- 外部API，第三方：TeamViewer API, Azure AD, Darwin等等
- 长时间运行的进程，对计算或者I/O要求很高
- 容易出错/过于复杂的方法 并且经常修改
- 没有时间约束：发送邮件——发送结果，但不要阻塞

> ===>标准越多，适用性越差  

# Rule 44: 扩展消息总线(message bus)
**内容**：消息总线会因需求而失败，所以需要进行扩展  
**原因**: 确保可以扩展以满足用户需求  
**用法**：在需求到来之前，采用AKF的Y轴和Z轴拆分  

[Message bus](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageBus.html)  
A Message Bus is a messaging infrastructure to allow different systems to communicate through a shared set of interfaces(message bus).  
![](https://i.stack.imgur.com/5PkJy.gif)  

### Message Queue vs Message Bus
> https://ardalis.com/bus-or-queue
> https://stackoverflow.com/questions/7793927/message-queue-vs-message-bus-what-are-the-differences

常见故障：消息总线的单点故障  

![](https://github.com/Carlos-Liu/Notes4Work/blob/master/%E5%AD%A6%E4%B9%A0%E6%80%BB%E7%BB%93/images/%E6%9E%B6%E6%9E%84%E7%9C%9F%E7%BB%8F/2018-09-12_10-06-23.jpg)

Y轴拆分的方法  
![](https://github.com/Carlos-Liu/Notes4Work/blob/master/%E5%AD%A6%E4%B9%A0%E6%80%BB%E7%BB%93/images/%E6%9E%B6%E6%9E%84%E7%9C%9F%E7%BB%8F/2018-09-12_10-39-52.jpg)

### 缺点
- 降低使用的灵活性

不同泳道/豌豆夹都有自己专用的消息总线，如果进行扩展（Y轴orZ轴）也取决于服务和资源是如何进行拆分的  
不应该完全依赖Paas提供的解决方案：供应商不会设计你的架构  
需要思考：这个平台可能会出现什么样的故障？如何对其进行扩展？  

# Rule 45: 避免总线过度拥挤
**内容**：总线流量仅限于那些价值高于处理成本的事件  
**原因**: **消息流量不是免费的，对系统有昂贵的要求**  
**用法**：价值+成本判断消息流量  

基于rule 44，考虑**成本**  

### 要点：
- 不要重复log类似的信息,e.g. 同一个错误写了多条log
- 精简log，不要妄图捕获系统所做的一切活动  
- 数据发布到消息总线上的成本 v.s. 带来的价值
- 成本：消息总线允许需要硬件/虚拟机，CM，DevOps
- 采样可以降低成本
- **不是所有的数据都有相同的价值，但是其成本可能是相同的**
