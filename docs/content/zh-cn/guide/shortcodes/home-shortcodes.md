---
title: 首页短代码
linkTitle: 首页
sidebar:
  exclude: true
next: /guide/site-deploy
---

这些短代码的主要用途是在布局`theme-home`内。

## `theme/feature-card`

显示功能卡的短代码。

### Usage

```
{{</* theme/feature-card title="Title" subtitle="Subtitle" */>}}
```

### Options

| Parameter    | Description |
|--------------|-------------|
| `title`      | 卡片的标题。      |
| `subtitle`   | 卡片的副标题。     |
| `class`      | 卡片的类别。      |
| `image`      | 卡片的图片。      |
| `imageClass` | 图片的类别。      |
| `style`      | 卡片的样式。      |
| `icon`       | 卡片的图标。      |
| `link`       | 卡片的链接。      |

## `theme/feature-grid`

用于显示特征网格的短代码。

### Usage

```
{{</* theme/feature-grid cols="3" */>}}
  {{</* theme/feature-card title="One" */>}}
  {{</* theme/feature-card title="Two" */>}}
  {{</* theme/feature-card title="Three" */>}}
{{</* /theme/feature-grid */>}}
```

### Options

| Parameter | Description |
|-----------|-------------|
| `cols`    | 列数。         |
| `style`   | 网格的样式。      |

## `theme/hero-badge`

用于呈现带有链接的徽章的短代码。

### Usage

```
{{</* theme/hero-badge */>}}
  <div class="hx:w-2 hx:h-2 hx:rounded-full hx:bg-primary-400"></div>
  <span>Free, open source</span>
  {{</* icon name="arrow-circle-right" attributes="height=14" */>}}
{{</* /theme/hero-badge */>}}
```

### Options

| Parameter | Description |
|-----------|-------------|
| `link`    | 徽章的链接。      |
| `class`   | 徽章的类别。      |
| `style`   | 徽章的样式。      |

## `theme/hero-button`

用于呈现带有链接的按钮的短代码。

### Usage

```
{{</* theme/hero-button text="Get Started" link="/docs" */>}}
```

### Options

| Parameter | Description |
|-----------|-------------|
| `link`    | 按钮的链接。      |
| `text`    | 按钮的文本。      |
| `style`   | 按钮的样式。      |

## `theme/hero-container`

一个简单的英雄容器，左侧有一个图像。

### Usage

```
{{</* theme/hero-container image="images/logo.svg"  imageTitle="title" */>}}
    Content
{{</* /theme/hero-container */>}}
```

### Options

| Parameter     | Description              |
|---------------|--------------------------|
| `class`       | 容器的类。                    |
| `cols`        | 列数（默认值：`2`）。             |
| `image`       | 容器的图片。                   |
| `imageCard`   | 是否将图片显示为卡片（默认值：`false`）。 |
| `imageClass`  | 图片的类。                    |
| `imageLink`   | 图片的链接。                   |
| `imageStyle`  | 图片的样式。                   |
| `imageTitle`  | 图片的标题。                   |
| `imageWidth`  | 图片的宽度（默认值：`350`）。        |
| `imageHeight` | 图片的高度（默认值：`350`）。        |
| `style`       | 容器的样式。                   |

## `theme/hero-headline`

显示英雄标题的短代码。

### Usage

```
{{</* theme/hero-headline */>}}
  Build modern websites&nbsp;<br class="hx:sm:block hx:hidden" />with Markdown and Hugo
{{</* /theme/hero-headline */>}}
```

### Options

| Parameter | Description |
|-----------|-------------|
| `style`   | 标题的样式。      |

## `theme/hero-section`

带有标题和可选样式的简单英雄部分。

### Usage

```
{{</* theme/hero-section heading="h3" */>}}Title{{</* /theme/hero-section */>}}>
```

### Options

| Parameter | Description     |
|-----------|-----------------|
| `heading` | 标题级别（默认值：`h2`）。 |
| `style`   | 标题的样式。          |
| `content` | 标题的内容。          |

## `theme/hero-subtitle`

显示英雄字幕的短代码。

### Usage

```
{{</* theme/hero-subtitle */>}}
  Fast, batteries-included Hugo theme&nbsp;<br class="hx:sm:block hx:hidden" />for creating beautiful static websites
{{</* /theme/hero-subtitle */>}}
```

### Options

| Parameter | Description |
|-----------|-------------|
| `style`   | 字幕的样式。      |
