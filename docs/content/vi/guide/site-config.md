---
title: Cấu hình Site
linkTitle: Cấu hình Site
weight: 9
---

Hướng dẫn này giải thích cách cấu hình trang tài liệu này cho doanh nghiệp hoặc dự án của bạn. Tất cả thông tin dự án được tập trung trong một file cấu hình duy nhất, giúp việc đổi thương hiệu và triển khai cho các tổ chức khác nhau trở nên dễ dàng.

<!--more-->

## Tổng quan

Khi triển khai template tài liệu này cho một doanh nghiệp mới, bạn cần cập nhật metadata dự án như:
- Tên dự án/sản phẩm
- Mô tả và slogan
- URL repository GitHub
- Logo và tài sản thương hiệu
- Liên hệ và mạng xã hội

Tất cả cài đặt này được tập trung trong **một file**: `hugo.yaml`.

**Vị trí file cấu hình:** Trong cấu trúc repo này, file cấu hình chính là **`docs/hugo.yaml`** khi bạn chạy Hugo với `--source=docs` (ví dụ `npm run dev:theme`). Mọi đường dẫn trong hướng dẫn đều áp dụng cho file đó trừ khi có ghi chú khác.

## Cấu trúc File Cấu hình

Mở `hugo.yaml` (tức `docs/hugo.yaml`) và tìm phần `params.project`. Đây là **nguồn duy nhất** cho tất cả metadata dự án:

```yaml {filename="hugo.yaml"}
params:
  project:
    # Định danh cốt lõi
    name: "Tên Dự Án"                                 # Tên dự án/sản phẩm
    shortName: "TDA"                                  # Tên ngắn cho hiển thị gọn
    tagline: "Slogan Tuyệt Vời"                       # Slogan ngắn gọn
    
    # Mô tả
    description: "Mô tả đầy đủ về dự án cho SEO và meta tags."
    shortDescription: "Mô tả ngắn cho phần hero"
    
    # Thông tin Tổ chức/Tác giả
    author: "Tên Bạn"
    organization: "Tổ Chức Của Bạn"
    email: "lienhe@example.com"
    
    # Liên kết
    website: "https://website-cua-ban.com"
    github: "https://github.com/to-chuc/repo"
    githubEditBase: "https://github.com/to-chuc/repo/edit/main/docs/content"
    
    # Mạng xã hội (tùy chọn - để trống nếu không dùng)
    twitter: "https://twitter.com/taikhoan"
    discord: "https://discord.gg/server"
    
    # Thương hiệu
    logo: "images/logo.svg"
    logoDark: "images/logo-dark.svg"
    
    # Phiên bản
    currentVersion: "v1.0"
    
    # Giấy phép
    license: "MIT"
    licenseUrl: "https://github.com/to-chuc/repo/blob/main/LICENSE"
```

## Hướng dẫn Cấu hình Từng Bước

Làm theo các bước sau để cấu hình site cho doanh nghiệp của bạn:

{{< steps >}}

### Cập nhật Cài đặt Cơ bản

Ở đầu `hugo.yaml`, cập nhật:

```yaml {filename="hugo.yaml"}
baseURL: "https://docs.domain-cua-ban.com/"
title: "Tên Dự Án"
```

### Cập nhật Thông tin Dự án

Trong phần `params.project`, cập nhật tất cả các trường với thông tin doanh nghiệp:

| Trường | Mô tả | Ví dụ |
|--------|-------|-------|
| `name` | Tên đầy đủ dự án | "Sản Phẩm Của Tôi" |
| `shortName` | Tên viết tắt | "SPCT" |
| `tagline` | Slogan ngắn | "Xây dựng nhanh, triển khai thông minh" |
| `description` | Mô tả đầy đủ cho SEO | "Tài liệu hoàn chỉnh cho..." |
| `author` | Tên tác giả hoặc team | "DevTeam" |
| `organization` | Tên công ty/tổ chức | "Công ty ABC" |
| `github` | URL Repository | "https://github.com/abc/docs" |

### Cập nhật Tiêu đề Ngôn ngữ

Cho mỗi ngôn ngữ trong phần `languages`, cập nhật `title`:

```yaml {filename="hugo.yaml"}
languages:
  en:
    title: Your Project Name
  vi:
    title: Tên Dự Án
  ja:
    title: プロジェクト名
  zh-cn:
    title: 项目名称
  fa:
    title: نام پروژه
```

