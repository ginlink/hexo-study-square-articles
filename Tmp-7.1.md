---
title: Tmp-7.1
---

思想

- 改比写快很多



# 1 数组排序

```ts
function tSort(data) {
    return data.sort((a, b) => a.num - b.num)
}

let data = [{ name: 'aaa', num: 2 }, { name: 'bbb', num: 1 }]
console.log('[]:', tSort(data))
```

# 2 内置组件component的用法

异步组件

```vue
<template>
  <div class="dashboard-container">
    <component :is="currentRole" />
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import adminDashboard from './admin'
import editorDashboard from './editor'

export default {
  name: 'Dashboard',
  components: { adminDashboard, editorDashboard },
  data() {
    return {
      currentRole: 'adminDashboard'
    }
  },
  computed: {
    ...mapGetters([
      'roles'
    ])
  },
  created() {
    if (!this.roles.includes('admin')) {
      this.currentRole = 'editorDashboard'
    }
  }
}
</script>
```

# 3 mac的一些技巧

### 3.1 给MAC添加 `ll`命令

1.编辑.bash_profile文件，添加别名

```bash
vim .bash_profile
alias ll='ls -alF'
```

2.新加内容生效

```bash
source .bash_profile
```

[1] [Mac终端添加ll命令](https://blog.csdn.net/BabyFish13/article/details/101106987) 

### 3.2 mac 在当前目录打开终端

https://jingyan.baidu.com/article/9989c746e8bb10f648ecfe91.html

### 3.3 mac中删除单词

- 第一种：按 delete 键，实现 Windows 键盘上退格键的功能，也就是删除光标之前的一个字符（默认）；

- 第二种：按 fn+delete 键，删除光标之后的一个字符；

- 第三种：**按 option+delete 键，删除光标之前的一个单词（英文有效）**；【常用】

- 第四种：按 command+delete 键，删除光标之前整行内容；

- 第五种：选中文件后按 command+delete，删除掉该文件。			

# 4 预渲染

预渲染：

基于prerender-spa-plugin的Vue.js预渲染实践.https://juejin.cn/post/6844904198723600391

有一个demo项目

> 注意，预渲染是根据路由来渲染的

> 待处理

[1] [vue-prerender-seo](https://github.com/mxin-d/vue-prerender-seo) 

# 4 css居中

### 4.1 块级元素居中

只说特殊的，垂直居中，方案有：1flex  2flex+margin【推荐】，水平居中都知道用margin

```css
.father {
    display: flex;
    /* 重点  必须设置为flex */
    min-height: 100vh;
    background: pink;
}

.son {
    margin: auto;
    /* 儿子用margin即可 */
    background: red;
}
```

联想：**为什么块级元素不能直接 `margin: auto 0;`来实现垂直居中呢？**

猜测和margin折叠有关，用 `display:flex;`之后子元素都是隔离的BFC，所以可以被margin撑起来

### 4.2 行内元素居中

垂直：1vertical-align  2height+line-height

水平：text-align

# 5 React学习

##### 5.1 什么情况下用state？

通过问自己以下三个问题，你可以逐个检查相应数据是否属于 state：

1. 该数据是否是由父组件通过 props 传递而来的？如果是，那它应该不是 state。
2. 该数据是否随时间的推移而保持不变？如果是，那它应该也不是 state。
3. 你能否根据其他 state 或 props 计算出该数据的值？如果是，那它也不是 state。

##### 5.2 状态提升

案例：温度转换器

# 6 React与Typescript

[1] 手册.https://typescript.bootcss.com/tutorials/react.html

# 7 input的间隙用padding，而不要用 `text-indent`

否则输入文字过多，会这样

![image-20210712113351432](/Users/jiangjin/Library/Application Support/typora-user-images/image-20210712113351432.png)

# 7 Css.Grid

> 一定要做示例，勿眼高手低，常复习

思想：grid布局分为容器属性和项目属性

容器控制容器排列位置，还可以控制项目家的大小，在家中排列位置，还可以指定项目跨度

而项目可以指定自己的跨度，只占一个容器，还是夸容器占领多个容器

> 注意，容器是容器，项目是项目，元素是元素  它们都有各自的控制方法

[1] grid-template-areas.https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-template-areas

[2] CSS Grid 网格布局教程.http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html【重点|易懂】

> 不要一味的追求外国文档，并不是都能看得懂的，国内有些大神的文章，写得很不错

# 8 favicon.ico

可以直接将png文件改为.ico即可

# 9 蓝湖无论选择哪个画质压缩，结果都是一样的

# 10 导航栏激活切换图片案例

![image-20210713232740038](https://gitee.com/nahaohao/pic-upload/raw/master/img/image-20210713232740038.png)

首先，在vue中是如何做的？


​	在data中用currentIndex记录，动态src（索引与current索引比较），在点击事件中切换current索引即可

原理：在切换current索引之后，vue会刷新视图，之后会比较各个动态src

其次，在react中应该如何做？

​	思想相同，在state中用一个量记录标志，动态src，在点击事件中更华安标志并更新state即可

[1] grid-template-areas.https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-template-areas

# 10 移动端适配

```sh
yarn add customize-cra postcss-px-to-viewport -D
```

```sh
yarn add postcss-px-to-viewport --dev
```

```sh
yarn add react-app-rewire-postcss react-app-rewired --dev
```

```sh
yarn remove react-app-rewired --dev
```

[1] create-react-app+react-app-rewired搭建viewport解决方案.https://segmentfault.com/a/1190000016780204

# 11401bWiFi密码

```sh
@t4QsyvAdv3FMk.
```

# 12 React相关内容

- 字体压缩插件

  font-spider

  引入字体文件，在v2（convert）项目的fonts文件夹内

- React需要掌握的hooks

  ```sh
  useMemo
  useEffect
  useState
  ```

# 13 语雀地址

https://www.yuque.com/docs/share/e7e51921-a972-45bc-8b81-0ab3086e634b?# 《Defi相关》

# 14 mac项目，windows拉取之后，eslint会报 `Delete CR`

~~解决方法两步，1将vscode设置搜索 `eol`设置末尾换行为 `\n`  2删除项目  3重新拉取项目，再用vscode打开~~

原因：`git`拉取代码的时候会转化为crlf（默认），可以通过以下方法更改

```csharp
# 提交时转换为LF，检出时转换为CRLF
git config --global core.autocrlf true

# 提交时转换为LF，检出时不转换
git config --global core.autocrlf input

# 提交检出均不转换
git config --global core.autocrlf false
```

# 15 windows平台启动不了项目

原因：

解决：用ubuntu启动

```sh
cd /mnt/d/nh_temp/04.demo-square/017.react-nomal/05.spweb/spweb
```

# 16 viewport适配移动端

```sh
yarn add -D react-app-rewired customize-cra postcss-px-to-viewport
```

`pakeage.json`

```json
"start": "react-app-rewired start",
"build": "react-app-rewired build",
"test": "react-app-rewired test",
"eject": "react-scripts eject"
```

`config-overrides.js`

```js
// eslint-disable-next-line @typescript-eslint/no-var-requires
const { override, overrideDevServer, addPostcssPlugins } = require('customize-cra')

const devServerConfig = () => (config) => {
  return {
    ...config,
    // 服务开启gzip
    compress: true,
  }
}
module.exports = {
  webpack: override(
    addPostcssPlugins([
      // eslint-disable-next-line @typescript-eslint/no-var-requires
      require('postcss-px-to-viewport')({
        viewportWidth: 375,
        unitPrecision: 3,
        viewportUnit: 'vw',
        selectorBlackList: ['.ignore', '.hairlines'],
        minPixelValue: 1,
        mediaQuery: false,
      }),
    ])
  ),
  devServer: overrideDevServer(devServerConfig()),
}
```

react适配关键字：`adaptive layouts with styled-component`

```javascript
export function px2vw(pixels, pixelTotal = 750) {
  return `${pixels / pixelTotal * 100}vw`;
};
```

[1] Creating responsive and adaptive layouts with React and Styled-Components.https://dev.to/carloscne/creating-responsive-and-adaptive-layouts-with-react-and-styled-components-1ghi

# 17 react中的移动端适配

首先react中无法使用postcss的插件，也就是无法使用postcss-px-to-viewport

### 17.1 rem适配

```tsx
function r(pxValue: any) {
  const ratio = 37.5 // 根据项目配置比例的方式自行设定
  pxValue = parseInt(pxValue)

  return (pxValue / ratio).toFixed(3) + 'rem'
}

export const PageWraper = styled.div`
  margin: ${r('50px')} auto 0;

  ${({ theme }) => theme.mediaWidth.upToMedium`
    margin: unset;
    width: 100%;
  `};
`
```

### 17.2 vh适配

适配函数

```tsx
function px2vw(pixels: string | number | TemplateStringsArray, pixelTotal = 375) {
  if (pixels instanceof Array) {
    // 从模板中拿去值
    pixels = pixels[0]
  }
  
  const num = parseInt(pixels as string)
  return `${((num / pixelTotal) * 100).toFixed(3)}vw`
  // 结果保留三位小数
}
```

使用

```tsx
const Container = styled.div`
  display: flex;
  margin: ${px2vw(30)} ${px2vw(18)} ${px2vw(30)} ${px2vw(28)};
  padding-bottom: ${px2vw(18)};
  align-items: center;
`;
```

> 注意：但在自己封装的媒体查询中会出错，原因未知

```tsx
${({ theme }) => theme.mediaWidth.upToMedium`
  width: ${px2vw(200)};
  height: ${px2vw(100)};
	// 样式出错

  background: url(${bgMiniH5}) no-repeat;
  background-size: 100% 100%;
  font-size: 100px;
`};
```

解决方案：用纯媒体查询

```tsx
@media (max-width: 700px){
  width: ${px2vw`345`};
  height: ${px2vw`100`};
}
```

### 17.3 适配新方案

基于[5] 

```tsx
function r(pxValue) {
  const ratio = 20; // 根据项目配置比例的方式自行设定

  // 针对template literals
  if (Array.isArray(pxValue)) {
    pxValue = pxValue[0];
  }

  pxValue = parseInt(pxValue);

  return pxValue / ratio + 'rem';
}

// 把字符串样式里面的px单位换算成rem的
// 支持多行匹配
function transformPxToRem(style) {
  // 避免处理了函数等情况
  if (typeof style !== 'string') {
    return style;
  }

  return style.replace(/\d+px/gm, matched => {
    return r(matched);
  });
}

// 实现在把样式传递给styled之前，预先用transformPxToRem处理
function t(strings, ...interpolations) {
  let styles = css(strings, ...interpolations); // css是styled-components的一个helper
  styles = styles.map(transformPxToRem);

  // 模拟raw的调用
  return [[""], styles]
};
```

> 拿到设备尺寸之后，有一个上下限，在上下限中进行转换  否则不转换
>
> 待完善

[1] styled-components中文文档.https://github.com/hengg/styled-components-docs-zh

[2] styled-components官网.https://github.com/styled-components/styled-components

[3] styled-xxxW3chool文档.https://www.w3cschool.cn/styledcomponents/styledcomponents-z8v638ja.html

[4] 移动端页面适配.https://www.jianshu.com/p/7139c05c7971【从rem到vw】

[5] 在styled-components的样式声明中做px到rem的自动转换.https://www.shuizhongyueming.com/2017/11/29/%E5%9C%A8styled-components%E7%9A%84%E6%A0%B7%E5%BC%8F%E5%A3%B0%E6%98%8E%E4%B8%AD%E5%81%9Apx%E5%88%B0rem%E7%9A%84%E8%87%AA%E5%8A%A8%E8%BD%AC%E6%8D%A2/【研究styled-comxxx的适配方案】

[6] Web移动端最强适配方案总结，没想到这么好用！.https://segmentfault.com/a/1190000038159934【比较全】

# 18 React中的Hooks

hooks主要用来：1模拟声明周期函数  2复用UI和逻辑  3性能优化

几个常用的hooks：1useState  2useEffect  3useMemo  4useRef

> useMemo和useEffect有什么区别？

最主要的区别就是在useMemo中不要操作DOM，在useEffect中操作DOM

因为useMemo是在渲染期间进行的，而useEffect是在渲染后执行的



[1] useMemo和useEffect有什么区别？.https://www.jianshu.com/p/94ace269414d

# 19 在cmd中快速打开资源管理器

```sh
start .
```

联想：vscode快速打开

```sh
code .
```

# 20 拖拽元素

首先，拖拽流程为：拖拽元素分为**拖动元素**和**放置元素**，拖动元素被拖起来之后，放到放置元素中去，这就是拖拽流程

> 拖拽的几个事件

一共有7个事件，拖动有3个，放置有4个

拖动：dragstart、drag、dragend，也就是开始、拖过程、拖动结束三个事件

放置：dragenter、dragover、dragleave和drop，也就是被拖动元素碰到放置元素、从放置元素经过、从放置元素离开、最终鼠标放开留在放置元素上的四个事件

> 练习1：拖拽元素

先看效果吧：

![image-20210717232434538](https://gitee.com/nahaohao/pic-upload/raw/master/img/image-20210717232434538.png)

```html
<!doctype html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    * {
      margin: 0;
    }

    .box {
      display: grid;
      /* grid真得好用，推荐阮一峰的教程，MDN可以当做手册看
                http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html
                */
      width: 200px;

      grid-template-columns: 1fr 1fr;
    }

    .box1 {
      width: 100%;
      height: 100px;
      border: 1px solid green;
    }

    .box2 {
      width: 100%;
      height: 100px;
      border: 1px solid lightcoral;
    }

    .el1 {
      width: 50px;
      height: 50px;
      border: 1px solid red;
    }

    .el2 {
      width: 50px;
      height: 50px;
      border: 1px solid green;
    }
  </style>
</head>

<body>

  <div class="box">
    <div id="box1" class="box2">
    </div>
    <div id="box2" class="box2">
    </div>
  </div>

  <div id="el" class="el">
    <div id="el1" class="el1" draggable="true">1
      <!-- 注意让元素支持拖拽，默认不支持 -->
    </div>
    <div id="el2" class="el2" draggable="true">2
    </div>
  </div>


  <script>
    window.onload = function () {

      const box1 = document.getElementById('box1')
      const box2 = document.getElementById('box2')
      const el = document.getElementById('el')
      const el1 = document.getElementById('el1')
      const el2 = document.getElementById('el2')

      el1.father = el
      el2.father = el
      // 记录它们各自的父亲

      let currentDraggingElement = null
      // 记录当前被拖动的元素，因为我发现拖动事件中获取不到放入的元素，呜呜呜

      el1.addEventListener('dragstart', function (e) {
        currentDraggingElement = this
      }, false)
      el2.addEventListener('dragstart', function (e) {
        currentDraggingElement = this
      }, false)
      // 给元素设置开始拖动事件，并重置当前被拖动的元素


      // 下面就是给盒子设置一些事件
      box1.addEventListener('drop', function (e) {
        // 当元素放入的时候
        if (!currentDraggingElement) return

        currentDraggingElement.father.removeChild(currentDraggingElement)
        this.appendChild(currentDraggingElement)

        currentDraggingElement.father = this
        // 重置元素的父亲
      })
      draggable(box1)
      // 这两个事件主要去除默认事件，让盒子支持放置元素，默认不支持

      box2.addEventListener('drop', function (e) {
        if (!currentDraggingElement) return

        currentDraggingElement.father.removeChild(currentDraggingElement)
        this.appendChild(currentDraggingElement)

        currentDraggingElement.father = this
      })
      draggable(box2)

    }

    function draggable(el) {
      el.addEventListener('dragenter', function (e) {
        e.preventDefault()
      })
      el.addEventListener('dragover', function (e) {
        e.preventDefault()
      })
    }
  </script>
</body>

</html>
```

> 练习2：拖拽结合事件委托

上面练习我们可以看出有一个弊端，如果子元素过多，那么要给所以子元素设置事件，这样会产生大量内存消耗，所以这里用事件委托来优化

这样发现，只需要6个事件即可，而拖动子元素可以定义无限个

```html
<!doctype html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    * {
      margin: 0;
    }

    .box {
      display: grid;
      /* grid真得好用，推荐阮一峰的教程，MDN可以当做手册看
                http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html
                */
      width: 200px;

      grid-template-columns: 1fr 1fr;
    }

    .box1 {
      width: 100%;
      height: 100px;
      border: 1px solid green;
    }

    .box2 {
      width: 100%;
      height: 100px;
      border: 1px solid lightcoral;
    }

    .el1 {
      width: 50px;
      height: 50px;
      border: 1px solid red;
    }

    .el2 {
      width: 50px;
      height: 50px;
      border: 1px solid green;
    }

    .el3 {
      width: 50px;
      height: 50px;
      border: 1px solid pink;
    }
  </style>
</head>

<body>

  <div id="box" class="box">
    <div id="box1" class="box2">
    </div>
    <div id="box2" class="box2">
    </div>
  </div>

  <div id="el" class="el">
    <div id="el1" class="el1" draggable="true">1
      <!-- 注意让元素支持拖拽，默认不支持 -->
    </div>
    <div id="el2" class="el2" draggable="true">2
    </div>
    <div id="el3" class="el3" draggable="true">3
    </div>
    <!-- 下面可以继续添加子元素 -->
  </div>


  <script>
    window.onload = function () {

      const box = document.getElementById('box')
      const box1 = document.getElementById('box1')
      const box2 = document.getElementById('box2')
      const el = document.getElementById('el')
      const el1 = document.getElementById('el1')
      const el2 = document.getElementById('el2')
      const el3 = document.getElementById('el3')
      // 遍历子元素操作比较好，但这里就不写了

      el1.father = el
      el2.father = el
      el3.father = el
      // 记录它们各自的父亲

      let currentDraggingElement = null
      // 中间量

      // 给子元素的父亲们设置拖拽委托事件【只要是子元素可能待的地方都要设置拖拽事件】
      el.addEventListener('dragstart', function (e) {
        console.log('[el委托]:', e)
        currentDraggingElement = e.target
      })

      box1.addEventListener('dragstart', function (e) {
        console.log('[box1委托]:', e)
        currentDraggingElement = e.target
      })
      box2.addEventListener('dragstart', function (e) {
        console.log('[box2委托]:', e)
        currentDraggingElement = e.target
      })

      // 给容器的父亲设置放置事件
      box.addEventListener('drop', function (e) {
        const that = e.target

        console.log('[]:', typeof (that))
        that.father && alert('[Wraning]: 子元素身上不允许放置元素!')
        if (!currentDraggingElement || that.father) return
        // 【注意】判断元素是否为el子元素，如果是，不能进行放置元素 否则会出错

        currentDraggingElement.father.removeChild(currentDraggingElement)
        that.appendChild(currentDraggingElement)

        currentDraggingElement.father = that
        // 重置元素的父亲
      })
      draggable(box)
      // 让盒子接受拖拽元素

    }

    function draggable(el) {
      el.addEventListener('dragenter', function (e) {
        // e.target.preventDefault()
        // 报错，preventDefault是事件的方法，不是元素的方法

        e.preventDefault()
        // 【注意】在委托事件中，只要父亲可以接受拖拽元素即可
      })
      el.addEventListener('dragover', function (e) {
        // e.target.preventDefault()
        e.preventDefault()
      })
    }
  </script>
</body>

</html>
```



> react中封装的拖拽

第一个：[react-draggable-list](https://github.com/StreakYC/react-draggable-list)

![image-20210717234320752](https://gitee.com/nahaohao/pic-upload/raw/master/img/image-20210717234320752.png)

第二个：[react-draggable](https://github.com/react-grid-layout/react-draggable)

![image-20210717234425122](https://gitee.com/nahaohao/pic-upload/raw/master/img/image-20210717234425122.png)

> vue的拖拽

第一个：[Vue.Draggable](https://github.com/SortableJS/Vue.Draggable)

![image-20210717234532734](https://gitee.com/nahaohao/pic-upload/raw/master/img/image-20210717234532734.png)

一些链接：

- vue封装的拖拽.https://github.com/SortableJS/Vue.Draggable
- react封装的拖拽.https://github.com/react-grid-layout/react-draggable
- CSS Grid 网格布局教程.http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html

# 21 利用gitee搭建博客

目的：

原理：

方法：

> 一些问题

- 如何配置个人域名？

  首先在gitpage设置中绑定域名，后将 `cname`解析到自己的博客地址即可，例如：

  ```sh
  ginlink.github.io/hexo-study-square
  ```

- 配置个人域名之后，`CNAME`文件应该放哪里？

  hexo中，在 `source`目录下的文件不会被删除，所以可以放入 `CNAME`文件 构建后会将这些文件放入 `public`目录中

- 为什么部署到GitHub之后样式变了？

  一般发生在自定义域名中，因为自定义

  > 待解决

参考文档：

在Gitee搭建属于自己的博客.https://blog.csdn.net/qq_46036214/article/details/110137239
