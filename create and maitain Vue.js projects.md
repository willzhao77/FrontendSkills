# 建立和维护大型 Vue.js 项目的 10 个最佳实践

Yujiaao [高级前端进阶](javascript:void(0);) *Yesterday*

这是我在使用大型代码库进行 Vue 项目时开发的最佳实践。这些技巧将帮助您开发更有效的代码，更易于维护和共享。

今年的自由职业生涯中，我有机会从事一些大型Vue应用程序的工作。我所谈论的项目有超过12个Vuex 存储，大量组件（有时数百个）和许多视图（页面）。实际上，这对我来说是非常有意义的经历，因为我发现了许多有趣的模式来使代码可扩展。我还必须修复一些导致著名的意大利面条代码难题的错误做法。🍝

因此，今天，我将与您分享10个最佳实践，如果您要处理大量的代码库，我建议您遵循这些最佳实践。

## 1.使用插槽（slot）使组件更易于理解并且功能更强大

我最近写了一篇文章，介绍有关Vue.js中的插槽您需要了解的一些重要事项。它着重说明插槽如何使您的组件更可重用且更易于维护，以及为什么要使用它们。

🧐但是，这与大型Vue.js项目有什么关系？一图胜千言，所以我将为您画一张图片，这是我第一次后悔不使用它们。

有一天，我只需要创建一个弹出窗口。乍一看，没有什么真正复杂的，只是包括标题，描述和一些按钮。所以我要做的就是把所有东西都当作属性。最后，我用了三个属性来定制组件，当人们单击按钮时会发出一个事件。十分简单！😅

但是，随着项目的不断发展，团队要求我们在其中显示许多其他新内容：表单字段，不同的按钮（取决于显示在哪个页面上），卡片，页脚和列表。我发现，如果我继续使用属性来使这个组件不断扩展，似乎也可以。但是上帝，😩我错了！该组件很快变得太复杂了，以至于无法理解，因为它包含了无数的子组件，使用了太多的属性并发出了大量事件。🌋我经历了一种可怕的情况，当您在某处进行更改时，它最终以某种方式破坏了另一页上的其他内容。我搞了个科学怪人的怪物，而不是一个可维护的组件！🤖

但是，如果我从一开始就依赖插槽，情况可能会更好。最后，我重构了所有东西以提供这个小组件。易于维护，更快地理解并且可扩展性更高！

```
<template>
  <div class="c-base-popup">
    <div v-if="$slots.header" class="c-base-popup__header">
      <slot name="header">
    </div>
    <div v-if="$slots.subheader" class="c-base-popup__subheader">
      <slot name="subheader">
    </div>
    <div class="c-base-popup__body">
      <h1>{{ title }}</h1>
      <p v-if="description">{{ description }}</p>
    </div>
    <div v-if="$slots.actions" class="c-base-popup__actions">
      <slot name="actions">
    </div>
    <div v-if="$slots.footer" class="c-base-popup__footer">
      <slot name="footer">
    </div>
  </div>
</template>
<script> export default {
  props: {
    description: {
      type: String,
      default: null
    },
    title: {
      type: String,
      required: true
    }
  }
} </script> 
```

我的观点是，根据经验，由知道何时使用插槽的开发人员构建的项目确实对其未来的可维护性有很大的影响。这样就可以减少发出事件的次数，使代码更易于理解，并且可以在内部显示所需的任何组件时提供更大的灵活性。

> ⚠️作为一个经验法则，请记住，当最终在子组件的父组件中复制子组件的属性时，应该从这一点开始使用插槽。

## 2.正确组织您的 Vuex 存储

通常，新的 Vue.js 开发人员开始学习 Vuex，因为他们偶然发现了以下两个问题：

- 他们要么需要从树结构中实际上相距太远的另一个组件访问给定组件的数据，要么
- 他们需要数据在组件销毁后继续存在。

那是他们创建第一个 Vuex 存储，了解模块并开始在应用程序中进行组织的时候。💡

问题是创建模块时没有单一模式可以遵循。但是，👆🏼我强烈建议您考虑如何组织它们。据我了解，大多数开发人员都喜欢按功能组织它们。例如：

- 验证码
- 博客
- 收件箱
- 设定

就我而言，我发现根据它们从API提取的数据模型来组织它们时更容易理解。例如：

- 用户数
- 队伍
- 留言内容
- 小部件
- 文章

