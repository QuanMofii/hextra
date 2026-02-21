---
title: "项目初始设置 V.1.0"
date: 2026-02-22
authors:
  - name: QuanMofii
    link: https://quanmofii.github.io/
weight: 1
tags:
  - 设置
  - 指南
---

本文说明本文档项目（版本 1）的初始设置：如何克隆、配置并运行站点，用于您自己的业务或产品。

<!--more-->

## 本模板包含什么

- **文档站点** — 多语言（en、vi、ja、zh-cn、fa），带侧栏、搜索和主题定制。
- **单一配置** — 项目名称、GitHub 链接、Logo、菜单均由 `hugo.yaml` 驱动（见 [站点配置](/guide/site-configuration/)）。
- **占位符** — 将 `PROJECT_NAME`、`your-username`、`your-project` 以及 `{author}` / `{project_name}` 替换为您的实际内容（见同一页面）。

## 快速开始

1. 替换 GitHub 与项目占位符（见 [替换 GitHub URL 占位符](/guide/site-configuration/#替换github-url占位符)）。
2. 更新 `docs/hugo.yaml`：`baseURL`、`title`、`params.project.*` 及各语言标题。
3. 在 `i18n/*.yaml` 中更新版权与所需菜单文案。
4. 在仓库根目录执行 `npm install`，然后执行 `npm run dev:theme`。

完整清单见 [站点配置](/guide/site-configuration/)。
