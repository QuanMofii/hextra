---
title: ホーム用ショートコード
linkTitle: ホーム
sidebar:
  exclude: true
next: /guide/site-deploy
---

これらのショートコードの主な使用場所は、レイアウト `theme-home` 内です。

## `theme/feature-card`

機能カードを表示するためのショートコード。

### Usage

```
{{</* theme/feature-card title="Title" subtitle="Subtitle" */>}}
```

### Options

| Parameter    | Description |
|--------------|-------------|
| `title`      | カードのタイトル。   |
| `subtitle`   | カードのサブタイトル。 |
| `class`      | カードのクラス。    |
| `image`      | カードの画像。     |
| `imageClass` | 画像のクラス。     |
| `style`      | カードのスタイル。   |
| `icon`       | カードのアイコン。   |
| `link`       | カードのリンク。    |

## `theme/feature-grid`

機能グリッドを表示するためのショートコード。

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
| `cols`    | 列の数。        |
| `style`   | グリッドのスタイル。  |

## `theme/hero-badge`

リンク付きのバッジをレンダリングするためのショートコード。

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
| `link`    | バッジのリンク。    |
| `class`   | バッジのクラス。    |
| `style`   | バッジのスタイル。   |

## `theme/hero-button`

リンク付きのボタンをレンダリングするためのショートコード。

### Usage

```
{{</* theme/hero-button text="Get Started" link="/docs" */>}}
```

### Options

| Parameter | Description |
|-----------|-------------|
| `link`    | ボタンのリンク。    |
| `text`    | ボタンのテキスト。   |
| `style`   | ボタンのスタイル。   |

## `theme/hero-container`

左側に画像があるシンプルなヒーロー コンテナー。

### Usage

```
{{</* theme/hero-container image="images/logo.svg"  imageTitle="title" */>}}
    Content
{{</* /theme/hero-container */>}}
```

### Options

| Parameter     | Description                       |
|---------------|-----------------------------------|
| `class`       | コンテナのクラス。                         |
| `cols`        | 列数（デフォルト：`2`）。                    |
| `image`       | コンテナの画像。                          |
| `imageCard`   | 画像をカードとして表示するかどうか（デフォルト：`false`）。 |
| `imageClass`  | 画像のクラス。                           |
| `imageLink`   | 画像のリンク。                           |
| `imageStyle`  | 画像のスタイル。                          |
| `imageTitle`  | 画像のタイトル。                          |
| `imageWidth`  | 画像の幅（デフォルト：`350`）。                |
| `imageHeight` | 画像の高さ（デフォルト：`350`）。               |
| `style`       | コンテナのスタイル。                        |

## `theme/hero-headline`

ヒーローの見出しを表示するためのショートコード。

### Usage

```
{{</* theme/hero-headline */>}}
  Build modern websites&nbsp;<br class="hx:sm:block hx:hidden" />with Markdown and Hugo
{{</* /theme/hero-headline */>}}
```

### Options

| Parameter | Description |
|-----------|-------------|
| `style`   | 見出しのスタイル。   |

## `theme/hero-section`

見出しとオプションのスタイルを備えたシンプルなヒーロー セクション。

### Usage

```
{{</* theme/hero-section heading="h3" */>}}Title{{</* /theme/hero-section */>}}>
```

### Options

| Parameter | Description          |
|-----------|----------------------|
| `heading` | 見出しレベル（デフォルト: `h2`）。 |
| `style`   | 見出しのスタイル。            |
| `content` | 見出しの内容。              |

## `theme/hero-subtitle`

ヒーローのサブタイトルを表示するためのショートコード。

### Usage

```
{{</* theme/hero-subtitle */>}}
  Fast, batteries-included Hugo theme&nbsp;<br class="hx:sm:block hx:hidden" />for creating beautiful static websites
{{</* /theme/hero-subtitle */>}}
```

### Options

| Parameter | Description |
|-----------|-------------|
| `style`   | 字幕のスタイル。    |