### Cập nhật Liên kết Menu

Cập nhật liên kết GitHub trong menu chính:

```yaml {filename="hugo.yaml"}
menu:
  main:
    - identifier: github
      name: GitHub
      url: "https://github.com/to-chuc/repo"
      params:
        icon: github
```

**Nhãn menu (Products, Versions, Showcase, Blog, Guide):** Các mục này được dịch qua **i18n**. Để đổi chữ hiển thị trên header/navbar, sửa các key `products`, `versions`, `showcase`, `blog`, `guide`, `more` trong từng file `i18n/*.yaml` (ví dụ `i18n/en.yaml`, `i18n/vi.yaml`).

### Cập nhật URL Chỉnh sửa

Cập nhật URL base cho tính năng "Chỉnh sửa trang này":

```yaml {filename="hugo.yaml"}
params:
  editURL:
    base: "https://github.com/to-chuc/repo/edit/main/docs/content"
```

### Thay thế Tài sản Thương hiệu

Thay thế các file trong `static/images/`:

| File | Mục đích | Kích thước khuyến nghị |
|------|----------|------------------------|
| `logo.svg` | Logo chế độ sáng | Cao: 32-40px |
| `logo-dark.svg` | Logo chế độ tối | Cao: 32-40px |
| `favicon.ico` | Favicon trình duyệt | 32x32px |

### Cấu hình Bình luận (Tùy chọn)

Nếu dùng Giscus cho bình luận, cập nhật cài đặt repository:

```yaml {filename="hugo.yaml"}
params:
  comments:
    enable: true
    type: giscus
    giscus:
      repo: to-chuc/repo
      repoId: YOUR_REPO_ID
      category: General
      categoryId: YOUR_CATEGORY_ID
```

