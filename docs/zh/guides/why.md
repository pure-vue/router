> 为了快速实现，这个库目前的核心思路以及超过 60%（目前）的逻辑实现都参考于`React-Router`，你可以视作他是一个`React-Router`的 vue3 版本实现，至少目前来看这句话是绝对成立的。我们会优先以学习的姿态把基础逻辑进行实现，后期再结合 vue3 的生态进行优化升级。再次在这里对`React-Router`团地报以诚挚的敬意，他们在 API 设计以及代码优雅性上都保有非常高的水准！

# 为什么需要一个新的路由库

**vue3 值得一个更好的路由库**

自 vue 发布开始，vue 的生态已经发展了 5 年有余，其间从 1.0 的小试牛刀，到 2.0 正式稳定并保持高度的使用率，成为了前端届前三的框架，并可见未来多年这个形势也不会变。

vue 作为 react 的后备，并不可否认其一直在追赶 react。但是 vue 的生态在很多层面上却比 react 要差太多，从整体社区的氛围来看，会有一种使用 vue 的更多的是一些初中级的开发者，而 react 则会被认为是搭建一些更复杂并且对于规范要求更高的项目的首选。

同时生态多样性上差距也是很大的，作为作为前端应用三驾马车除框架本身之外的**路由库**和**状态管理库**，vue 也一直处于只有官方维护的 vue-router 和 vuex 能保持热度的状态，并没有优秀的第三方实现出现。

最令人难受的是，vue 官方本身也在把*容易上手，简单易用*作为自己的首要目标，SFC 方言就是最明显的，我们不难理解，在 vue 刚开始出现的时候，react 正如日中天，一个跟 react 那么像的库，没有优秀的生态，怎么竞争呢？**面向行业最广大的人群，初中级开发者，就是一个比较好的策略。**

最初期这样是可以理解的，但是在现在 vue 的受众已经很广，生态也已经发展得不错，这时候还在对于*容易上手*上下功夫就有点本末倒置了。（说实话我非常非常不喜欢`<script setup>`提案。）

在 vue 本身上如此，在 vue 官方的路由库也是如此。纯声明式的 API，对于使用场景，扩展方式都有很大的限制，唯一的优点可能就是初中级开发同学也能一眼理清的路由结构。

### composition api

另外一个在这个节点发布这个库的原因，则是 vue3 的改版。在 vue3 中新增了 composition api，一种实现和运行方式和 react hooks 天差地别，但是对于构建应用的意义却又非常接近于 hooks 的 api。这个 API 让我们抽象组件和业务逻辑的能力上获得了空前的提升，这也是实现该库的 API 形势一个重要基础。

让人惊喜的是 vue3 的虚拟 dom api 也更接近于 react，让 vue2 中形同鸡肋的 jsx 语法开发模式，在 vue3 中有了一席之地。而更纯粹的组件化 API 无疑是更适合 jsx 语法进行使用的，这是 vue2 所不具有的条件，也是我们选择不支持 vue2 的一个主要原因。

自 vue3 宣布其 composition api 开始，我们就已经开始为全面组件化的开发模式做准备。我们在 vue2 时期就抛弃了指令，并且不到万不得已，不实用`mixin`，也在团队内建立**不要使用在 vue 的 prototype 上挂载属性**这样的规范，因为我们认为这是不安全且难以维护的开发实践，我们发布过一篇[文章]()深度讨论过这个话题。所以我们在 vue2 时期就已经开始极力实践一切皆组件的开发模式，但是因为 vue2 本身的实现上的一些短板让我们很难做到所有细节。而 composition api 则拯救了我们。

### 最后

vue3 虽然努力做到了和 vue2 的兼容，但我们极力推荐大家把 vue3 当作一个新的框架来进行使用，去发觉一些更好的实践，而不是固步自封，不思进取。vue3 需要的不是使用人数的增加，而是使用高度的提升，而这，正是我们[pure]()团队正在努力达成的目标。