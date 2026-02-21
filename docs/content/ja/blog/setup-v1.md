---
title: "プロジェクト初期セットアップ V.1.0"
date: 2026-02-22
authors:
  - name: QuanMofii
    link: https://quanmofii.github.io/
weight: 1
tags:
  - セットアップ
  - ガイド
---

このドキュメントプロジェクト（バージョン1）の初期セットアップについて説明します：自社のビジネスや製品向けにサイトをクローン・設定・実行する方法です。

<!--more-->

## このテンプレートの内容

- **ドキュメントサイト** — 多言語（en, vi, ja, zh-cn, fa）対応。サイドバー、検索、テーマのカスタマイズが可能。
- **単一設定** — プロジェクト名、GitHub URL、ロゴ、メニューは `hugo.yaml` で管理（[サイト設定](/guide/site-config/) 参照）。
- **プレースホルダー** — `PROJECT_NAME`、`your-username`、`your-project`、`{author}` / `{project_name}` を実際の値に置き換えてください（同上）。

## クイックスタート

1. GitHub とプロジェクトのプレースホルダーを置換（[GitHub URLプレースホルダーの置換](/guide/site-config/#github-urlプレースホルダーの置換) 参照）。
2. `docs/hugo.yaml` を更新：`baseURL`、`title`、`params.project.*`、各言語のタイトル。
3. `i18n/*.yaml` で copyright と必要なメニューラベルを更新。
4. リポジトリルートで `npm install` のあと `npm run dev:theme` を実行。

完全なチェックリストは [サイト設定](/guide/site-config/) を参照してください。
