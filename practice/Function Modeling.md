# 功能建模

> 下面是关于功能建模学习的知识汇总。



## 什么是功能建模？

给出系统面向外部实体（用户及外部系统）要实现的**业务操作**功能的定义。



## 为什么要进行功能建模？

- 识别所有系统要提供的业务操作，给出严格的定义。
- 通过识别这些操作，精确的估算工作量。
- 完善系统实现的细节（消息、参数）等，进一步完善领域模型与资源API设计。



## 建模方法与工具

- 系统顺序图（System Sequence Diagram）
- 操作协议（Operation contracts）
- 基于功能点的项目工作量估计（Function Points）



## 案例研究

- [理解OAuth2.0](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html) 与[微信 OAuth2.0 授权登录的系统顺序图](https://open.weixin.qq.com/cgi-bin/showdocument?action=dir_list&t=resource/res_list&verify=1&id=open1419317851&token=&lang=zh_CN)。
- 微信小程序开放接口（login）工作原理的系统顺序图。



## 功能点

功能点的计算步骤：

1. 确定计算类型（3种）：
   - 优化（项目）的功能点计算
   - 应用的功能点计算
   - 开发（项目）的功能点计算
2. 识别计算范围与应用边界
3. 计算数据功能（内部/外部存储）
4. 计算业务功能（外部输入/输出/查询）
5. 确定 Unadjusted 功能点的数量
6. 确定 Value Adjustment Factor
7. 计算 Adjusted 功能点的数量 

