---
title: Cấu hình
weight: 2
tags:
  - Config
---

Hugo đọc cấu hình từ file `hugo.yaml` tại thư mục gốc của site Hugo.
File cấu hình là nơi bạn thiết lập mọi khía cạnh của site.
Tham khảo file cấu hình của site mẫu [`docs/hugo.yaml`](https://github.com/your-username/your-project/blob/main/docs/hugo.yaml) trên GitHub để nắm các thiết lập và best practice.

<!--more-->

## Điều hướng

### Menu

Menu góc phải được định nghĩa trong mục `menu.main` của file cấu hình:

```yaml {filename="hugo.yaml"}
menu:
  main:
    - name: Documentation
      pageRef: /docs
      weight: 1
    - name: Blog
      pageRef: /blog
      weight: 2
    - name: About
      pageRef: /about
      weight: 3
    - name: Search
      weight: 4
      params:
        type: search
    - name: GitHub
      weight: 5
      url: "https://github.com/your-username/your-project"
      params:
        icon: github
```

Có các kiểu mục menu:

1. Liên kết tới trang trong site bằng `pageRef`
   ```yaml
   - name: Tài liệu
     pageRef: /docs
   ```
2. Liên kết tới URL ngoài bằng `url`
   ```yaml
   - name: GitHub
     url: "https://github.com"
   ```
3. Thanh tìm kiếm với `type: search`
   ```yaml
   - name: Tìm kiếm
     params:
       type: search
   ```
4. Chỉ icon
   ```yaml
   - name: GitHub
     params:
       icon: github
   ```
5. Liên kết kèm icon
   ```yaml
   - name: Blog
     params:
       type: link
       icon: rss
   ```
6. Chuyển theme
   ```yaml
    - name: Chuyển theme
      params:
        type: theme-toggle
        label: true # tùy chọn, mặc định false
   ```
7. Chuyển ngôn ngữ
   ```yaml
    - name: Chuyển ngôn ngữ
      params:
        type: language-switch
        label: true # tùy chọn, mặc định false
        icon: "globe-alt" # tùy chọn, mặc định "translate"
   ```

Thứ tự mục menu có thể điều chỉnh bằng tham số `weight`.

### Menu lồng nhau

Bạn có thể tạo menu thả xuống bằng cách định nghĩa mục con. Menu con hiện khi bấm vào mục cha.

```yaml {filename="hugo.yaml"}
menu:
  main:
    - identifier: sdk
      name: SDK
    - identifier: python
      name: Python ↗
      url: https://python.org
      parent: sdk
    - identifier: go
      name: Go
      url: https://go.dev
      parent: sdk
```

Mục menu con cần có tham số `parent` với giá trị `identifier` của mục cha.

### Logo và tiêu đề

Để đổi logo mặc định, sửa `hugo.yaml` và thêm đường dẫn tới file logo trong thư mục `static`. Tùy chọn: đổi liên kết khi bấm logo và đặt width/height (pixel).

```yaml {filename="hugo.yaml"}
params:
  navbar:
    displayTitle: true
    displayLogo: true
    logo:
      path: images/logo.svg
      dark: images/logo-dark.svg
      link: /
      width: 40
      height: 20
```

### Phân trang

Để tắt điều hướng Trước/Tiếp ở cuối trang tài liệu hoặc bài blog:

```yaml {filename="hugo.yaml"}
params:
  page:
    displayPagination: false  # for docs pages
  blog:
    article:
      displayPagination: false  # for blog articles
```

## Sidebar

### Sidebar chính

Sidebar chính được tạo tự động theo cấu trúc thư mục nội dung. Xem trang [Tổ chức file](/guide/organize-files) để biết thêm.

Để loại một trang khỏi sidebar trái, đặt tham số `sidebar.exclude` trong front matter của trang:

```yaml {filename="content/guide/configuration.md"}
---
title: Cấu hình
sidebar:
  exclude: true
---
```

### Liên kết thêm

Liên kết thêm của sidebar định nghĩa trong mục `menu.sidebar` của file cấu hình:

```yaml {filename="hugo.yaml"}
menu:
  sidebar:
    - name: More
      params:
        type: separator
      weight: 1
    - name: "About"
      pageRef: "/about"
      weight: 2
    - name: "Hugo Docs ↗"
      url: "https://gohugo.io/documentation/"
      weight: 3
```

### Ẩn sidebar

Có thể ẩn sidebar bằng front matter:

```yaml {filename="content/guide/configuration.md"}
---
title: Cấu hình
sidebar:
  hide: true
---
```

Khi đó sidebar chính sẽ bị ẩn trên trang, giải phóng không gian cho nội dung chính.


## Sidebar phải

### Mục lục

Mục lục được tạo tự động từ các heading trong file nội dung. Có thể tắt bằng `toc: false` trong front matter:

```yaml {filename="content/guide/configuration.md"}
---
title: Cấu hình
toc: false
---
```

### Liên kết sửa trang

Để cấu hình liên kết sửa trang, đặt tham số `params.editURL.base` trong file cấu hình:

```yaml {filename="hugo.yaml"}
params:
  editURL:
    enable: true
    base: "https://github.com/your-username/your-repo/edit/main"
```

Liên kết sửa sẽ được tạo tự động cho từng trang dựa trên url cung cấp làm thư mục gốc. Nếu muốn đặt liên kết sửa cho một trang cụ thể, đặt tham số `editURL` trong front matter:

```yaml {filename="content/guide/configuration.md"}
---
title: Cấu hình
editURL: "https://example.com/edit/this/page"
---
```

## Chân trang

### Bản quyền

Để sửa dòng copyright hiển thị ở chân trang, tạo file `i18n/en.yaml` (hoặc `i18n/vi.yaml` cho tiếng Việt). Trong file đó khai báo nội dung copyright mới, ví dụ:

```yaml {filename="i18n/en.yaml"}
copyright: "© 2024 YOUR TEXT HERE"
```

Có thể tham khảo file mẫu [`i18n/en.yaml`](https://github.com/your-username/your-project/blob/main/i18n/en.yaml) trên repository. Bạn cũng có thể dùng định dạng Markdown trong nội dung copyright.

## Khác

### Favicon

Để tùy chỉnh [favicon](https://en.wikipedia.org/wiki/Favicon) của site, đặt file icon trong thư mục `static` để ghi đè [favicon mặc định của theme](https://github.com/your-username/your-project/tree/main/static):

{{< filetree/container >}}
  {{< filetree/folder name="static" >}}
    {{< filetree/file name="android-chrome-192x192.png" >}}
    {{< filetree/file name="android-chrome-512x512.png" >}}
    {{< filetree/file name="apple-touch-icon.png" >}}
    {{< filetree/file name="favicon-16x16.png" >}}
    {{< filetree/file name="favicon-32x32.png" >}}
    {{< filetree/file name="favicon-dark.svg" >}}
    {{< filetree/file name="favicon.ico" >}}
    {{< filetree/file name="favicon.svg" >}}
    {{< filetree/file name="site.webmanifest" >}}
  {{< /filetree/folder >}}
{{< /filetree/container >}}

#### Thiết lập cơ bản

Tối thiểu cần có `favicon.svg` trong thư mục `static`. File này sẽ dùng làm favicon mặc định của site.

Bạn có thể tạo favicon SVG thích ứng với theme hệ thống bằng CSS media query trong chính file SVG, theo [Building an Adaptive Favicon](https://web.dev/articles/building/an-adaptive-favicon).

#### Hỗ trợ chế độ tối

Để hỗ trợ dark mode tốt hơn, thêm `favicon-dark.svg` vào thư mục `static` cùng `favicon.svg`. Khi có cả hai, giao diện sẽ tự động:

- Dùng `favicon.svg` cho chế độ sáng hoặc khi không xác định được theme
- Chuyển sang `favicon-dark.svg` khi hệ thống người dùng đặt chế độ tối
- Tuân theo `prefers-color-scheme` của hệ thống để chuyển tự động

Chuyển favicon theo dark mode hoạt động trên mọi trình duyệt hiện đại, kể cả Firefox.

#### Định dạng bổ sung

`favicon.ico` thường dùng cho trình duyệt cũ; trình duyệt hiện đại hỗ trợ favicon SVG (scalable, dung lượng nhỏ). Có thể dùng [favicon.io](https://favicon.io/) hoặc [favycon](https://github.com/ruisaraiva19/favycon) để tạo thêm định dạng favicon nếu cần.

### Cấu hình theme

Dùng thiết lập `theme` để cấu hình chế độ theme mặc định và nút chuyển, cho phép người xem chuyển giữa chế độ sáng và tối.

```yaml {filename="hugo.yaml"}
params:
  theme:
    # light | dark | system
    default: system
    displayToggle: true
```

Các giá trị cho `theme.default`:

- `light` – luôn dùng chế độ sáng
- `dark` – luôn dùng chế độ tối
- `system` – đồng bộ với cài đặt hệ điều hành (mặc định)

Tham số `theme.displayToggle` cho phép hiển thị nút chuyển theme. Khi đặt `true`, người xem có thể chuyển giữa sáng và tối, ghi đè thiết lập mặc định.

### Lần sửa đổi cuối

Ngày sửa đổi cuối của trang có thể hiển thị bằng cách bật `params.displayUpdatedDate`. Để lấy ngày từ Git commit, bật thêm `enableGitInfo`.

Để tùy chỉnh định dạng ngày, đặt tham số `params.dateFormat`. Cú pháp giống [`time.Format`](https://gohugo.io/functions/time/format/) của Hugo.

Tác giả của lần sửa cuối có thể hiển thị bằng cách bật `params.displayUpdatedAuthor`. Cần đặt `enableGitInfo: true`.

```yaml {filename="hugo.yaml"}
# Parse Git commit
enableGitInfo: true

params:
  # Display the last modification date
  displayUpdatedDate: true
  dateFormat: "January 2, 2006"
  # Display the author of the last modification
  displayUpdatedAuthor: true
```

### Tags

To display page tags, set following flags in the config file:

```yaml {filename="hugo.yaml"}
params:
  blog:
    list:
      displayTags: true
  toc:
    displayTags: true
```

### Image Zoom

Image zoom is disabled by default. When enabled, clicking a Markdown image opens a zoomed view.

```yaml {filename="hugo.yaml"}
params:
  imageZoom:
    enable: true
```

To disable zoom on a specific page, add this to the page front matter:

```yaml {filename="content/guide/configuration.md"}
---
imageZoom: false
---
```

If you want to pin the Medium Zoom asset or load it from local assets:

```yaml {filename="hugo.yaml"}
params:
  imageZoom:
    enable: true
    base: "https://cdn.jsdelivr.net/npm/medium-zoom@1.1.0/dist"
    # js: "js/medium-zoom.min.js" # optional, relative to the base or local assets
```

### Page Width

The layout shell width can be customized by the `params.page.width` parameter in the config file:

```yaml {filename="hugo.yaml"}
params:
  page:
    # full (100%), wide (90rem), normal (1280px)
    width: wide
```

Available options for `params.page.width`: `full`, `wide`, `normal`.

The main reading content width remains fixed at `72rem` by default.

To customize content width, override the CSS variable in your custom stylesheet:

```css {filename="assets/css/custom.css"}
:root {
  --hextra-max-content-width: 100%;
}
```

Similarly, the width of the navbar and footer can be customized by the `params.navbar.width` and `params.footer.width` parameters.

### Page Context Menu

The page context menu provides a dropdown button that allows users to copy the page content as Markdown or view the raw Markdown source. This feature is useful for documentation sites where readers may want to share or reference the content in Markdown format.

#### Enabling the Context Menu

To enable the context menu globally, add the following to your config file:

```yaml {filename="hugo.yaml"}
params:
  page:
    contextMenu:
      enable: true
```

You also need to enable the `markdown` output format for pages:

```yaml {filename="hugo.yaml"}
outputs:
  page: [html, markdown]
  section: [html, rss, markdown]
```

#### Per-Page Control

To enable or disable the context menu for a specific page, use the `contextMenu` parameter in the front matter:

```yaml {filename="content/docs/example.md"}
---
title: Example Page
contextMenu: false
---
```

#### Custom Links

You can add custom links to the context menu dropdown. This is useful for integrating with external services. The links support the following placeholders:

- `{url}` - The page URL (URL-encoded)
- `{title}` - The page title (URL-encoded)
- `{markdown_url}` - The URL to the raw Markdown content (URL-encoded)

```yaml {filename="hugo.yaml"}
params:
  page:
    contextMenu:
      enable: true
      links:
        - name: Open in ChatGPT
          icon: chatgpt
          url: "https://chatgpt.com/?hints=search&q=I%27m+looking+at+this+documentation%3A+{url}%0AHelp+me+understand+how+to+use+it."
```

Each link can have:
- `name` - The display text for the link
- `icon` - An optional icon name (see [Icons]({{% relref "guide/shortcodes/icon" %}}))
- `url` - The URL with optional placeholders

### FlexSearch Index

Full-text search powered by [FlexSearch](https://github.com/nextapps-de/flexsearch) is enabled by default.
To customize the search index, set the `params.search.flexsearch.index` parameter in the config file:

```yaml {filename="hugo.yaml"}
params:
  # Search
  search:
    enable: true
    type: flexsearch

    flexsearch:
      # index page by: content | summary | heading | title
      index: content
```

Options for `flexsearch.index`:

- `content` - full content of the page (default)
- `summary` - summary of the page, see [Hugo Content Summaries](https://gohugo.io/content-management/summaries/) for more details
- `heading` - level 1 and level 2 headings
- `title` - only include the page title

To customize the search tokenize, set the `params.search.flexsearch.tokenize` parameter in the config file:

```yaml {filename="hugo.yaml"}
params:
  search:
    # ...
    flexsearch:
      # full | forward | reverse | strict
      tokenize: forward
```

Options for [`flexsearch.tokenize`](https://github.com/nextapps-de/flexsearch/#tokenizer-prefix-search):

- `strict` - index whole words
- `forward` - incrementally index words in forward direction
- `reverse` - incrementally index words in both directions
- `full` - index every possible combination

To exclude a page from the FlexSearch search index, set the `excludeSearch: true` in the front matter of the page:

```yaml {filename="content/guide/configuration.md"}
---
title: Configuration
excludeSearch: true
---
```

### Google Search Index

To [block Google Search](https://developers.google.com/search/docs/crawling-indexing/block-indexing) from indexing a page, set `noindex` to true in your page frontmatter:

```yaml
title: Configuration (archive version)
params:
  noindex: true
```

To exclude an entire directory, use the [`cascade`](https://gohugo.io/configuration/cascade/) key in the parent `_index.md` file.

> [!NOTE]
> To block search crawlers, you can make a [`robots.txt` template](https://gohugo.io/templates/robots/).
> However, `robots.txt` instructions do not necessarily keep a page out of Google search results.

### Analytics

The theme has support for several different analytics solutions. The theme only supports analytics in production environments. This is to ensure that you do not accidentally send analytic events when working locally. If, however, you do want to test analytics locally, you can run a production server using:

```
hugo server --environment production
```

#### Google Analytics

To enable [Google Analytics](https://marketingplatform.google.com/about/analytics/), set `services.googleAnalytics.ID` flag in `hugo.yaml`:

```yaml {filename="hugo.yaml"}
services:
  googleAnalytics:
    ID: G-MEASUREMENT_ID
```

#### Umami Analytics

To enable [Umami](https://umami.is/docs/), set `params.analytics.umami.serverURL` and `params.analytics.umami.websiteID` flag in `hugo.yaml`:

```yaml {filename="hugo.yaml"}
params:
  analytics:
    umami:
      serverURL: "https://example.com"
      websiteID: "94db1cb1-74f4-4a40-ad6c-962362670409"
      # scriptName: "script.js" # optional (default: script.js)
      # https://umami.is/docs/tracker-configuration#data-host-url
      # hostURL: "http://stats.example.org" # optional
      # https://umami.is/docs/tracker-configuration#data-auto-track
      # autoTrack: "false" # optional
      # https://umami.is/docs/tracker-configuration#data-tag
      # domains: "example.net,example.org" # optional
      # https://umami.is/docs/tracker-configuration#data-exclude-search
      # tag: "umami-eu" # optional
      # https://umami.is/docs/tracker-configuration#data-exclude-hash
      # excludeSearch: "true" # optional
      # https://umami.is/docs/tracker-configuration#data-do-not-track
      # excludeHash: "true" # optional
      # https://umami.is/docs/tracker-configuration#data-domains
      # doNotTrack: "true" # optional
```

#### Matomo Analytics

To enable [Matomo](https://matomo.org/), set `params.analytics.matomo.URL` and `params.analytics.matomo.ID` flag in `hugo.yaml`:

```yaml {filename="hugo.yaml"}
params:
  analytics:
    matomo:
      serverURL: "https://example.com"
      websiteID: "94db1cb1-74f4-4a40-ad6c-962362670409"
```

#### GoatCounter Analytics

To enable [GoatCounter](https://www.goatcounter.com/), set `params.analytics.goatCounter.code` in `hugo.yaml`
All settings available here are mirrors of the settings described in GoatCounter [settings](https://www.goatcounter.com/help/js#settings-44186)

```yaml {filename="hugo.yaml"}
params:
  analytics:
    goatCounter:
      code: "ABCDE"

      # Optional Settings
      #------------------
      # disables automatic collection of data
      # noOnload: true
      
      # disables event binding. See more here https://www.goatcounter.com/help/events
      # noEvents: true

      # allows data collection from local addresses. Use this with a production environment to test locally
      # allowLocal: true

      # Allow data collection when a page is loaded in a frame or iframe
      # allowFrame: true
```

### LLMS.txt Support

To enable [llms.txt](https://llmstxt.org/) output format for your site, which provides a structured text outline for [large language models](https://en.wikipedia.org/wiki/Large_language_model) and AI agents, add the `llms` output format to your site's `hugo.yaml`:

```diff {filename="hugo.yaml"}
outputs:
- home: [html]
+ home: [html, llms]
  page: [html]
  section: [html, rss]
```

This will generate an `llms.txt` file at your site's root containing:

- Site title and description
- Hierarchical listing of all sections and pages
- Page summaries and publication dates
- Direct links to all content

You can exclude specific pages or sections by setting `llms: false` in their front matter:

```yaml
---
title: "Internal Notes"
llms: false
---
```

The llms.txt file is automatically generated from your content structure and makes your site more accessible to AI tools and language models for context and reference.

### Open Graph

To add [Open Graph](https://ogp.me/) metadata, you can:
- add values in the front-matter params of a page
- or add values in the Hugo configuration file

As a page can have multiple `image` and `video` tags, place their values in an array.
Other Open Graph properties can have only one value.

{{< tabs >}}
{{< tab name="Page Level" >}}

```md {filename="mypage.md"}
---
title: "My Page"
params:
  images:
    - "images/image01.jpg"
  audio: "podcast02.mp3"
  videos:
    - "video01.mp4"
---

Page content.
```
{{< /tab >}}
{{< tab name="Global Level" >}}
```yaml {filename="hugo.yaml"}
params:
  images:
    - "images/image01.jpg"
  audio: "podcast02.mp3"
  videos:
    - "video01.mp4"
```
{{< /tab >}}
{{< /tabs >}}

### Banner

To add a banner to your site, add the following to your `hugo.yaml`:

```yaml
params:
  banner:
    key: 'announcement-xxx'
    message: |
      🎉 Welcome! [PROJECT_NAME](https://github.com/your-username/your-project) is a static site generator that helps you build modern websites.
```

The banner will be displayed on all pages.

The field `message` supports Markdown syntax.

If you want to use template syntax, you can define the partial in `layouts/_partials/custom/banner.html`.
In this case, the field `message` will be ignored.

### External Link Decoration

Adds an arrow icon to external links (default: false) when rendering links from Markdown.

```yaml
params:
  externalLinkDecoration: true
```
