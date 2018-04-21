# 用例建模

> 这是关于用例建模学习的知识汇总和实践。



## 什么是用例建模？

用讲故事的手段（自然语言故事），描述通过人机交互达成用户目标的过程。

它特别关注用户看到或期望系统处理的数据。



## 用例建模的制品有哪些？

- UML Usecase Diagram

- 用例描述
  - 用例文本
    - 简洁的用例文本（Brief）
    - 非正式的用例文本（Casual）
    - 详尽的用例文本（Detailed）
  - 故事板（Storyboard）
    - User interface-flow diagram
    - UI Prototypes



## 如何进行敏捷需求管理？

- 管理方法，如《硝烟中的 Scrum 和 XP》
- 管理工具，如 TAPD 腾讯敏捷产品开发



## 如何识别与组织需求？



###合理的用例识别（制作的用例图）给团队的利益

- 明确系统的业务范围、服务对象（角色）、外部系统与设备
- 帮助识别技术风险，提前实施关键技术原型公关与学习
- 易于评估项目工作量，合理规划迭代周期，规划人力需要



###需求识别的步骤

1. 确定研讨的系统
   - 使用用例图 System框，表示一个待研究的系统
   - 正确命名系统或子系统
   - **不要将研究的系统的名称起的太泛，以避免业务空泛问题**
2. 识别 Actors
   - 识别使用系统的主要参与者（primary actors）或角色（roles）
     - 使用用例图 Actor 符号表示，通常放在系统的左边
     - 企业应用可以通过企业组织架构，业务角色与职责识别
     - 互联网应用则必须通过市场分析，确定受众范围
     - **不要用「用户」代表系统使用者，以避免过于通用导致缺乏用户体验**
   - 识别系统依赖的外部系统
     - 使用用例图 Neighboursystem 框表示用例依赖的外部系统（<<system>>）、服务（<<service>>） 、设备（<<device>> 或 <<sensor>>），并使用构造型（Stereotype）识别
     - **将一些专业功能赋予专业系统，以确保系统的简洁与专业**
3. 识别用例（服务）
   - 识别用户级别用例（user goal level）
     - 以主要参与者目标驱动，收集主要参与者的业务事件
     - 必须满足 boss / EBP / Size test准则
   - 识别子功能级别的用例（sub function level）
     - 子用例特征：业务复用、复杂业务分解、强调技术或业务创新
     - 正确使用用例与子用例之间的关系
       - <<include>> 表示子用例是父用例的一部分，通常强调离开这个特性，父用例无法达成目标或失去意义
       - <<extend>> 表示子用例是父用例的可选场景或技术特征
       - 箭头表示的依赖关系，<<include>> 箭头指向子用例，<<extend>> 箭头指向父用例
4. 建立 Actor 和 Use Cases 之间的关联
   - 使用**无方向连线**，表示两间之间是双向交互的协议



###组织与跟踪需求

- 用树形结构组织需求

  ```c++
  -- system or sub system
    |-- usecase
      |-- sub usecase
      |-- scene
      |-- feature
  ```

- 可以投产的需求或特征
  - 一个迭代可以完成编码与测试
  - 可以独立测试




## 实践与参考

### 实践

- **Dinner Now**
- **Reserve Hotel**

### 参考

- [User interface-flow diagram](http://agilemodeling.com/artifacts/uiFlowDiagram.htm)
- [UI Prototypes](http://agilemodeling.com/artifacts/uiPrototype.htm)
- [编写有效用例（中／英）](http://download.csdn.net/detail/zyg345382708/3094197)
- [使用用例点估算软件成本](https://www.ibm.com/developerworks/cn/rational/edge/09/mar09/collaris_dekker/index.html)