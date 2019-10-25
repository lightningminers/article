> 原文地址: https://blog.usejournal.com/vue-js-gsap-animations-26fc6b1c3c5a
>
> 原文作者: Daily Fire
>
> 翻译作者: [hanxiansen](https://github.com/hanxiansen)
>
> 中文标题：通过GASP让vue实现动态效果

单页应用及支持它们的前端框架提供了一个很好的机会，可以为程序设计提供令人惊叹的交互层，本文，我们将了解 vue.js 及如何集成 GASP 动画库来添加令人惊叹的动画效果。
![](https://miro.medium.com/max/2400/1*CdW_uGBqT9McjEmoaW3hEw.png)
Vue.js 是一个功能强大且易掌握的 JS 框架，在 Vue CLI 的帮助下，我们能够快速构建具有所有最新 Webpack 功能的应用程序，而无需花费时间来配置 webpack，只需安装 Vue CLI，在重大上输入:`create <project-name>`，您就可以发车了。

GASP是一个JavaScript动画库，它支持快速开发高性能的 Web 动画。GASP 使我们能够轻松轻松快速的将动画串在一起，来创造一个高内聚的流畅动画序列。

在构建新的 Daily Fire 主页时，我为了演示产品如何工作而使用了大量动画，但是通过 GASP的方式（不是 GIF 或视频），我可以为动画添加交互层使它们更具吸引力。如你所见，将 GASP 与 vue相结合是简单且强大的，

让我们看看如何使用 GASP 与 VUE 实现简单的时间轴，我们将在本文使用 .vue 文件，这些文件由 webpack 的 vue-loader加载使用，通过Vue CLI创建的项目将会自动
### 基础

让我们先编写一些标记，以便了解我们将制作的动画

```vue
<template>
  <div ref="box" class="box"></div>
</template>

<style>
.box {
  height: 60px;
  width: 60px;
  background: red;
}
</style>
```

我们将一个红色 box 绘制到DOM中，注意 div 标签上的`ref` 标记，当我们在引入GASP 后通过该属性可以引用该元素。VUE 通过组件的`$refs`属性使通过 ref 标记的元素可以使用。

现在引入 GASP

```vue
<template>
  <div ref="box" class="box"></div>
</template>

<script>
import { TimelineLite } from 'gsap'

export default {
  mounted() {
    const { box } = this.$refs
    const timeline = new TimelineLite()

    timeline.to(box, 1, { x: 200, rotation: 90 })
  }
}
</script>

<style>
/* styles emitted */
</style>
```

首先，我们从 GASP 中引入`TimelineLite`，然后，当组件挂载后，我们通过`$refs`获取到对 box 元素的引用。然后我们初始化 GASP 的时间线实例来播放动画。

Timeline 实例暴露出一个`to`方法，我们传递三个参数给该方法：

- 参数1：要设置动画效果的元素
- 参数2：动画运行的秒数
- 参数3：描述动画行为的对象

下面链接展示了一小段代码展示的运行效果：

https://codepen.io/smlparry/pen/rZdbEw

很简单，有木有！接下来让我们用 GASP 的 EasePack 赋予这个小动画更多的生命。使用 `ease`缓动特效是一种简单的方案，它将使你的动画特效不再那么僵硬，更加友好。当然，如果你没有将你的动画放进队列中，你将不能充分利用好 GASP 的时间线，让我们在动画的运行中途将其由红框过渡为绿框。

```vue
<template>
  <div ref="box" class="box"></div>
</template>

<script>
import { TimelineLite, Back } from 'gsap'

export default {
  mounted() {
    const { box } = this.$refs
    const timeline = new TimelineLite()

    timeline.to(box, 1, {
      x: 200,
      rotation: 90,
      ease: Back.easeInOut, // Specify an ease
    })
    timeline.to(box, 0.5, {
      background: 'green'
    },
    '-=0.5' // Run the animation 0.5s early
    )
  }
}
</script>

<style>
/* styles emitted */
</style>
```

注意第21行的额外参数，在上面的代码中它将告诉 GASP 运行一个相对于前一个动画的动画，使用`+=`指定完成后的时间，使用`-=` 指定完成前的时间。

结果在链接中：https://codepen.io/smlparry/pen/mGxYWN

有了这个简单的改动，我们的动画更加生动了！

通过这些原则的基础了解，我们可以开始构建更复杂、更吸引人的动画。正如我们将在下一个例子中所看到的。

### 在基础上更进一步

让我们创建一个动画(该动画曾在[Daily Fire首页](https://daily-fire.com/?ref=medium)中使用 )，这个友好的小泡泡:

![](https://miro.medium.com/max/411/1*eJ3KNfut8uNzE3i3N5oiCQ.gif)

让我们从标签标记开始：

```vue
<template>
<div class="bubble-wrapper">
  <div ref="bubble" class="bubble">
    <img class="bubble-image"
         src="./assets/img/slack-white.svg" />
  </div>
  <div ref="bubblePulse" class="bubble-pulse"></div>
</div>
</template>

<style>
.bubble-wrapper {
  position: relative;
}

.bubble {
  position: relative;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid white;
  background: #272727;
  border-radius: 50%;
  height: 100px;
  width: 100px;
}

.bubble-pulse {
  position: absolute;
  z-index: 1;
  height: 120px;
  width: 120px;
  top: 50%;
  left: 50%;
  margin-top: -60px;
  margin-left: -60px;
  background: #272727;
  border-radius: 50%;
  opacity: 0;
  transform: scale(0);
}

.bubble-image {
  height: 50%;
}
</style>
```

我们现在有这个一个元素

![](https://miro.medium.com/max/794/1*cuOEeHUXmh4F7QX613vKFw.png)

让我们赋予它一些生命：

```vue
<template>
<!-- HTML emitted -->
</template>

<script>
import { TimelineLite, Back, Elastic, Expo } from "gsap"

export default {
  mounted() {
    const { bubble, bubblePulse } = this.$refs
    const timeline = new TimelineLite()

    timeline.to(bubble, 0.4, {
      scale: 0.8,
      rotation: 16,
      ease: Back.easeOut.config(1.7),
    })
    timeline.to(
      bubblePulse,
      0.5,
      {
        scale: 0.9,
        opacity: 1,
      },
     '-=0.6'
    )

    this.timeline.to(bubble, 1.2, {
      scale: 1,
      rotation: '-=16',
      ease: Elastic.easeOut.config(2.5, 0.5),
    })
    this.timeline.to(
      bubblePulse,
      1.1,
      {
        scale: 3,
        opacity: 0,
        ease: Expo.easeOut,
      },
      '-=1.2'
    )
  }
}
</script>

<style>
/* CSS Emitted */
</style>
```

虽然一开始看起来很麻烦，但只要花点时间来理解它的实际运行情况，其实它只是一些按顺序排列的 CSS transform属性。这里有几个自定义的 ease 特效，GASP 提供了一个有趣的小工具，你可以根据喜好自由配置：[https://greensock.com/ease-visualizer](https://greensock.com/ease-visualizer)

现在效果如下：

![](https://miro.medium.com/max/397/1*CZOFIGoXeWPda8RWNAb6sg.gif)

### 循环

上面的gif动画其实具有欺骗性，gif图片是循环的，但代码不是，让我们看看如何使用 GASP 和 VUE 循环播放动画。GASP 的 `TimelineLite`提供了一个`onComplete`属性，通过该属性我们可以分配一个函数，利用该函数我们可以循环动画，另外，我们将通过`data`使`timeline`在组件的其余部分也可使用。

```vue
<template>
<!-- HTML Emitted -->
</template>

<script>

// ...

export default {
  data() {
    return {
      timeline: null,
    }
  },

  mounted() {
    // ...

    this.timeline = new TimelineLite({
      onComplete: () => this.timeline.restart()
    })

    // ...

  }
}
</script>

<style>
/* CSS Emitted */
</style>
```

现在 GASP 将会在动画完成后又重新开始，效果如下：https://codepen.io/smlparry/pen/dqmEax

### 添加交互性

现在，我们的动画效果已经写得差不多了，可以考虑添加一些交互特效。在本例中，我们将添加一个按钮，来随机更新气泡中的logo。

为了能做到该需求，我们必须做以下几件事：

- 将图片的引用源地址绑定到 VUE 的data中
- 创建要使用的图片数组
- 创建随机获取logo的方法
- 添加按钮来更改logo

```vue
<template>
  <div class="bubble-wrapper">
    <div ref="bubble" class="bubble">
      <img class="bubble-image"
           :src="currentLogo" />
    </div>
    <div ref="bubblePulse" class="bubble-pulse"></div>
  </div>

  <button @click="randomiseLogo">Random Logo</button>
</template>

<script>

// ...

export default {
  data() {
    return {
      timeline: null,
      logos: ['path/to/logo-1.svg', 'path/to/logo-2.svg', 'path/to/logo-3.svg'],
      currentLogo: '',
    }
  },

  methods: {
    randomiseLogo() {
      const logosToSample = this.logos.filter(logo => logo !== this.currentLogo)
      this.currentLogo = logosToSample[Math.floor(Math.random() * logosToSample.length)]
    }
  },

  mounted() {
    this.randomiseLogo()

    // ...

  }
}
</script>

<style>
/* CSS Emitted */
</style>
```

有了上面的代码，现在我们可以通过一个按钮来更新制作运行动画的元素，通史也可以对其进行动画制作，效果：https://codepen.io/smlparry/pen/RYMXPx

我使用了与上面动画非常类似的技术来实现主页的动画效果，我从数组中选择列表的下一个元素，然后将其append到列表中。
