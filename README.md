# fe-eight-part-essay

八股总结（或者如何在面试中应对问题）。
永远要保持自己的思考能力。
放轻松，不会就直说，或者说自己的理解。

## 自我介绍
> 面试官您好，我是来自xx大学的xxx，我已学习和从事前端有一年半多，曾在xx公司的xx部门以及现在在xx公司的xx部门中实习。
> 我目前正在维护两个上线的项目，一个是仿北京大学 Botzone 平台，一个是基于Web Canvas 2D的简单游戏。并且也正在设计与开发一个游戏相关的 npm 包。
> 我所熟悉的前端技术栈是 React 以及 Vue ，以及它们的相关生态，并且也正在了解新兴框架如 Svelte 和 SolidJS。
> 在工程化方面我比较常用 Vite、Rollup、基于 Webpack 的二次封装 CLI。
> 在前端之外也兼顾过后端开发，使用过 Java 的 SpringBoot、Python 的 Flask、Django、JS 的 express、nest。也常用中间件 MySQL 以及 Docker。
> 我的个人介绍至此，感谢贵司给我这个面试机会。

## 实习收获？（回答比较笼统，但确实是真实想法）
> - 接触真实的工业环境，一个项目的建立、开发、测试、上线、维护过程，可以说是真正接触到团队协作的软件工程
> - 职场中的交流氛围，一定程度上影响到个人性格，有事直说、不懂就问是效率最高的交流
> - 重要的是，可以在公司内部查阅其他人的技术文档、技术方案，我个人比较喜欢查阅代码设计的技术方案，虽然记不得看了谁的看了多少，但是也潜影默化影响了我的开发思想，以及设计能力
> - 业务理解，有什么沉淀？观察业务觉得能干什么，为什么服务？技术理解，好处是？性能优化？编程范式？

## 为什么学前端？
> - 对交互比较敏感，而前端是最直接的交互设计的工作，喜欢通过优化性能提升体验，也喜欢设计不同的交互模式去给用户带来不同的体验
> - 不只是用户体验，我也对开发体验很敏感，对于前端开发是有非常繁荣的生态去设计工具链
> - 产品的优秀必然包括使用体验上面的优秀

## 怎么学习前端？
> - 主要还是通过跟从事前端的业内人士交流，他们身处各个企业，做不同的业务，对于前端技术上有什么思考，可以通过交谈得到收获
> - 通过我的个人项目去驱动学习，因为有需求，我就会有目的性地去学可以完成这些需求的技术。当开发完成之后仍可以思考有什么技术可以更好地优化这个项目，再去学习，这样就形成了一个良性循环
> - 只要进入了前端行业，社区输出的文章总会出现在眼前，这样也就更方便地接触并且了解到新的前端技术、方案等等（虽然都因为目前个人业务暂时用不上，只是看一眼，去吸收印象比较深刻的点）

## HTTP 和 HTTPS 的区别？
> - 一个明文一个密文，明文有被窃取和篡改的风险
> - 在 TCP 和 HTTP 网络层之间加了一层 SSL/TLS 安全协议
> - 三次握手后 HTTPS 仍需要 SSL/TLS 握手
> - 需要向 CA 申请数字证书，证明自己可受信任

## HTTPS 的过程？
> - SSL/TLS 连接过程
>   - C -> S TLS version + C Random + support
>   - S -> C TLS version + S Random + support + CA
>   - C -> S pre-master.secret(pub_key) + CR + SR + summary
>   - S -> C secret(pre-master + CR + SR)
> - C 验证证书
>   - Content -hash-> hashed_content
>   - Content -hash-> Signature
>   - Signature -CA-> Certificated Signature
>   - Certificated Signature -no_hash-> Signature
>   - compare(hashed_content, Signature) is same
> - 交流加密
>   - content -hash-> signature
>   - signature -pri_key-> encrypted_signature
>   - content + encrypted_signature -send_to-> server
>   - encrypted_signature -pub_key-> signature
>   - content -hash-> hash_v1
>   - signature -hash-> hash_v2
>   - compare(hash_v1, hash_v2)

## flex: 0 & flex: 1
> - flex: grow shrink basis
> - flex: 0 = flex: 0 1 0% 不增只缩
> - flex: 1 = flex: 1 1 0% 同增同缩
> - flex: initial = flex: 0 1 auto 不增只缩自适应
> - flex: none = flex: 0 0 auto 不增不缩自适应
> - flex: auto = flex: 1 1 auto 同增同缩自适应

## React 和 Vue 的区别？（应该自由发挥）
> - 一个使用 JSX、一个使用模板语法，JSX 好处是相对自由，缺点是下限很低，模板语法好处是更符合声明式编程的理念，缺点是相对 JSX 不够自由，并且遵循 SFC 原则
> - 一个 MVC 一个 MVVM，MVC 强调数据不可变（页面），响应式数据更新就要重新执行一次组件渲染 Function 生成新页面这就是 MVC；MVVM 不这样考虑，认为数据是可变的，视图与数据应该是相互作用的
> - 更新的时候框架做了什么？React 自 16 之后更新数据不会 STW，而是在 Fiber 上一边更新视图一边给一阵子用户可交互的时间，用户无感知般框架的修改带来的性能问题；Vue 响应式数据本身的实现支持细粒度更细的更新，如果要引入 Fiber 代价太大提升太少
> - 一个单向diff，一个双向diff或者LIS算法优化diff
> - React 生态更好，Vue 2 到 3 因为 api 的大改动，导致 Vue2 与 3 的生态割裂
> - React 心智模型更复杂，仍需要 Hook 去增强可设计性，Vue 底层做了大量设计，因此有更加符合直觉的开发体验

## 讲讲 BFC？（感觉没啥意义、平时遇不到）
> - 块级格式化上下文
> - 独立渲染区域，BFC 之间渲染布局相互不影响
> - 触发：float、overflow、脱离文档流、根元素
> - 场景：外边距合并、清楚浮动、高度塌陷

## Fiber？
> - 背景：React 16 之前如果页面视图涉及大量数据，一触发更新就会 STW ，因为把线程交给了 JS 执行，渲染线程就长时间没有得到控制权，在用户眼里就是卡了。
> - 把 React 中的更新过程划分成一个一个小任务，然后每执行完一个小任务就把控制权归还一段时间，再获取控制权，继续更新，如此反复。
> - 要做到能够保持控制权交接的时候不丢失状态（轮到什么小任务），就使用 Fiber 维护，作为组件树，这样就能中断和恢复了。
> - 特点：使用优先级、时间切片、可中断恢复、增量渲染。

