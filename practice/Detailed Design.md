 # 详细设计

> 使用交互图和设计类图实现用例。



## 设计的核心

- 以业务场景为中心
- 减少对具体语言实现和技术依赖



## 方法 - BCE 模型

### 准备

- 用例
- 界面原型与外部系统接口文档
- 领域模型与数据库设计（ER 逻辑模型）
- 逻辑架构与应用程序框架



### 识别类

- **Boundary**：与外部 Actor 交互的类（包括 UI、外部系统接口）
- **Controller**：处理外部事件，实现控制流的类（通常是一个子系统、一个用例一个类）
- **Entity**：领域对象或数据实体



### 动态图设计

- UI类（如业务表单）放最左边，控制器对象放置中间，实体放置右边，外部系统放在最右边

  - 使用构造型细化四种类

  - **Boundary**，**Controller**，**Entity**，Interface / Boundary

- 按 BCE 规则实现用例中主要场景
  - Boundary 只能和 Controller 联系，Controller 处理 UI 事件

  - Entity 只能和 Controller 联系，Controller 请求 Entity 加工自己或关联的数据

    - 即 Entity 提供业务服务，包括简单的 CRUD 资源操作

- 按 UI 事件顺序，描述 UI 事件被处理的过程



### 静态设计

- Boundary 对象（完善界面不在讨论范围内）
- Controller 对象

  - Boundary 发生的用户事件消息，皆是 Controller 的方法。

  - 以下都是不正确的交互（严格的层次模型）：

    - UI 有箭头指向模型（注意 ViewModel 与 Model 的区别）

    - 模型有箭头指向控制器。或控制器有除创建之外的箭头指向界面

    - 无论安卓或web，控制器都设计为多用户。即控制器不包含状态变量
  - 不能考虑多线程，使用多线程更新界面。要使用回调函数（消息）机制完成异步操作。
- Entity 对象
  - 从 领域模型 获取属性
  - 如果模型之间存在关联，请将关系转化为合适的实现（关联属性）
  - 将 Controller 消息转化为方法

### 映射

不同架构和框架映射机制不一样，以传统 java web 为例：

- 表示层
  - M （ViewModel） 与 用例涉及的 Entities 数据一致， 放入 models 或 pojos 或 entities 包
  - V （View） 就是视图模板，或部分视图模板（如查询表单）
  - C （Controller） 与 Controller 对象一致，处理一类 UI 事件
  - 如果模板数据 是 Entities 数据的投影、join，设计为 dto（data transfer object） 对象，放入 dtos 包
  - 如果一个表达或数据需要在多个界面共享，可设计为应用程序范围或 Session 范围变量，如输入表单，一般放入 form 包
  - 将常用数据验证方法、翻页等，应写成统一的实用程序包 utilities
  - 将常用数据转换（序列化、反序列化、格式化）类，放在 converter 包中
- 业务层（services 包）
  - Entities 的方法
  - 获取关联对象的方法
- 数据层（daos 或 repos 包）
  - Entities 的 CRUD 方法

