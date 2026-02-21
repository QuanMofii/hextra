---
title: شورت‌کدهای صفحه اصلی
linkTitle: صفحه اصلی
sidebar:
  exclude: true
next: /guide/site-deploy
---

الاستخدام الرئيسي لهذه الرموز المختصرة هو داخل التخطيط `theme-home`.

## `theme/feature-card`

رمز مختصر لعرض بطاقة مميزة.

### Usage

```
{{</* theme/feature-card title="Title" subtitle="Subtitle" */>}}
```

### Options

| Parameter    | Description             |
|--------------|-------------------------|
| `title`      | عنوان البطاقة.          |
| `subtitle`   | العنوان الفرعي للبطاقة. |
| `class`      | فئة البطاقة.            |
| `image`      | صورة البطاقة.           |
| `imageClass` | فئة الصورة.             |
| `style`      | نمط البطاقة.            |
| `icon`       | أيقونة البطاقة.         |
| `link`       | رابط البطاقة.           |

## `theme/feature-grid`

رمز مختصر لعرض شبكة الميزات.

### Usage

```
{{</* theme/feature-grid cols="3" */>}}
  {{</* theme/feature-card title="One" */>}}
  {{</* theme/feature-card title="Two" */>}}
  {{</* theme/feature-card title="Three" */>}}
{{</* /theme/feature-grid */>}}
```

### Options

| Parameter | Description  |
|-----------|--------------|
| `cols`    | عدد الأعمدة. |
| `style`   | نمط الشبكة.  |

## `theme/hero-badge`

رمز مختصر لعرض شارة تحتوي على رابط.

### Usage

```
{{</* theme/hero-badge */>}}
  <div class="hx:w-2 hx:h-2 hx:rounded-full hx:bg-primary-400"></div>
  <span>Free, open source</span>
  {{</* icon name="arrow-circle-right" attributes="height=14" */>}}
{{</* /theme/hero-badge */>}}
```

### Options

| Parameter | Description  |
|-----------|--------------|
| `link`    | رابط الشارة. |
| `class`   | فئة الشارة.  |
| `style`   | شكل الشارة.  |

## `theme/hero-button`

رمز مختصر لعرض زر يحتوي على رابط.

### Usage

```
{{</* theme/hero-button text="Get Started" link="/docs" */>}}
```

### Options

| Parameter | Description |
|-----------|-------------|
| `link`    | رابط الزر.  |
| `text`    | نص الزر.    |
| `style`   | شكل الزر.   |

## `theme/hero-container`

حاوية بطل بسيطة مع صورة على الجانب الأيسر.

### Usage

```
{{</* theme/hero-container image="images/logo.svg"  imageTitle="title" */>}}
    Content
{{</* /theme/hero-container */>}}
```

### Options

| Parameter     | Description                             |
|---------------|-----------------------------------------|
| `class`       | فئة الحاوية.                            |
| `cols`        | عدد الأعمدة (الافتراضي: `2`).           |
| `image`       | صورة الحاوية.                           |
| `imageCard`   | عرض الصورة كبطاقة (الافتراضي: `false`). |
| `imageClass`  | فئة الصورة.                             |
| `imageLink`   | رابط الصورة.                            |
| `imageStyle`  | شكل الصورة.                             |
| `imageTitle`  | عنوان الصورة.                           |
| `imageWidth`  | عرض الصورة (الافتراضي: `350`).          |
| `imageHeight` | ارتفاع الصورة (الافتراضي: `350`).       |
| `style`       | شكل الحاوية.                            |

## `theme/hero-headline`

رمز مختصر لعرض عنوان رئيسي.

### Usage

```
{{</* theme/hero-headline */>}}
  Build modern websites&nbsp;<br class="hx:sm:block hx:hidden" />with Markdown and Hugo
{{</* /theme/hero-headline */>}}
```

### Options

| Parameter | Description    |
|-----------|----------------|
| `style`   | أسلوب العنوان. |

## `theme/hero-section`

قسم بطل بسيط مع عنوان ونمط اختياري.

### Usage

```
{{</* theme/hero-section heading="h3" */>}}Title{{</* /theme/hero-section */>}}>
```

### Options

| Parameter | Description                    |
|-----------|--------------------------------|
| `heading` | مستوى العنوان (افتراضي: `h2`). |
| `style`   | نمط العنوان.                   |
| `content` | محتوى العنوان.                 |

## `theme/hero-subtitle`

رمز مختصر لعرض عنوان فرعي للبطل.

### Usage

```
{{</* theme/hero-subtitle */>}}
  Fast, batteries-included Hugo theme&nbsp;<br class="hx:sm:block hx:hidden" />for creating beautiful static websites
{{</* /theme/hero-subtitle */>}}
```

### Options

| Parameter | Description    |
|-----------|----------------|
| `style`   | أسلوب الترجمة. |
