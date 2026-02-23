# Tailwind CSS 配置笔记

## 文件：`tailwind.config.js`

### 自定义字体族配置（第 11-14 行）

```js
fontFamily: {
  sans: ['Josefin Sans', 'sans-serif'],
  alata: ['Alata'],
},
```

#### 解释

**1. `sans` 配置**
```js
sans: ['Josefin Sans', 'sans-serif'],
```
- 这里**覆盖**了 Tailwind 默认的 `font-sans` 字体族
- 优先使用 `Josefin Sans` 字体
- 如果该字体不可用，会回退到系统默认的 `sans-serif` 字体
- 使用方式：`class="font-sans"`

**2. `alata` 配置**
```js
alata: ['Alata'],
```
- 创建了一个**新的自定义字体族**，命名为 `alata`
- 使用 `Alata` 字体
- 使用方式：`class="font-alata"`

#### 实际使用示例

```html
<!-- 使用 Josefin Sans 字体 -->
<h1 class="font-sans">这是 Josefin Sans 字体</h1>

<!-- 使用 Alata 字体 -->
<p class="font-alata">这是 Alata 字体</p>
```

#### 注意事项

要使这些字体生效，你还需要在 CSS 或 HTML 中引入这些 Google Fonts（或其他字体源），例如：

```html
<link href="https://fonts.googleapis.com/css2?family=Alata&family=Josefin+Sans&display=swap" rel="stylesheet">
```

或者在 CSS 文件中：
```css
@import url('https://fonts.googleapis.com/css2?family=Alata&family=Josefin+Sans&display=swap');
```
