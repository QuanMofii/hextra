---
title: "Init Setup Project V.1.0"
date: 2026-02-22
authors:
  - name: QuanMofii
    link: https://quanmofii.github.io/
weight: 1
tags:
  - Setup
  - Guide
---

This post describes the initial setup of this documentation project (version 1): how to clone, configure, and run the site for your own business or product.

<!--more-->

## What’s in this template

- **Docs site** — Multi-language documentation (en, vi, ja, zh-cn, fa) with sidebar, search, and theme customization.
- **Single config** — Project name, GitHub URLs, logo, and menu are driven from `hugo.yaml` (see [Site Config](/guide/site-config/)).
- **Placeholders** — Replace `PROJECT_NAME`, `your-username`, `your-project`, and `{author}` / `{project_name}` with your values (see the same guide).

## Quick start

1. Replace GitHub and project placeholders (see [Replacing GitHub URL Placeholders](/guide/site-config/#replacing-github-url-placeholders)).
2. Update `docs/hugo.yaml`: `baseURL`, `title`, `params.project.*`, and language titles.
3. Update `i18n/*.yaml` for copyright and any menu labels you need.
4. Run `npm install` then `npm run dev:theme` from the repo root.

For a full checklist, see [Site Config](/guide/site-config/).
