![](https://i.postimg.cc/dtdTv30G/image.png)

# Software Engineering Series | 软件工程、算法与架构

软件开发就是把一个复杂的问题分解为一系列简单的问题，再把一系列简单的解决方案组合成一个复杂的解决方案。而软件开发中最大的挑战，就是即能够快速高效地针对需求、环境的变化做出改变，也能够持续提供稳定、高可用的服务。

在笔者的系列文章中，分门别类地讨论了 Web、服务端、基础架构等某些具体的领域，而本系列关注形而上的软件工程相关的思考方式、通用能力与设计原则。为了更好地阐述，本系列默认使用 Java 为实现语言，不过你也可以在各篇的编程实现章节中查阅 TS、Go、Python、PHP、Rust 等其他版本的实现。

# Preface | 前言，从编码到软件系统

一般来说，在软件工程中，我们往往会面临三类问题：性能问题（The Performant System Problem）、系统的嵌入式问题（the Embedded System Problem）以及复杂领域建模问题（the Complex Domain Problem）。

![](https://i.postimg.cc/wBjMt2jj/image.png)

系统泛指由一群有关联的个体组成，根据某种规则运作，能完成个别元件不能单独完成的工作的群体。子系统也是由一群有关联的个体所组成的系统，多半会是更大系统中的一部分。

关联：系统是由一群有关联的个体组成的，没有关联的个体堆在一起不能成为一个系统。例如，把一个发动机和一台 PC 放在一起不能称之为一个系统，把发动机、底盘、轮胎、车架组合起来才能成为一台汽车。

规则：系统内的个体需要按照指定的规则运作，而不是单个个体各自为政。规则规定了系统内个体分工和协作的方式。例如，汽车发动机负责产生动力，然后通过变速器和传动轴，将动力输出到车轮上，从而驱动汽车前进。

能力：系统能力与个体能力有本质的差别，系统能力不是个体能力之和，而是产生了新的能力。例如，汽车能够载重前进，而发动机、变速器、传动轴、车轮本身都不具备这样的能力。

# 模块与组件

软件模块(Module)是一套一致而互相有紧密关连的软件组织。它分别包含了程序和数据结构两部分。现代软件开发往往利用模块作为合成的单位。模块的接口表达了由该模块提供的功能和调用它时所需的元素。模块是可能分开被编写的单位。这使它们可再用和允许人员同时协作、编写及研究不同的模块。

软件组件定义为自包含的、可编程的、可重用的、与语言无关的软件单元，软件组件可以很容易被用于组装应用程序中。模块和组件都是系统的组成部分，只是从不同的角度拆分系统而已。

从逻辑的角度来拆分系统后，得到的单元就是“模块”；从物理的角度来拆分系统后，得到的单元就是“组件”。划分模块的主要目的是职责分离；划分组件的主要目的是单元复用。其实，“组件”的英文 component 也可翻译成中文的“零件”一词，“零件”更容易理解一些，“零件”是一个物理的概念，并且具备“独立且可替换”的特点。

# 框架与架构

软件框架(Software framework)通常指的是为了实现某个业界标准或完成特定基本任务的软件组件规范，也指为了实现某个软件组件规范时，提供规范所要求之基础功能的软件产品。框架是组件规范，提供基础功能的产品。

软件架构指软件系统的顶层结构。首先，“系统是一群关联个体组成”，这些“个体”可以是“子系统”“模块”“组件”等；架构需要明确系统包含哪些“个体”。

其次，系统中的个体需要“根据某种规则”运作，架构需要明确个体运作和协作的规则。

第三，维基百科定义的架构用到了“基础结构”这个说法，我改为“顶层结构”，可以更好地区分系统和子系统，避免将系统架构和子系统架构混淆在一起导致架构层次混乱。

# 逻辑

逻辑的抽象复用可以说是所有软件开发活动中最为重要的一条原则，衡量一个程序员代码水平的重要原则之一就是看他代码中重复代码和相似代码的比例。大量重复代码或相似代码背后反映的是工程师思维的懒惰，因为他觉得复制粘贴或者直接照着抄是最省事的做法。这样做不仅看上去非常的丑陋，而且也非常容易出错，更不用提维护起来的难度。

# 数据中台

产品化是一种技术沉淀，从 CASE BY CASE 支持业务功能过程中，作抽象，把一些通用功能和模块独立出来，配合一些周边的技术工具和便利化的管理界面，形成产品化的结果，更高效的实现一种或多种业务需求，是技术效能提升的方法之一。产品化作得好的系统是一个闭封性优秀的系统，尽量不要外面的使用者关心我内部的实现。

模块化是把系统分离的一种设计思路，模块化后可以方便重复使用和插拨到不同的平台，不同的业务逻辑过程中。

产品化的系统一般都会在内部实现组件化，把模块独立抽象成组件，分离组件边界和责任，便于独立升级和维护。组件化可以让一个产品化的系统更可维护。

平台是一组程序的集合，提供了一系列的接口或界面。平台化是让一个系统具备装载很多不同外部系统的能力。平台化作得好的系统，要吧让外部系统很方便的了解你的内部能力，实现自由方便的插拨。平台化是一种对外的能力，提升的是外部系统与平台系统之间的联接能力，以开放作为设计目标，而不是封闭。

我们的系统有很多服务中心，会员中心，商品中心，产易中心和营销中心等。建这些中心的目的是为了业务系统解偶，为了让业务系统能更专注各自的业务逻辑，让通用业务下沉或平移抽出成为服务中心。中心化和组件化的不同一般是远程和本地的区别。以前客户端软件多用组件化设计，而互联网架构多用中心化，服务中心内部可以有不同的组件化设计，业务系统内部也常用组件化的设计。
中心化可以隔离易变和不易变的逻辑，也可以隔离不同运维策略的业务逻辑。中心化的系统一般符合职责单一原则，在面对对象设计的理论下，中心化可以看作一个逻辑上的大的对象来对待。服务中心是一个完整的业务闭包，可以完成一整组业务逻辑。
中心化不一定需要服务化。业务单元也可以中心化。

服务化，服务化一般是指远程调用的形式，我们关注调用的协议，API 和内容的格式。一个 API 可以独立服务化，一个服务中心也可以通过网关来实现服务化。
服务化有时候也用本地的二方库，类库包的形式提供服务。
服务化关注服务的治理策略和方法，手段。服务化关注服务注册，服务协调，服务可用性，服务通讯协议和内容交换。

SOA 是为了更好的集成，为了隔离不同逻辑之间的互相影响而形成的架构设计理念。服务化是 SOA 的一种实现方式。SPI 是一个接口标准规范，需要别人去实现；API 是标准的实现，可以直接使用。

架构师是一个既需要看全局整体又需要攻坚局部瓶颈并能在业务场景中平衡取舍方案的人，中台和前台，后台都需要架构师，架构师有自已的领域经验。

架构师是分领域的。架构师通过领域建模来划分业务边界，用领域经验来隔离变化，预测变化。很多系统的重复建设，与架架构的领域分拆不清楚有关系。可以借这个底层的实体关系模型来帮助系统建模，找到所有角色、实体对象和关系。
领域建模是一个抽象事实的过程。要为将来的业务扩展性和变化作好足够的准备。

中台和前台的区别是，前台实现业务逻辑和试错，需要比较多的人，这些人可能会失败。而中台实现通用逻辑和工具，产品，帮助前台快速试错，中台失败的可能性应该比较低，把可能错的事让前台去完成。中台人要少，前台人要多。如果前台人少，中台人多，那这个中台基本上应该归属到前台。中台的重点是产品化和平台化。中台应该是一系列能力的组合，包括组织规范和系统的规范，人和系统的一个方法论，标准。

诉求不是需求，而是需求的本质。电商业务中台由一系列业务能力标准、运行机制、业务分析方法论，配置管理和执行系统以及运营服务团队构成的体系，提供各业务方能够快速，低成本创新的能力。

定义能力的定义与标准，提供一个能力注册、发现、查询等管理的机制与管理系统；提供全局性的业务或应用注册管理中心，要让业务跑在大平台上，而不是一个或几个平台上。

提供一套或多套领域对象建模方法论或标准，比如按领域驱动设计 DDD；提供一系列成熟的案例或解决方案，提供多端化开发规范。

定义平台化的标准，定义可以实现平台化的框架的标准，比如框架需要提供模块化、流程化、插件、扩展等功能 。平台化的标准是什么？玄难大师有个很好的比喻，如果你的业务能一键上线或下线，就接近平台化了。这里的一键上下线，不是指单纯的切换一个开关，而是要做到部署的代码里不再有和该业务相关的任何代码。

平台化的基础构建，定义业务规则的定义，提供一个统一的业务规则平台（非中心，非动态编译引擎），支持自定义 DSL 插件，权限，审批流程等等，最终每个业务方都可形成自己业务领域的知识库。建设元数据管理中心，与业务规则等平台打通。提供一套服务鉴权的机制。可配置固然重要，但其重要性远低于平台化。

# 软件设计

软件设计有以下四大目标：简单、正确、一致、完整，但两大流派 MIT Style (MIT AI Lab 是 LISP 重镇) 和 New Jersey Style (C 和 UNIX 的老家贝尔实验室所在地) 对这些目标的优先级排序不同。MIT Style 认为软件正确性要绝对保证，然后优先级 正确 ~= 一致 > 完整 > 简单，简单这一条还得分，为了接口简单，可以忍受实现复杂。而 New Jersey Style 是正好反过来：首先软件实现得简单，做不到宁愿让接口复杂点，为了简单显然可以牺牲完整性，而正确、一致，那就尽力吧…… 反正得简单。Worse is Better 前面的 Worse 指的就是像 UNIX 这样为简单甚至能放弃「正确」这种有绝对标准的好的东西，后面的 Better, 指的是更好的生存适应性，这里面不带价值判断，文章作者也为 "Worse Is Better Is Worse" or "Worse is Better is Still Better" 一直在纠结，但这是一个能解释很多现象的准确观察。

## 性能

以著名的 Twitter 为例，你注册，你发推文，你喜欢别人的推文，这就是它。如果 Twitter 很简单，为什么其他人不能这样做呢？很明显，Twitter 的真正挑战实际上不是“它做什么”，而是它“如何做它能做的事情”。

Twitter 面临着每天为大约 5 亿用户提供服务的独特挑战。Twitter 解决的难题实际上是一个性能问题。当挑战是表现时，我们是否使用严格类型的语言并不重要。

## 系统嵌入

嵌入式系统是计算机硬件和软件的组合，其目的是实现对系统的机械或电气方面的控制。我们今天使用的大多数系统都是建立在一个非常复杂的代码层上，如果不是最初编写的，通常会编译成 C 或 C ++。

用这些语言编码不适合胆小的人。在 C 中，没有物体这样的东西; 我们作为人类喜欢物体，因为我们可以很容易地理解它们。C 是程序性的，这使我们用这种语言编写的代码更加难以保持清洁。这些问题还需要了解较低级别的细节。

C ++确实让生活变得更好，因为它具有面向对象，但挑战仍然是与较低级别的硬件细节进行有趣的交互。因为我们对这些问题使用的语言并没有那么多的选择，所以在这里讨论 TypeScript 是无关紧要的。

## 编程

## 架构与复杂性控制

对于某些问题，这个挑战不是关于处理更多请求的扩展，而是根据代码库的大小进行扩展。企业公司有复杂的现实问题需要解决。在这些公司中，最大的工程挑战通常是：

- 能够逻辑地（通过域）将整块的各个部分分成更小的应用程序。然后，物理上（通过有界上下文的微服务）将它们分开，以便可以分配团队来维护它们

- 处理这些应用程序之间的集成和同步

- 对域概念进行建模并实际解决域的问题

- 创建由开发人员和领域专家共享的无处不在（包罗万象）的语言

- 不会迷失在大量编写的代码中，并且在不破坏现有代码的情况下无法添加新功能

我基本上描述了 Domain Driven Design 解决的问题类型。对于这些类型的项目，您甚至不会考虑不使用像 TypeScript 这样的严格类型的语言。

## 强/弱类型语言

对于设计到复杂领域建模的问题，如果您不选择 TypeScript 而是选择 JavaScript，则需要一些额外的努力才能成功。您不仅需要更加熟悉 vanilla JavaScript 中的对象建模功能，而且还必须知道如何利用面向对象编程的 4 个原则（封装，抽象，继承和多态）。

这可能很难做到。JavaScript 自然不具备接口和抽象类的概念。使用 vanilla JavaScript 无法轻松实现 SOLID 设计原则中的“接口隔离”。单独使用 JavaScript 也需要一定程度的纪律作为开发人员才能保持代码清洁，而且一旦代码库足够大，这一点至关重要。您还需要确保您的团队在如何在 JavaScript 中实现通用设计模式方面拥有相同的学科，经验和知识水平。如果没有，你需要引导他们。

在像这样的领域驱动项目中，使用严格类型语言的强大好处不是表达可以做什么，而是更多关于使用封装和信息隐藏来通过限制实际允许的域对象来减少错误的表面区域。代码大小通常与复杂域问题相关联，其中大型代码库意味着复杂的域，但情况并非总是如此。当项目的代码量达到一定大小时，跟踪存在的所有内容变得更加困难，并且更容易最终重新实现已编码的内容。

复制是精心设计和稳定的软件的敌人。当新开发人员开始在已经很大的代码库上编码时，这一点尤为明显。Visual Studio Code 的自动完成和 Intellisense 有助于浏览大型项目。它适用于 TypeScript，但它在 JavaScript 方面有限。对于我知道将保持简单和小型的项目，或者如果我知道它最终将被丢弃，我将不太愿意推荐 TypeScript 作为必需品。

## 生产级别软件与 Demo

生产软件是您关心的代码，或者如果它不起作用您将遇到麻烦的代码。这也是你为其编写测试的代码。一般的经验法则是，如果您关心代码，则需要对其进行单元测试。如果您不在乎，请不要进行测试。

宠物项目是不言自明的。做你喜欢的事。您没有专业承诺维护任何标准的工艺。

## 性能与高可用

## 研发效能

# About

![default](https://i.postimg.cc/y1QXgJ6f/image.png)

## Copyright | 版权

![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg) ![](https://parg.co/bDm)

笔者所有文章遵循 [知识共享 署名-非商业性使用-禁止演绎 4.0 国际许可协议](https://creativecommons.org/licenses/by-nc-nd/4.0/deed.zh)，欢迎转载，尊重版权。如果觉得本系列对你有所帮助，欢迎给我家布丁买点狗粮(支付宝扫码)~

![](https://i.postimg.cc/y1QXgJ6f/image.png?raw=true)

## Home & More | 延伸阅读

![技术视野](https://s2.ax1x.com/2019/12/03/QQJLvt.png)

您可以通过以下导航来在 Gitbook 中阅读笔者的系列文章，涵盖了技术资料归纳、编程语言与理论、Web 与大前端、服务端开发与基础架构、云计算与大数据、数据科学与人工智能、产品设计等多个领域：

- 知识体系：《[Awesome Lists | CS 资料集锦](https://ng-tech.icu/Awesome-Lists)》、《[Awesome CheatSheets | 速学速查手册](https://ng-tech.icu/Awesome-CheatSheets)》、《[Awesome Interviews | 求职面试必备](https://ng-tech.icu/Awesome-Interviews)》、《[Awesome RoadMaps | 程序员进阶指南](https://ng-tech.icu/Awesome-RoadMaps)》、《[Awesome MindMaps | 知识脉络思维脑图](https://ng-tech.icu/Awesome-MindMaps)》、《[Awesome-CS-Books | 开源书籍（.pdf）汇总](https://github.com/wx-chevalier/Awesome-CS-Books)》

- 编程语言：《[编程语言理论](https://ng-tech.icu/ProgrammingLanguage-Series/#/)》、《[Java 实战](https://ng-tech.icu/Java-Series)》、《[JavaScript 实战](https://ng-tech.icu/JavaScript-Series)》、《[Go 实战](https://ng-tech.icu/Go-Series)》、《[Python 实战](https://ng-tech.icu/ProgrammingLanguage-Series/#/)》、《[Rust 实战](https://ng-tech.icu/ProgrammingLanguage-Series/#/)》
- 软件工程、模式与架构：《[编程范式与设计模式](https://ng-tech.icu/SoftwareEngineering-Series/)》、《[数据结构与算法](https://ng-tech.icu/SoftwareEngineering-Series/)》、《[软件架构设计](https://ng-tech.icu/SoftwareEngineering-Series/)》、《[整洁与重构](https://ng-tech.icu/SoftwareEngineering-Series/)》、《[研发方式与工具](https://ng-tech.icu/SoftwareEngineering-Series/)》

* Web 与大前端：《[现代 Web 全栈开发与工程架构](https://ng-tech.icu/Web-Series/)》、《[数据可视化](https://ng-tech.icu/Frontend-Series/)》、《[iOS](https://ng-tech.icu/Frontend-Series/)》、《[Android](https://ng-tech.icu/Frontend-Series/)》、《[混合开发与跨端应用](https://ng-tech.icu/Web-Series/)》、《[Node.js 全栈开发](https://ng-tech.icu/Node-Series/)》

* 服务端开发实践与工程架构：《[服务端基础](https://ng-tech.icu/Backend-Series/#/)》、《[微服务与云原生](https://ng-tech.icu/Backend-Series/#/)》、《[测试与高可用保障](https://ng-tech.icu/Backend-Series/#/)》、《[DevOps](https://ng-tech.icu/Backend-Series/#/)》、《[Spring](https://github.com/wx-chevalier/Spring-Series)》、《[信息安全与渗透测试](https://ng-tech.icu/Backend-Series/#/)》

* 分布式基础架构：《[分布式系统](https://ng-tech.icu/DistributedSystem-Series/#/)》、《[分布式计算](https://ng-tech.icu/DistributedSystem-Series/#/)》、《[数据库](https://github.com/wx-chevalier/Database-Series)》、《[网络](https://ng-tech.icu/DistributedSystem-Series/#/)》、《[虚拟化与云计算](https://github.com/wx-chevalier/Cloud-Series)》、《[Linux 与操作系统](https://github.com/wx-chevalier/Linux-Series)》

* 数据科学，人工智能与深度学习：《[数理统计](https://ng-tech.icu/AI-Series/#/)》、《[数据分析](https://ng-tech.icu/AI-Series/#/)》、《[机器学习](https://ng-tech.icu/AI-Series/#/)》、《[深度学习](https://ng-tech.icu/AI-Series/#/)》、《[自然语言处理](https://ng-tech.icu/AI-Series/#/)》、《[工具与工程化](https://ng-tech.icu/AI-Series/#/)》、《[行业应用](https://ng-tech.icu/AI-Series/#/)》

* 产品设计与用户体验：《[产品设计](https://ng-tech.icu/Product-Series/#/)》、《[交互体验](https://ng-tech.icu/Product-Series/#/)》、《[项目管理](https://ng-tech.icu/Product-Series/#/)》

* 行业应用：《[行业迷思](https://github.com/wx-chevalier/Business-Series)》、《[功能域](https://github.com/wx-chevalier/Business-Series)》、《[电子商务](https://github.com/wx-chevalier/Business-Series)》、《[智能制造](https://github.com/wx-chevalier/Business-Series)》

此外，你还可前往 [xCompass](https://ng-tech.icu/) 交互式地检索、查找需要的文章/链接/书籍/课程；或者也可以关注微信公众号：**某熊的技术之路**以获取最新资讯。