您选择哪一个取决于您。唯一要记住的是，从长远来看，组织良好的 Vuex 存储将使团队更具生产力。这也将使新来者更容易在加入您的团队时就将您的想法围绕您的代码库。

## 3.使用操作（Vuex Actions）进行 API 调用和提交数据

我的大多数API调用（如果不是全部）都在我的 Vuex 操作（vuex actions）中进行。您可能想知道：为什么这里调用更好？🤨

仅仅因为它们中的大多数都提取了我需要在存储（vuex store）中提交的数据。此外，它们提供了我真正喜欢的封装性和可重用性。我这样做还有其他一些原因：

- 如果我需要在两个不同的地方（例如博客和首页）获取文章的首页，则可以使用正确的参数调用适当的调度程序。数据将被提取，提交和返回，除了调度程序调用外，没有重复的代码。
- 如果我需要创建一些逻辑来避免在提取第一页时提取它，则可以在一个地方进行。除了减少服务器上的负载之外，我还有信心它可以在任何地方使用。
- 我可以在这些操作(vuex actions)中跟踪我的大多数 Mixpanel 事件，从而使分析代码库真正易于维护。我确实有一些应用程序，其中所有 Mixpanel 调用都是在操作中单独进行的。当我不必了解跟踪什么不跟踪什么以及何时发送时，😂这种方式工作会给我带来有多大的快乐。

> 译注：Mixpanel 是一家数据跟踪和分析公司，允许开发者跟踪各种用户行为，比如用户浏览的页面数，iPhone 应用分析，Facebook 应用互动情况，以及 Email 分析。类似Firebase一样的埋点分析工具。

## 4.使用 mapState，mapGetters，mapMutations 和 mapAction 简化代码库

当您只需要访问state/getter或在组件内部调用action/mutation时，通常无需创建多个计算属性或方法。使用`mapState`，`mapGetters`，`mapMutations`和`mapActions`可以帮助你缩短你的代码，通过分组来化繁为简，从你存储里模块一个地方就能掌握全局。

```
// NPM
import { mapState, mapGetters, mapActions, mapMutations } from "vuex";
export default {
  computed: {
    // Accessing root properties
    ...mapState("my_module", ["property"]),
    // Accessing getters
    ...mapGetters("my_module", ["property"]),
    // Accessing non-root properties
    ...mapState("my_module", {
      property: state => state.object.nested.property
    })
  },
  methods: {
    // Accessing actions
    ...mapActions("my_module", ["myAction"]),
    // Accessing mutations
    ...mapMutations("my_module", ["myMutation"])
  }
}; 
```

Vuex官方文档中提供了您在这些便捷帮助器上所需的所有信息。🤩

## 5.使用 API 工厂

我通常喜欢创建一个`this.$api`可以在任何地方调用以获取API端点的助手。在项目的根目录下，我有一个`api`包含所有类的文件夹（请参阅下面的其中一个）。

```
api
├── auth.js
├── notifications.js
└── teams.js 
```

每个节点都将其类别的所有端点分组。这是我在 Nuxt 应用程序中使用插件初始化此模式的方式（这与标准 Vue 应用程序中的过程非常相似）。

```
// PROJECT: API
import Auth from "@/api/auth";
import Teams from "@/api/teams";
import Notifications from "@/api/notifications";
export default (context, inject) => {
  if (process.client) {
    const token = localStorage.getItem("token");
    // Set token when defined
    if (token) {
      context.$axios.setToken(token, "Bearer");
    }
  }
  // Initialize API repositories
  const repositories = {
    auth: Auth(context.$axios),
    teams: Teams(context.$axios),
    notifications: Notifications(context.$axios)
  };
  inject("api", repositories);
}; 
```

的JavaScript

```
export default $axios => ({
  forgotPassword(email) {
    return $axios.$post("/auth/password/forgot", { email });
  },
  login(email, password) {
    return $axios.$post("/auth/login", { email, password });
  },
  logout() {
    return $axios.$get("/auth/logout");
  },
  register(payload) {
    return $axios.$post("/auth/register", payload);
  }
}); 
```

的JavaScript

现在，我可以简单地在我的组件或 Vuex 操作中调用它们，如下所示：

```
export default {
  methods: {
    onSubmit() {
      try {
        this.$api.auth.login(this.email, this.password);
      } catch (error) {
        console.error(error);
      }
    }
  }
}; 
```

的JavaScript

## 6.使用 $config 访问您的环境变量（在模板中特别有用）

