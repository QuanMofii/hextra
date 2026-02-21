---
title: "راه‌اندازی اولیه پروژه V.1.0"
date: 2026-02-22
authors:
  - name: QuanMofii
    link: https://quanmofii.github.io
    image: https://github.com/quanmofii.png
weight: 1
tags:
  - راه‌اندازی
  - راهنما
---

این مطلب راه‌اندازی اولیه پروژه مستندات (نسخه ۱) را توضیح می‌دهد: نحوه کلون، پیکربندی و اجرای سایت برای کسب‌وکار یا محصول خودتان.

<!--more-->

## در این قالب چه هست

- **سایت مستندات** — چندزبانه (en, vi, ja, zh-cn, fa) با نوار کناری، جستجو و سفارشی‌سازی تم.
- **یک فایل پیکربندی** — نام پروژه، آدرس‌های GitHub، لوگو و منو از `hugo.yaml` خوانده می‌شوند (ببینید [پیکربندی سایت](/guide/site-configuration/)).
- **جایگزین‌ها** — `PROJECT_NAME`، `your-username`، `your-project` و `{author}` / `{project_name}` را با مقادیر خود عوض کنید (همان راهنما).

## شروع سریع

1. جایگزین‌های GitHub و پروژه را عوض کنید ([جایگزینی جایگزین‌های URL گیت‌هاب](/guide/site-configuration/#جایگزینی-جایگزین‌های-url-گیت‌هاب)).
2. `docs/hugo.yaml` را به‌روز کنید: `baseURL`، `title`، `params.project.*` و عناوین زبان‌ها.
3. در `i18n/*.yaml` مقدار copyright و در صورت نیاز برچسب‌های منو را تنظیم کنید.
4. از ریشهٔ مخزن `npm install` و سپس `npm run dev:theme` را اجرا کنید.

برای چک‌لیست کامل [پیکربندی سایت](/guide/site-configuration/) را ببینید.
