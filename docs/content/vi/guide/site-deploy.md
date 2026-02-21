---
title: Triển khai site
prev: /guide/shortcodes
next: /docs/advanced
---

Hugo tạo website tĩnh, cho phép linh hoạt trong cách host. Trang này hướng dẫn triển khai site PROJECT_NAME trên các nền tảng khác nhau.

<!--more-->


## GitHub Pages

[GitHub Pages](https://docs.github.com/pages) là cách được khuyến nghị để triển khai và host website miễn phí.

Nếu bạn tạo site từ [hextra-starter-template](https://github.com/your-username/your-project-starter-template), template đã có sẵn workflow GitHub Actions để tự động triển khai lên GitHub Pages.

{{% details title="Cấu hình GitHub Actions" closed="true" %}}

Dưới đây là ví dụ cấu hình từ [hextra-starter-template](https://github.com/your-username/your-project-starter-template):

```yaml {filename=".github/workflows/pages.yaml"}
# Workflow mẫu để build và triển khai site Hugo lên GitHub Pages
name: Deploy Hugo site to Pages

on:
  # Chạy khi push lên nhánh mặc định
  push:
    branches: ["main"]

  # Cho phép chạy thủ công từ tab Actions
  workflow_dispatch:

# Quyền GITHUB_TOKEN để triển khai lên GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Chỉ một lần triển khai đồng thời
concurrency:
  group: "pages"
  cancel-in-progress: false

defaults:
  run:
    shell: bash

jobs:
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.147.7
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          fetch-depth: 0
          submodules: recursive
      - name: Setup Go
        uses: actions/setup-go@v5
        with:
          go-version: '1.22'
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v4
      - name: Setup Hugo
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb
      - name: Build with Hugo
        env:
          HUGO_ENVIRONMENT: production
          HUGO_ENV: production
        run: |
          hugo \
            --gc --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

{{% /details %}}


{{< callout type="warning" >}}
  Trong cài đặt repository, đặt **Pages** > **Build and deployment** > **Source** thành **GitHub Actions**:
  ![](https://user-images.githubusercontent.com/5097752/266784808-99676430-884e-42ab-b901-f6534a0d6eee.png)
{{< /callout >}}

Mặc định workflow GitHub Actions `.github/workflows/pages.yaml` trên giả định site triển khai tới `https://<USERNAME>.github.io/<REPO>/`.

Nếu bạn triển khai tới `https://<USERNAME>.github.io/` thì sửa `--baseURL`:

```yaml {filename=".github/workflows/pages.yaml",linenos=table,linenostart=54,hl_lines=[4]}
run: |
  hugo \
    --gc --minify \
    --baseURL "https://${{ github.repository_owner }}.github.io/"
```

Nếu triển khai lên tên miền riêng, hãy đổi giá trị `--baseURL` cho phù hợp.


## Cloudflare Pages

1. Đưa mã nguồn site vào repository Git (ví dụ GitHub)
2. Đăng nhập [Cloudflare dashboard](https://dash.cloudflare.com/) và chọn tài khoản
3. Ở Account Home, chọn **Workers & Pages** > **Create application** > **Pages** > **Connect to Git**
4. Chọn repository, trong mục **Set up builds and deployments** điền:

| Cấu hình          | Giá trị                 |
| ----------------- | ----------------------- |
| Production branch | `main`                  |
| Build command     | `hugo --gc --minify`    |
| Build directory   | `public`                |

Chi tiết thêm:
- [Triển khai site Hugo](https://developers.cloudflare.com/pages/framework-guides/deploy-a-hugo-site/#deploy-with-cloudflare-pages).
- [Hỗ trợ ngôn ngữ và công cụ](https://developers.cloudflare.com/pages/platform/language-support-and-tools/).


## Netlify

1. Đẩy code lên repository Git (GitHub, GitLab, v.v.)
2. [Import dự án](https://app.netlify.com/start) vào Netlify
3. Nếu không dùng [hextra-starter-template][hextra-starter-template], cấu hình thủ công:
   - Build command: `hugo --gc --minify`
   - Publish directory: `public`
   - Biến môi trường `HUGO_VERSION` = `0.147.7`, hoặc đặt trong file `netlify.toml`
4. Triển khai.

Xem [Hugo trên Netlify](https://docs.netlify.com/integrations/frameworks/hugo/) để biết thêm.


## Vercel

1. Đẩy code lên repository Git (GitHub, GitLab, v.v.)
2. Vào [Vercel Dashboard](https://vercel.com/dashboard) và import dự án Hugo
3. Cấu hình dự án, chọn Hugo làm Framework Preset
4. Ghi đè Build Command và Install command:
   1. Build Command: `hugo --gc --minify`
   2. Install Command: `yum install golang`

![Cấu hình triển khai Vercel](https://github.com/your-username/your-project/assets/5097752/887d949b-8d05-413f-a2b4-7ab92192d0b3)
