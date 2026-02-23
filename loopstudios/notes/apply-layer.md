# @layer components 与 @apply 详解

## 源代码

```css
@layer components {
    .btn {
        @apply px-10 py-2 my-0 font-bold tracking-widest uppercase border-2 border-black font-alata hover:bg-black hover:text-white;
    }
}
```

## 解释

### @layer components

`@layer` 是 Tailwind CSS 的指令，用于将样式归类到特定的层。

| 层名 | 用途 |
|------|------|
| `base` | 基础样式（如重置样式） |
| `components` | 组件样式（如按钮、卡片） |
| `utilities` | 工具类（Tailwind 默认） |

```css
@layer components {
    .btn { ... }
}
```

效果：
- 将 `.btn` 样式放入 `components` 层
- 方便管理和覆盖

### @apply

`@apply` 用于在自定义 CSS 中**复用** Tailwind 工具类。

```css
@apply 工具类1 工具类2 ...;
```

例如：

```css
.btn {
    @apply px-10 py-2 font-bold;
}
```

等价于：

```html
<button class="px-10 py-2 font-bold">按钮</button>
```

## 工作流程

1. **定义**：`input.css` 中用 `@apply` 创建 `.btn` 组件
2. **使用**：`index.html` 中直接用 `class="btn"` 引用

```html
<!-- index.html -->
<button class="btn hidden md:block">See All</button>
```

## 好处

1. **代码复用**：多处按钮只需引用 `.btn`
2. **HTML 简洁**：不用写一长串工具类
3. **易于维护**：修改一次即可全局生效
4. **语义化**：`.btn` 比一堆工具类更易读

## 完整示例

```css
/* input.css */
@layer components {
    .btn {
        @apply px-10 py-2 my-0 font-bold tracking-widest uppercase border-2 border-black font-alata hover:bg-black hover:text-white;
    }

    .card {
        @apply bg-white rounded-lg shadow-lg p-6;
    }
}
```

```html
<!-- index.html -->
<button class="btn">See All</button>
<div class="card">内容</div>
```
