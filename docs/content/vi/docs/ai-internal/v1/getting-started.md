---
title: Bắt đầu
weight: 1
tags:
  - Docs
  - Guide
next: /guide
prev: /docs
---

## Bắt đầu nhanh từ template

{{< icon "github" >}}&nbsp;[your-username/your-project-starter-template](https://github.com/your-username/your-project-starter-template)

Bạn có thể bắt đầu nhanh bằng cách dùng repository template ở trên.

<img src="https://docs.github.com/assets/cb-77734/mw-1440/images/help/repository/use-this-template-button.webp" width="500" alt="Trang repository GitHub hiển thị nút Use this template">

Chúng tôi cung cấp [workflow GitHub Actions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow) giúp build và triển khai site lên GitHub Pages tự động, host miễn phí.
Để xem thêm tùy chọn, tham khảo [Triển khai site](../guide/site-deploy).

[🌐 Demo ↗](https://your-username.github.io/your-project-starter-template/)

## Bắt đầu với dự án mới

Có hai cách chính để thêm giao diện (theme) vào dự án Hugo:

1. **Hugo Modules (Khuyến nghị)**: Cách đơn giản và được khuyến nghị. [Hugo modules](https://gohugo.io/hugo-modules/) cho phép bạn kéo theme trực tiếp từ nguồn trực tuyến. Theme được tải và quản lý tự động bởi Hugo.

2. **Git Submodule**: Hoặc thêm theme dưới dạng [Git Submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules). Theme được Git tải và lưu trong thư mục `themes` của dự án.

### Cài theme qua Hugo module

#### Yêu cầu

Trước khi bắt đầu, cần cài đặt các phần mềm sau:

- [Hugo (bản extended)](https://gohugo.io/installation/)
- [Git](https://git-scm.com/)
- [Go](https://go.dev/)

#### Các bước

{{% steps %}}

### Khởi tạo site Hugo mới

```shell
hugo new site my-site --format=yaml
```

### Cấu hình theme qua module

```shell
# khởi tạo hugo module
cd my-site
hugo mod init github.com/username/my-site

# thêm theme
hugo mod get github.com/your-username/your-project
```

Thêm vào `hugo.yaml` để dùng theme:

```yaml
module:
  imports:
    - path: github.com/your-username/your-project
```

### Tạo các trang nội dung đầu tiên

Tạo trang nội dung cho trang chủ và trang tài liệu:

```shell
hugo new content/_index.md
hugo new content/docs/_index.md
```

### Xem thử site trên máy

```shell
hugo server --buildDrafts --disableFastRender
```

Xem site tại `http://localhost:1313/`.

{{% /steps %}}


{{% details title="Cách cập nhật theme?" %}}

Để cập nhật tất cả Hugo modules trong dự án lên phiên bản mới nhất:

```shell
hugo mod get -u
```

Để cập nhật theme lên [phiên bản phát hành mới nhất](https://github.com/your-username/your-project/releases):

```shell
hugo mod get -u github.com/your-username/your-project
```

Nếu muốn thử thay đổi mới nhất trước khi phát hành, cập nhật module trực tiếp lên nhánh development (⚠️ có thể chứa thay đổi chưa ổn định):

```shell
hugo mod get -u github.com/your-username/your-project@main
```

Xem [Hugo Modules](https://gohugo.io/hugo-modules/use-modules/#update-all-modules) để biết thêm.

{{% /details %}}


### Cài theme qua Git submodule

#### Yêu cầu

Trước khi bắt đầu, cần cài đặt:

- [Hugo (bản extended)](https://gohugo.io/installation/)
- [Git](https://git-scm.com/)

#### Các bước

{{% steps %}}

### Khởi tạo site Hugo mới

```shell
hugo new site my-site --format=yaml
```

### Thêm theme dưới dạng Git submodule

Chuyển vào thư mục site và khởi tạo repository Git:

```shell
cd my-site
git init
```

Sau đó thêm theme làm Git submodule:

```shell
git submodule add https://github.com/your-username/your-project.git themes/hextra
```

Thêm vào `hugo.yaml` để dùng theme:

```yaml
theme: hextra
```

### Tạo các trang nội dung đầu tiên

Tạo trang nội dung cho trang chủ và trang tài liệu:

```shell
hugo new content/_index.md
hugo new content/docs/_index.md
```

### Xem thử site trên máy

```shell
hugo server --buildDrafts --disableFastRender
```

Site xem thử có tại `http://localhost:1313/`.

{{% /steps %}}


Khi dùng [CI/CD](https://en.wikipedia.org/wiki/CI/CD) để triển khai site Hugo, cần chạy lệnh sau trước khi chạy `hugo`:

```shell
git submodule update --init
```

Nếu không chạy lệnh này, thư mục theme sẽ không có file theme và quá trình build sẽ lỗi.


{{% details title="Cách cập nhật theme?" %}}

Để cập nhật tất cả submodule trong repository lên commit mới nhất:

```shell
git submodule update --remote
```

Để chỉ cập nhật theme lên commit mới nhất:

```shell
git submodule update --remote themes/hextra
```

Xem [Git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) để biết thêm.

{{% /details %}}

## Tiếp theo

Khám phá các mục sau để thêm nội dung:

{{< cards >}}
  {{< card link="../guide/organize-files" title="Tổ chức file" icon="document-duplicate" >}}
  {{< card link="../guide/configuration" title="Cấu hình" icon="adjustments" >}}
  {{< card link="../guide/markdown" title="Markdown" icon="markdown" >}}
{{< /cards >}}
