# Tailwind CSS Group 与 Group-Hover 详解

## 源代码示例

```html
<div class="group">
  <a href="#">About</a>
  <div class="mx-2 group-hover:border-b group-hover:border-blue-50"></div>
</div>
```

## 概念解释

### `group` 类

- 放在**父元素**上
- 作用：标记这个元素为一个"组"，使得子元素可以共享父元素的 hover 状态
- 不添加任何样式，仅作为状态标记

### `group-hover:` 前缀

- 放在**子元素**上
- 作用：当父元素被 hover 时，触发子元素的样式变化
- 语法：`group-hover:样式类`

## 工作原理

1. 给父元素添加 `group` 类
2. 给需要响应 hover 的子元素添加 `group-hover:xxx` 类
3. 当鼠标悬停在父元素（或其任何子元素）上时，子元素的样式会变化

## 本例解析

```html
<div class="group">
  <!-- 1. 标记为 group -->
  <a href="#">About</a>
  <!-- 链接文字 -->
  <div class="mx-2 group-hover:border-b group-hover:border-blue-50">
    <!-- 2. 悬停时显示下边框 -->
  </div>
</div>
```

效果：

- 鼠标移到整个 `div` 区域时
- `div` 内的 `border-b`（下边框）会显示
- 边框颜色为 `border-blue-50`（很浅的蓝色）

## 常见用法

```html
<!-- 图片遮罩效果 -->
<div class="group relative">
  <img src="..." />
  <div class="absolute inset-0 bg-black opacity-0 group-hover:opacity-50">
    <!-- 悬停时显示半透明黑色遮罩 -->
  </div>
</div>

<!-- 文字变色 -->
<div class="group">
  <span class="text-gray-600 group-hover:text-blue-500"> 悬停时变蓝色 </span>
</div>

<!-- 整体上移 -->
<div class="group">
  <div class="transition-transform group-hover:-translate-y-2">
    悬停时向上移动
  </div>
</div>
```

## 总结

| 类名               | 位置   | 作用                 |
| ------------------ | ------ | -------------------- |
| `group`            | 父元素 | 标记元素组           |
| `group-hover:xxx`  | 子元素 | 父元素 hover 时触发  |
| `group-focus:xxx`  | 子元素 | 父元素 focus 时触发  |
| `group-active:xxx` | 子元素 | 父元素 active 时触发 |

## 更多 Group 变体

Tailwind CSS 提供了丰富的 group 状态变体：

| 变体                 | 说明                           | 示例            |
| -------------------- | ------------------------------ | --------------- |
| `group-hover`        | 父元素 hover 时                | 鼠标悬停        |
| `group-focus`        | 父元素获得焦点时               | input focus     |
| `group-focus-within` | 父元素或其任意子元素获得焦点时 | 表单容器        |
| `group-active`       | 父元素激活时                   | 按钮按下        |
| `group-visited`      | 父元素被访问过（链接）         | 已访问链接      |
| `group-checked`      | 父元素被选中时                 | 单选/复选框选中 |
| `group-disabled`     | 父元素禁用时                   | 禁用状态        |
| `group-first`        | 父元素是第一个子元素时         | 第一个元素      |
| `group-last`         | 父元素是最后一个子元素时       | 最后一个元素    |
| `group-odd`          | 父元素是奇数个子元素时         | 第 1、3、5...个 |
| `group-even`         | 父元素是偶数个子元素时         | 第 2、4、6...个 |

## 必须叫 `group` 吗？

**默认情况下必须使用 `group`**。Tailwind CSS 没有直接提供修改 `group` 前缀的简单配置项。

如果你确实需要自定义名称，可以使用插件实现：

```js
// tailwind.config.js
const plugin = require("tailwindcss/plugin")

module.exports = {
  plugins: [
    plugin(function ({ addVariant }) {
      // 添加自定义变体 'parent-hover'（替代 group-hover）
      addVariant("parent-hover", ({ container }) => {
        container.walkRules((rule) => {
          rule.selector = rule.selector.replace(
            /^parent-hover:/,
            ":not(:hover) "
          )
        })
      })
    }),
  ],
}
```

但这种做法：

1. 复杂度高，容易出错
2. 需要额外配置
3. 兼容性不确定

**所以最简单的方式就是直接使用默认的 `group` 类名。**
