---
title: サイト設定
linkTitle: サイト設定
weight: 9
---

このガイドでは、このドキュメントサイトをビジネスやプロジェクト向けに設定する方法を説明します。すべてのプロジェクト情報は単一の設定ファイルに集約されており、異なる組織向けのブランド変更とデプロイが簡単です。

<!--more-->

## 概要

このドキュメントテンプレートを新しいビジネス向けにデプロイする際、以下のプロジェクトメタデータを更新する必要があります：
- プロジェクト/製品名
- 説明とタグライン
- GitHubリポジトリURL
- ロゴとブランドアセット
- 連絡先とソーシャルリンク

これらの設定はすべて**1つのファイル**に集約されています：`hugo.yaml`。

**設定ファイルの場所:** このリポジトリ構造では、メインの設定ファイルは `--source=docs` でHugoを実行する場合（例: `npm run dev:theme`）**`docs/hugo.yaml`**です。本ガイドのパスは特記がない限りこのファイルを指します。

## 設定ファイルの構造

`hugo.yaml`（つまり `docs/hugo.yaml`）を開き、`params.project`セクションを見つけてください。これがすべてのプロジェクトメタデータの**単一ソース**です：

```yaml {filename="hugo.yaml"}
params:
  project:
    # コアアイデンティティ
    name: "プロジェクト名"
    shortName: "PN"
    tagline: "素晴らしいタグライン"
    
    # 説明
    description: "SEOとメタタグ用のプロジェクトの完全な説明。"
    shortDescription: "ヒーローセクション用の簡潔な説明"
    
    # 組織/著者情報
    author: "あなたの名前"
    organization: "あなたの組織"
    email: "contact@example.com"
    
    # リンク
    website: "https://your-website.com"
    github: "https://github.com/your-org/your-repo"
    githubEditBase: "https://github.com/your-org/your-repo/edit/main/docs/content"
```

## ステップバイステップ設定ガイド

{{< steps >}}

### 基本設定を更新

`hugo.yaml`の先頭で更新：

```yaml {filename="hugo.yaml"}
baseURL: "https://docs.your-domain.com/"
title: "プロジェクト名"
```

### プロジェクト情報を更新

`params.project`セクションで、すべてのフィールドをビジネス情報で更新します。

### 言語タイトルを更新

`languages`セクションで各言語の`title`を更新します。

### メニューリンクを更新

メインメニューのGitHubリンクを更新します。**メニューラベル（Products, Versions, Showcase, Blog, Guide）**は**i18n**で翻訳されています。ヘッダー/ナビバーに表示する文言を変えるには、各 `i18n/*.yaml`（例: `i18n/en.yaml`, `i18n/ja.yaml`）の `products`, `versions`, `showcase`, `blog`, `guide`, `more` を編集してください。

### ブランドアセットを置き換え

`static/images/`の以下のファイルを置き換えます：

| ファイル | 用途 |
|----------|------|
| `logo.svg` | ライトモードロゴ |
| `logo-dark.svg` | ダークモードロゴ |
| `favicon.ico` | ブラウザファビコン |

### コンテンツを更新

メインコンテンツページを更新：
- ホームページ：`content/{lang}/_index.md`
- Aboutページ：`content/{lang}/about/index.md`

{{< /steps >}}

## コンテンツでのプロジェクト情報の使用

ショートコードを使用してコンテンツ内でプロジェクト情報を動的に表示できます：

```markdown
{{</* project "name" */>}}へようこそ！

{{</* project "description" */>}}

現在のバージョン：{{</* project "currentVersion" */>}}
```

## 推奨リブランド順序

以下の順で進めると抜けがありません。

