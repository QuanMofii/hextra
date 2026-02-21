---
title: "Thiết lập Ban đầu Dự án V.1.0"
date: 2026-02-22
authors:
  - name: QuanMofii
    link: https://quanmofii.github.io
    image: https://github.com/quanmofii.png
weight: 1
tags:
  - Thiết lập
  - Hướng dẫn
---

Bài viết mô tả thiết lập ban đầu của dự án tài liệu này (phiên bản 1): cách clone, cấu hình và chạy site cho doanh nghiệp hoặc sản phẩm của bạn.

<!--more-->

## Trong template có gì

- **Site tài liệu** — Đa ngôn ngữ (en, vi, ja, zh-cn, fa) với sidebar, tìm kiếm và tùy chỉnh theme.
- **Một file cấu hình** — Tên dự án, URL GitHub, logo và menu lấy từ `hugo.yaml` (xem [Cấu hình Site](/guide/site-configuration/)).
- **Placeholder** — Thay `PROJECT_NAME`, `your-username`, `your-project` và `{author}` / `{project_name}` bằng giá trị của bạn (xem cùng trang).

## Bắt đầu nhanh

1. Thay placeholder GitHub và dự án (xem [Thay thế Placeholder URL GitHub](/guide/site-configuration/#thay-thế-placeholder-url-github)).
2. Cập nhật `docs/hugo.yaml`: `baseURL`, `title`, `params.project.*` và tiêu đề ngôn ngữ.
3. Cập nhật `i18n/*.yaml` cho copyright và nhãn menu (nếu cần).
4. Chạy `npm install` rồi `npm run dev:theme` từ thư mục gốc repo.

Checklist đầy đủ xem [Cấu hình Site](/guide/site-configuration/).
