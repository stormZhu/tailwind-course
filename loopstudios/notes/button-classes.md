# Button 类名详解

## 源代码

```html
<button
  class="hidden px-10 py-2 my-0 font-bold tracking-widest uppercase border-2 border-black font-alata hover:bg-black hover:text-white md:block"
>
  See All
</button>
```

## 类名解析

| 类名               | 作用            | 数值          |
| ------------------ | --------------- | ------------- |
| `hidden`           | 小屏幕隐藏      | -             |
| `px-10`            | 左右内边距      | 2.5rem (40px) |
| `py-2`             | 上下内边距      | 0.5rem (8px)  |
| `my-0`             | 上下外边距      | 0             |
| `font-bold`        | 字体加粗        | 700           |
| `tracking-widest`  | **字间距最宽**  | 0.1em         |
| `uppercase`        | 文字大写        | -             |
| `border-2`         | 边框宽度        | 2px           |
| `border-black`     | 边框颜色        | 黑色 #000     |
| `font-alata`       | 使用 Alata 字体 | -             |
| `hover:bg-black`   | 悬停背景黑色    | -             |
| `hover:text-white` | 悬停文字白色    | -             |
| `md:block`         | 大屏幕显示      | -             |

## tracking-widest 详解

`tracking` = **字间距**（letter-spacing）

### 完整对照表

| 类名               | 字间距    |
| ------------------ | --------- |
| `tracking-tighter` | -0.05em   |
| `tracking-tight`   | -0.025em  |
| `tracking-normal`  | 0 (默认)  |
| `tracking-wide`    | 0.025em   |
| `tracking-wider`   | 0.05em    |
| `tracking-widest`  | **0.1em** |

### 视觉效果对比

```
Without tracking:    SEEE ALL
With tracking-widest: S  E  E  E     A  L  L
```

### 使用场景

`tracking-widest` 常用于：

- 按钮文字
- 导航菜单
- 大标题
- 品牌标识

目的是营造**现代感**、**高级感**或**间距感**。