您的项目可能在某些文件中定义了一些全局配置变量：

```
config
├── development.json
└── production.json 
```

我喜欢通过`this.$config`助手快速访问它们，尤其是当我在模板中时。与往常一样，扩展Vue对象非常容易：

```
// NPM
import Vue from "vue";
// PROJECT: COMMONS
import development from "@/config/development.json";
import production from "@/config/production.json";
if (process.env.NODE_ENV === "production") {
  Vue.prototype.$config = Object.freeze(production);
} else {
  Vue.prototype.$config = Object.freeze(development);
} 
```

## 7.遵循一个约定来写提交注释

随着项目的发展，您将需要定期浏览组件的提交历史记录。如果您的团队没有遵循相同的约定来书写他们的提交说明，那么将很难理解每个团队成员的行为。

我总是使用并推荐Angular commit消息准则。在我从事的每个项目中，我都会遵循它，在许多情况下，其他团队成员也会很快发现遵循它也更好。

遵循这些准则会导致更具可读性的消息，从而在查看项目历史记录时更易于跟踪提交。简而言之，这是它的工作方式：

```
git commit -am "<type>(<scope>): <subject>"
# Here are some samples
git commit -am "docs(changelog): update changelog to beta.5"
git commit -am "fix(release): need to depend on latest rxjs and zone.js" 
```

看看他们的README文件以了解更多约定。

## 8.始终在生产项目时冻结软件包的版本

我知道...所有软件包都应遵循语义版本控制规则。但实际情况是，其中一些并非如此。😅

为避免因您的一个依赖项在半夜醒来破坏了整个项目，锁定所有软件包的版本会使您的早晨工作压力减轻。😇

它的意思很简单：避免使用以`^`开头的版本：

```
{
  "name": "my project",
  "version": "1.0.0",
  "private": true,
  "dependencies": {
    "axios": "0.19.0",
    "imagemin-mozjpeg": "8.0.0",
    "imagemin-pngquant": "8.0.0",
    "imagemin-svgo": "7.0.0",
    "nuxt": "2.8.1",
  },
  "devDependencies": {
    "autoprefixer": "9.6.1",
    "babel-eslint": "10.0.2",
    "eslint": "6.1.0",
    "eslint-friendly-formatter": "4.0.1",
    "eslint-loader": "2.2.1",
    "eslint-plugin-vue": "5.2.3"
  }
} 
```

## 9.显示大量数据时使用 Vue 虚拟滚动条

当您需要在给定页面中显示很多行或需要循环访问大量数据时，您可能已经注意到该页面的呈现速度很快。要解决此问题，可以使用vue-virtual-scoller。

```
npm install vue-virtual-scroller 
```

它将仅渲染列表中的可见项，并重用组件和dom元素，以使其尽可能高效。它真的很容易使用，顺滑得很！✨

```
<template>
  <RecycleScroller
    class="scroller"
    :items="list"
    :item-size="32"
    key-field="id"
    v-slot="{ item }"
  >
    <div class="user">
      {{ item.name }}
    </div>
  </RecycleScroller>
</template> 
```

的HTML

## 10.跟踪第三方程序包的大小

当很多人在同一个项目中工作时，如果没有人关注它们，那么已安装软件包的数量会迅速增加，令人难以置信。为了避免您的应用程序变慢（尤其是在移动网络变慢的情况下），我在Visual Studio Code中使用了导入费用包。这样，我可以从编辑器中直接看到导入的模块库有多大，并且可以查看导入的模块库过大时出了什么问题。

例如，在最近的项目中，导入了整个 lodash 库（压缩后大约24kB）。问题在于，项目里仅仅使用cloneDeep 一个方法。通过在**导入费用包**中识别此问题后，我们通过以下方式解决了该问题：

```
npm remove lodash
npm install lodash.clonedeep 
```

然后可以在需要的地方导入clonedeep函数：

```
import cloneDeep from "lodash.clonedeep"; 
```

的JavaScript

> 为了进一步优化，您还可以使用Webpack Bundle Analyzer软件包通过交互式可缩放树状图来可视化Webpack输出文件的大小。

------

处理大型Vue代码库时，您还有其他最佳实践吗？请在下面的评论中告诉我，或者在Twitter @RifkiNada上与我联系。🤠



来自：https://segmentfault.com/a/1190000040712187

译自：https://www.telerik.com/blogs/all-you-need-to-know-about-slots-in-vuejs