Truy cập [giscus.app](https://giscus.app/) để tạo các giá trị này.

### Cập nhật Nội dung

Cập nhật các trang nội dung chính:
- Trang chủ: `content/{lang}/_index.md`
- Trang Giới thiệu: `content/{lang}/about/index.md`
- Cấu trúc tài liệu sản phẩm

{{< /steps >}}

## Sử dụng Thông tin Dự án trong Nội dung

Bạn có thể hiển thị động thông tin dự án trong nội dung bằng shortcodes:

### Hiển thị Giá trị Dự án

```markdown
Chào mừng đến với {{</* project "name" */>}}!

{{</* project "description" */>}}

Phiên bản hiện tại: {{</* project "currentVersion" */>}}
```

**Các trường có sẵn:**
- `name`, `shortName`, `tagline`
- `description`, `shortDescription`
- `author`, `organization`, `email`
- `website`, `github`
- `currentVersion`, `license`, `licenseUrl`
- `twitter`, `discord`

### Tạo Liên kết

```markdown
Xem {{</* project-link "github" */>}}

Truy cập {{</* project-link "website" "website chính thức" */>}}

Được cấp phép theo {{</* project-link "license" */>}}
```

## Thứ tự Rebrand Đề xuất

Làm lần lượt theo thứ tự sau để tránh bỏ sót:

1. **Cấu hình** — `hugo.yaml`: `baseURL`, `title`, `params.project.*`, `languages.*.title`, `menu.main` (GitHub), `params.editURL.base`, `theme` (nếu bạn đổi tên thư mục theme).
2. **i18n** — Trong **mọi** file trong `i18n/*.yaml` (en, vi, ja, zh-cn, fa, …): `copyright`, `poweredBy`, và các key menu (`products`, `versions`, `showcase`, …) nếu cần nhãn dịch.
3. **Thương hiệu** — Thay logo và favicon trong `static/images/`.
4. **Banner** — Cập nhật `languages.<lang>.params.banner.message` trong `hugo.yaml` cho từng ngôn ngữ (xem [Thông báo Banner theo ngôn ngữ](#thông-báo-banner-theo-ngôn-ngữ) bên dưới).
5. **Nội dung** — Trang chủ, About, và tìm/thay **PROJECT_NAME** trong toàn bộ nội dung (front matter và body).
6. **Placeholder** — Thay placeholder URL GitHub (`{author}`, `{project_name}`, `your-username`, `your-project`) trong các file liệt kê ở [Thay thế Placeholder URL GitHub](#thay-thế-placeholder-url-github).

## Danh sách Kiểm tra Cấu hình

Sử dụng danh sách này khi thiết lập cho doanh nghiệp mới:

| Mục | Vị trí | Trạng thái |
|-----|--------|------------|
| Base URL | `hugo.yaml` → `baseURL` | ☐ |
| Tiêu đề site | `hugo.yaml` → `title` | ☐ |
| Thông tin dự án | `hugo.yaml` → `params.project.*` | ☐ |
| Tiêu đề ngôn ngữ | `hugo.yaml` → `languages.*.title` | ☐ |
| Theme key (nếu đổi tên thư mục theme) | `hugo.yaml` → `theme` | ☐ |
| Link GitHub menu | `hugo.yaml` → `menu.main` | ☐ |
| URL chỉnh sửa | `hugo.yaml` → `params.editURL.base` | ☐ |
| File logo | `static/images/logo*.svg` | ☐ |
| Favicon | `static/images/favicon.ico` | ☐ |
| i18n: copyright & poweredBy | **Tất cả** `i18n/*.yaml` (en, vi, ja, zh-cn, fa, …) | ☐ |
| Thông báo banner | `hugo.yaml` → `languages.*.params.banner.message` | ☐ |
| Nội dung trang chủ | `content/*/\_index.md` | ☐ |
| Trang Giới thiệu | `content/*/about/index.md` | ☐ |
| Thay PROJECT_NAME | Toàn bộ nội dung (front matter + body) | ☐ |
| Cấu hình Giscus (nếu dùng) | `hugo.yaml` → `params.comments.giscus` | ☐ |

## Theme Key

Trong `hugo.yaml` có dòng `theme: hextra`. Đây là **tên thư mục theme** mà Hugo tải.

- **Nếu bạn dùng repo nguyên bản** (theme trong thư mục tên `hextra`), giữ nguyên `theme: hextra`.
- **Nếu bạn copy hoặc đổi tên thư mục theme** (ví dụ thành `mytheme`), đặt `theme: mytheme` để Hugo tải đúng layout.

## Thông báo Banner theo ngôn ngữ

Chữ banner phía trên trang được cấu hình **theo từng ngôn ngữ** trong `hugo.yaml` tại `languages.<lang>.params.banner.message`. Cập nhật cho từng ngôn ngữ bạn dùng:

```yaml {filename="hugo.yaml"}
languages:
  en:
    title: Your Project Name
    params:
      banner:
        message: |
          Your Project **v1.0** is here! 🎉 [What's new](/blog/setup-v1/)
  vi:
    title: Tên Dự Án
    params:
      banner:
        message: |
          Dự án **v1.0** đã ra mắt! 🎉 [Xem thêm](/blog/setup-v1/)
```

Để tắt banner cho một ngôn ngữ, xóa block `params.banner` hoặc để `message` rỗng.

## Các File Cần Cập nhật Thủ công

Một số file không thể dùng cấu hình động và phải cập nhật thủ công:

| File | Cần thay đổi gì |
|------|-----------------|
| `go.mod` | Đường dẫn module (nếu dùng Hugo Modules) |
| `README.md` | Mô tả dự án và badges |
| `LICENSE` | Nội dung giấy phép nếu thay đổi loại |
| `hugo.yaml` → `theme` | Đặt tên thư mục theme nếu bạn đã đổi tên |
| Front matter & body nội dung | Tiêu đề trang và mọi chữ **PROJECT_NAME** trong nội dung |
| Thông báo banner | `hugo.yaml` → `languages.<lang>.params.banner.message` (xem trên) |

## Thay thế Placeholder URL GitHub

Template sử dụng các giá trị placeholder cho URL GitHub trong toàn bộ codebase:
- **Trong nội dung documentation**: `your-username` và `your-project` (dễ đọc)
- **Trong file config**: `{author}` và `{project_name}` (cho thay thế tự động)

Khi fork theme này cho dự án của bạn, bạn cần thay thế các placeholder này bằng username GitHub và tên repository thực tế.

### Tìm và Thay thế

Sử dụng tính năng find-and-replace của editor để cập nhật:

| Placeholder | Thay bằng | Ví dụ |
|-------------|-----------|-------|
| `your-username` | Username GitHub của bạn | `mycompany` |
| `your-project` | Tên repository | `my-docs` |
| `{author}` | Username GitHub của bạn | `mycompany` |
| `{project_name}` | Tên repository | `my-docs` |

### Các File Chứa Placeholder

| File | Định dạng Placeholder | Mục đích |
|------|----------------------|----------|
| `go.mod` | `{author}/{project_name}` | Đường dẫn Go module |
| `docs/go.mod` | `{author}/{project_name}` | Đường dẫn module docs |
| `theme.toml` | `{author}/{project_name}` | Metadata theme |
| `README.md`, `README.*.md` | `{author}/{project_name}` | Tài liệu dự án |
| `.github/CONTRIBUTING.md` | `{author}/{project_name}` | Hướng dẫn đóng góp |
| `.github/FUNDING.yml` | `{author}` | Cấu hình GitHub Sponsors |
| `docs/content/**/*.md` | `your-username/your-project` | Nội dung documentation |
| `layouts/_partials/components/analytics/*.html` | `{author}.github.io/{project_name}` trong thông báo lỗi | Gợi ý cấu hình Umami, Matomo, GoatCounter |

### Lệnh Thay thế Nhanh

Trước khi chạy: thay `YOUR_GITHUB_USER` và `YOUR_REPO` trong lệnh bằng username và tên repo GitHub thực của bạn.

**File config** (go.mod, theme.toml, …) dùng `{author}` và `{project_name}`. **File content** (`docs/content/**/*.md`) dùng `your-username` và `your-project`. Chạy cả hai nhóm lệnh:

```bash
# Linux/macOS - File config ({author} → giá trị của bạn)
find . -type f \( -name "*.yaml" -o -name "*.toml" -o -name "go.mod" \) \
  -exec sed -i 's/{author}/YOUR_GITHUB_USER/g; s/{project_name}/YOUR_REPO/g' {} +

# Linux/macOS - File content (your-username/your-project → giá trị của bạn)
find ./docs/content -type f -name "*.md" \
  -exec sed -i 's/your-username/YOUR_GITHUB_USER/g; s/your-project/YOUR_REPO/g' {} +
```

```powershell
# Windows PowerShell - File config
Get-ChildItem -Recurse -Include *.yaml,*.toml,go.mod | 
  ForEach-Object { (Get-Content $_) -replace '\{author\}','YOUR_GITHUB_USER' -replace '\{project_name\}','YOUR_REPO' | Set-Content $_ }

# Windows PowerShell - File content
Get-ChildItem -Path docs/content -Recurse -Include *.md |
  ForEach-Object { (Get-Content $_) -replace 'your-username','YOUR_GITHUB_USER' -replace 'your-project','YOUR_REPO' | Set-Content $_ }
```

## Ví dụ Bắt đầu Nhanh

Cấu hình tối thiểu cho một triển khai mới:

```yaml {filename="hugo.yaml"}
baseURL: "https://docs.doanhnghiep.com/"
title: "Tài liệu Doanh nghiệp"

params:
  project:
    name: "Doanh Nghiệp"
    shortName: "DN"
    description: "Tài liệu cho các sản phẩm Doanh Nghiệp"
    organization: "Công ty Doanh Nghiệp"
    github: "https://github.com/doanhnghiep/docs"
    githubEditBase: "https://github.com/doanhnghiep/docs/edit/main/docs/content"
    website: "https://doanhnghiep.com"
    currentVersion: "v1.0"
```

Sau đó cập nhật:
1. URL link GitHub trong `menu.main` (identifier: github)
2. File logo trong `static/images/`
3. Nội dung trang chủ và trang Giới thiệu

## Mẹo cho Triển khai Đa Doanh nghiệp

1. **Duy trì template cơ sở** - Giữ một phiên bản sạch không có nội dung riêng của doanh nghiệp
2. **Sử dụng Git branches** - Tạo branch riêng cho các triển khai khác nhau
3. **Ghi chú các thay đổi** - Lưu lại những gì đã tùy chỉnh cho mỗi triển khai
4. **Tự động hóa thiết lập** - Cân nhắc tạo script setup nhắc nhập thông tin dự án
5. **Tìm kiếm PROJECT_NAME** - Template sử dụng `PROJECT_NAME` làm placeholder; tìm và thay thế bằng tên dự án thực tế của bạn