1. **設定** — `hugo.yaml`: `baseURL`, `title`, `params.project.*`, `languages.*.title`, `menu.main`（GitHub）, `params.editURL.base`, `theme`（テーマフォルダ名を変えた場合）
2. **i18n** — `i18n/*.yaml` の**すべて**のファイル（en, vi, ja, zh-cn, fa 等）で: `copyright`, `poweredBy`、必要に応じてメニューキー（`products`, `versions`, `showcase` 等）
3. **ブランド** — `static/images/` のロゴとファビコンを差し替え
4. **バナー** — 使用する言語ごとに `hugo.yaml` の `languages.<lang>.params.banner.message` を更新（下記[言語別バナーメッセージ](#言語別バナーメッセージ)参照）
5. **コンテンツ** — ホーム、About、および全コンテンツ（front matter・本文）で **PROJECT_NAME** を検索・置換
6. **プレースホルダー** — [GitHub URLプレースホルダーの置換](#github-urlプレースホルダーの置換)の一覧に従い、`{author}`, `{project_name}`, `your-username`, `your-project` を置換

## 設定チェックリスト

| 項目 | 場所 | 状態 |
|------|------|------|
| Base URL | `hugo.yaml` → `baseURL` | ☐ |
| サイトタイトル | `hugo.yaml` → `title` | ☐ |
| プロジェクト情報 | `hugo.yaml` → `params.project.*` | ☐ |
| 言語タイトル | `hugo.yaml` → `languages.*.title` | ☐ |
| テーマキー（テーマフォルダ名を変えた場合） | `hugo.yaml` → `theme` | ☐ |
| GitHubメニューリンク | `hugo.yaml` → `menu.main` | ☐ |
| 編集URL | `hugo.yaml` → `params.editURL.base` | ☐ |
| ロゴファイル | `static/images/logo*.svg` | ☐ |
| ファビコン | `static/images/favicon.ico` | ☐ |
| i18n: copyright & poweredBy | **全** `i18n/*.yaml`（en, vi, ja, zh-cn, fa 等） | ☐ |
| バナーメッセージ | `hugo.yaml` → `languages.*.params.banner.message` | ☐ |
| ホームページ | `content/*/\_index.md` | ☐ |
| Aboutページ | `content/*/about/index.md` | ☐ |
| PROJECT_NAMEの置換 | 全コンテンツ（front matter・本文） | ☐ |
| Giscus（使用時） | `hugo.yaml` → `params.comments.giscus` | ☐ |

## テーマキー

`hugo.yaml` に `theme: hextra` とあります。これはHugoが読み込む**テーマフォルダ名**です。

- **このリポジトリをそのまま使う場合**（テーマが `hextra` という名前のサブフォルダにある場合）は `theme: hextra` のままでよいです。
- **テーマフォルダをコピーまたはリネームした場合**（例: `mytheme`）は、`theme: mytheme` に設定してください。

## 言語別バナーメッセージ

ページ上部のバナー文言は、`hugo.yaml` の `languages.<lang>.params.banner.message` で**言語ごと**に設定します。使用する言語ごとに更新してください。

```yaml {filename="hugo.yaml"}
languages:
  en:
    title: Your Project Name
    params:
      banner:
        message: |
          Your Project **v1.0** is here! 🎉 [What's new]({{% relref "blog/setup-v1.md" %}})
  ja:
    title: プロジェクト名
    params:
      banner:
        message: |
          プロジェクト **v1.0** リリース！🎉 [新着はこちら]({{% relref "blog/setup-v1.md" %}})
```

バナーを無効にするには、その言語の `params.banner` ブロックを削除するか、`message` を空にしてください。

## 手動で更新が必要なファイル

次のファイルは動的設定が使えず、手動で更新します。

| ファイル | 変更内容 |
|----------|----------|
| `go.mod` | モジュールパス（Hugo Modules使用時） |
| `README.md` | プロジェクト説明とバッジ |
| `LICENSE` | ライセンス種類を変える場合の文言 |
| `hugo.yaml` → `theme` | テーマフォルダ名を変えた場合 |
| コンテンツの front matter・本文 | ページタイトルおよび **PROJECT_NAME** の検索・置換 |
| バナーメッセージ | `hugo.yaml` → `languages.<lang>.params.banner.message`（上記参照） |

## GitHub URLプレースホルダーの置換

テンプレートはコードベース全体でGitHub URLにプレースホルダー値を使用しています：
- **ドキュメントコンテンツ内**: `your-username` と `your-project`（人間が読みやすい形式）
- **設定ファイル内**: `{author}` と `{project_name}`（自動置換用）

このテーマをフォークする際は、これらのプレースホルダーを実際のGitHubユーザー名とリポジトリ名に置き換える必要があります。

### 検索と置換

エディタの検索・置換機能を使用して更新：

| プレースホルダー | 置換先 | 例 |
|------------------|--------|-----|
| `your-username` | GitHubユーザー名 | `mycompany` |
| `your-project` | リポジトリ名 | `my-docs` |
| `{author}` | GitHubユーザー名 | `mycompany` |
| `{project_name}` | リポジトリ名 | `my-docs` |

### プレースホルダーを含むファイル

| ファイル | プレースホルダー形式 | 目的 |
|----------|---------------------|------|
| `go.mod` | `{author}/{project_name}` | Goモジュールパス |
| `docs/go.mod` | `{author}/{project_name}` | Docsモジュールパス |
| `theme.toml` | `{author}/{project_name}` | テーマメタデータ |
| `README.md`, `README.*.md` | `{author}/{project_name}` | プロジェクトドキュメント |
| `.github/CONTRIBUTING.md` | `{author}/{project_name}` | コントリビューションガイド |
| `.github/FUNDING.yml` | `{author}` | GitHub Sponsors設定 |
| `docs/content/**/*.md` | `your-username/your-project` | ドキュメントコンテンツ |
| `layouts/_partials/components/analytics/*.html` | エラーメッセージ内の `{author}.github.io/{project_name}` | Umami/Matomo/GoatCounter設定のヒント |

### クイック置換コマンド

実行前に、コマンド内の `YOUR_GITHUB_USER` と `YOUR_REPO` を実際のGitHubユーザー名とリポジトリ名に置き換えてください。**設定ファイル**（go.mod, theme.toml 等）は `{author}` / `{project_name}`、**コンテンツ**（`docs/content/**/*.md`）は `your-username` / `your-project` を使用。両方実行します。

```bash
# Linux/macOS - 設定ファイル
find . -type f \( -name "*.yaml" -o -name "*.toml" -o -name "go.mod" \) \
  -exec sed -i 's/{author}/YOUR_GITHUB_USER/g; s/{project_name}/YOUR_REPO/g' {} +
# Linux/macOS - コンテンツ
find ./docs/content -type f -name "*.md" \
  -exec sed -i 's/your-username/YOUR_GITHUB_USER/g; s/your-project/YOUR_REPO/g' {} +
```

```powershell
# PowerShell - 設定ファイル
Get-ChildItem -Recurse -Include *.yaml,*.toml,go.mod | ForEach-Object { (Get-Content $_) -replace '\{author\}','YOUR_GITHUB_USER' -replace '\{project_name\}','YOUR_REPO' | Set-Content $_ }
# PowerShell - コンテンツ
Get-ChildItem -Path docs/content -Recurse -Include *.md | ForEach-Object { (Get-Content $_) -replace 'your-username','YOUR_GITHUB_USER' -replace 'your-project','YOUR_REPO' | Set-Content $_ }
```

## クイックスタート例

新しいデプロイのための最小限の設定：

```yaml {filename="hugo.yaml"}
baseURL: "https://docs.mybusiness.com/"
title: "マイビジネスドキュメント"

params:
  project:
    name: "マイビジネス"
    shortName: "MB"
    description: "マイビジネス製品のドキュメント"
    organization: "マイビジネス株式会社"
    github: "https://github.com/mybusiness/docs"
    githubEditBase: "https://github.com/mybusiness/docs/edit/main/docs/content"
    website: "https://mybusiness.com"
    currentVersion: "v1.0"
```

その後更新：
1. `menu.main`のGitHubリンクURL（identifier: github）
2. `static/images/`のロゴファイル
3. ホームページとAboutページのコンテンツ

## マルチデプロイのヒント

1. **ベーステンプレートを維持** - ビジネス固有のコンテンツなしのクリーンなバージョンを保持
2. **Gitブランチを使用** - 異なるデプロイ用に別々のブランチを作成
3. **変更を記録** - 各デプロイでカスタマイズした内容をメモ
4. **セットアップを自動化** - プロジェクト情報を入力するセットアップスクリプトの作成を検討
5. **PROJECT_NAMEを検索** - テンプレートは`PROJECT_NAME`をプレースホルダーとして使用；実際のプロジェクト名で検索・置換
