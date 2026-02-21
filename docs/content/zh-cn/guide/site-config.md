---
title: 站点配置
linkTitle: 站点配置
weight: 9
---

本指南说明如何为您的业务或项目配置此文档站点。所有项目信息都集中在单个配置文件中，使不同组织的品牌更换和部署变得简单。

<!--more-->

## 概述

为新业务部署此文档模板时，您需要更新项目元数据：
- 项目/产品名称
- 描述和标语
- GitHub仓库URL
- Logo和品牌资源
- 联系方式和社交链接

所有这些设置都集中在**一个文件**中：`hugo.yaml`。

**配置文件位置：** 在本仓库结构中，当使用 `--source=docs` 运行 Hugo 时（如 `npm run dev:theme`），主配置文件为 **`docs/hugo.yaml`**。本指南中的路径如无特别说明均指该文件。

## 配置文件结构

打开 `hugo.yaml`（即 `docs/hugo.yaml`）并找到 `params.project` 部分。这是所有项目元数据的**单一来源**：

```yaml {filename="hugo.yaml"}
params:
  project:
    # 核心标识
    name: "您的项目名称"
    shortName: "YPN"
    tagline: "您的精彩标语"
    
    # 描述
    description: "用于SEO和元标签的项目完整描述。"
    shortDescription: "用于hero部分的简短描述"
    
    # 组织/作者信息
    author: "您的姓名"
    organization: "您的组织"
    email: "contact@example.com"
    
    # 链接
    website: "https://your-website.com"
    github: "https://github.com/your-org/your-repo"
    githubEditBase: "https://github.com/your-org/your-repo/edit/main/docs/content"
```

## 分步配置指南

{{< steps >}}

### 更新基本设置

在`hugo.yaml`顶部更新：

```yaml {filename="hugo.yaml"}
baseURL: "https://docs.your-domain.com/"
title: "您的项目名称"
```

### 更新项目信息

在`params.project`部分，用您的业务信息更新所有字段。

### 更新语言标题

在`languages`部分更新每种语言的`title`。

### 更新菜单链接

更新主菜单中的GitHub链接。**菜单标签（Products、Versions、Showcase、Blog、Guide）** 通过 **i18n** 翻译。要修改页眉/导航栏显示的文字，请编辑各 `i18n/*.yaml`（如 `i18n/en.yaml`、`i18n/zh-cn.yaml`）中的 `products`、`versions`、`showcase`、`blog`、`guide`、`more` 键。

### 替换品牌资源

替换`static/images/`中的以下文件：

| 文件 | 用途 |
|------|------|
| `logo.svg` | 亮色模式logo |
| `logo-dark.svg` | 暗色模式logo |
| `favicon.ico` | 浏览器图标 |

### 更新内容

更新主要内容页面：
- 首页：`content/{lang}/_index.md`
- 关于页面：`content/{lang}/about/index.md`

{{< /steps >}}

## 在内容中使用项目信息

您可以使用短代码在内容中动态显示项目信息：

```markdown
欢迎使用{{</* project "name" */>}}！

{{</* project "description" */>}}

当前版本：{{</* project "currentVersion" */>}}
```

## 推荐换品牌顺序

按以下顺序进行可避免遗漏：

1. **配置** — `hugo.yaml`：`baseURL`、`title`、`params.project.*`、`languages.*.title`、`menu.main`（GitHub）、`params.editURL.base`，若重命名了 theme 文件夹则改 `theme`。
2. **i18n** — 在 **所有** `i18n/*.yaml`（en、vi、ja、zh-cn、fa 等）中：`copyright`、`poweredBy`，以及如需翻译菜单标签则改 `products`、`versions`、`showcase` 等。
3. **品牌** — 替换 `static/images/` 中的 logo 和 favicon。
4. **横幅** — 在 `hugo.yaml` 中按语言更新 `languages.<lang>.params.banner.message`（见下方[按语言横幅消息](#按语言横幅消息)）。
5. **内容** — 首页、关于页，并在全部内容（front matter 与正文）中搜索并替换 **PROJECT_NAME**。
6. **占位符** — 在[替换 GitHub URL 占位符](#替换github-url占位符)所列文件中替换 `{author}`、`{project_name}`、`your-username`、`your-project`。

## 配置清单

| 项目 | 位置 | 状态 |
|------|------|------|
| Base URL | `hugo.yaml` → `baseURL` | ☐ |
| 站点标题 | `hugo.yaml` → `title` | ☐ |
| 项目信息 | `hugo.yaml` → `params.project.*` | ☐ |
| 语言标题 | `hugo.yaml` → `languages.*.title` | ☐ |
| 主题键（若重命名 theme 文件夹） | `hugo.yaml` → `theme` | ☐ |
| GitHub菜单链接 | `hugo.yaml` → `menu.main` | ☐ |
| 编辑URL | `hugo.yaml` → `params.editURL.base` | ☐ |
| Logo文件 | `static/images/logo*.svg` | ☐ |
| Favicon | `static/images/favicon.ico` | ☐ |
| i18n：copyright 与 poweredBy | **所有** `i18n/*.yaml`（en、vi、ja、zh-cn、fa 等） | ☐ |
| 横幅消息 | `hugo.yaml` → `languages.*.params.banner.message` | ☐ |
| 首页内容 | `content/*/\_index.md` | ☐ |
| 关于页 | `content/*/about/index.md` | ☐ |
| 替换 PROJECT_NAME | 全部内容（front matter + 正文） | ☐ |
| Giscus（若使用） | `hugo.yaml` → `params.comments.giscus` | ☐ |

## 主题键

在 `hugo.yaml` 中可见 `theme: hextra`，这是 Hugo 加载的 **主题文件夹名**。

- **直接使用本仓库**（主题在名为 `hextra` 的子文件夹中）时，保持 `theme: hextra` 即可。
- **复制或重命名主题文件夹**（如改为 `mytheme`）时，需设置 `theme: mytheme`。

## 按语言横幅消息

页面顶部横幅文字在 `hugo.yaml` 的 `languages.<lang>.params.banner.message` 中 **按语言** 设置。请为使用的每种语言更新：

```yaml {filename="hugo.yaml"}
languages:
  en:
    title: Your Project Name
    params:
      banner:
        message: |
          Your Project **v1.0** is here! 🎉 [What's new](/blog/setup-v1/)
  zh-cn:
    title: 您的项目名称
    params:
      banner:
        message: |
          您的项目 **v1.0** 发布！🎉 [查看更新](/blog/setup-v1/)
```

要关闭某语言的横幅，可删除该语言的 `params.banner` 块或将 `message` 设为空。

## 需手动更新的文件

以下文件无法通过动态配置，需手动修改：

| 文件 | 修改内容 |
|------|----------|
| `go.mod` | 模块路径（使用 Hugo Modules 时） |
| `README.md` | 项目说明与徽章 |
| `LICENSE` | 若更换许可证类型时的正文 |
| `hugo.yaml` → `theme` | 若重命名了主题文件夹 |
| 内容 front matter 与正文 | 页面标题及所有 **PROJECT_NAME** 的搜索与替换 |
| 横幅消息 | `hugo.yaml` → `languages.<lang>.params.banner.message`（见上） |

## 替换GitHub URL占位符

模板在整个代码库中使用占位符值作为GitHub URL：
- **文档内容中**: `your-username` 和 `your-project`（易读格式）
- **配置文件中**: `{author}` 和 `{project_name}`（用于自动替换）

当您fork此主题用于您的项目时，需要将这些占位符替换为您的实际GitHub用户名和仓库名。

### 搜索和替换

使用编辑器的查找替换功能进行更新：

| 占位符 | 替换为 | 示例 |
|--------|--------|------|
| `your-username` | 您的GitHub用户名 | `mycompany` |
| `your-project` | 您的仓库名 | `my-docs` |
| `{author}` | 您的GitHub用户名 | `mycompany` |
| `{project_name}` | 您的仓库名 | `my-docs` |

### 包含占位符的文件

| 文件 | 占位符格式 | 用途 |
|------|-----------|------|
| `go.mod` | `{author}/{project_name}` | Go模块路径 |
| `docs/go.mod` | `{author}/{project_name}` | Docs模块路径 |
| `theme.toml` | `{author}/{project_name}` | 主题元数据 |
| `README.md`, `README.*.md` | `{author}/{project_name}` | 项目文档 |
| `.github/CONTRIBUTING.md` | `{author}/{project_name}` | 贡献指南 |
| `.github/FUNDING.yml` | `{author}` | GitHub Sponsors配置 |
| `docs/content/**/*.md` | `your-username/your-project` | 文档内容 |
| `layouts/_partials/components/analytics/*.html` | 错误信息中的 `{author}.github.io/{project_name}` | Umami/Matomo/GoatCounter 配置提示 |

### 快速替换命令

运行前将命令中的 `YOUR_GITHUB_USER` 和 `YOUR_REPO` 改为你的 GitHub 用户名和仓库名。**配置文件**（go.mod、theme.toml 等）使用 `{author}` / `{project_name}`，**内容**（`docs/content/**/*.md`）使用 `your-username` / `your-project`。两组都需执行。

```bash
# Linux/macOS - 配置文件
find . -type f \( -name "*.yaml" -o -name "*.toml" -o -name "go.mod" \) \
  -exec sed -i 's/{author}/YOUR_GITHUB_USER/g; s/{project_name}/YOUR_REPO/g' {} +
# Linux/macOS - 内容
find ./docs/content -type f -name "*.md" \
  -exec sed -i 's/your-username/YOUR_GITHUB_USER/g; s/your-project/YOUR_REPO/g' {} +
```

```powershell
# PowerShell - 配置文件
Get-ChildItem -Recurse -Include *.yaml,*.toml,go.mod | ForEach-Object { (Get-Content $_) -replace '\{author\}','YOUR_GITHUB_USER' -replace '\{project_name\}','YOUR_REPO' | Set-Content $_ }
# PowerShell - 内容
Get-ChildItem -Path docs/content -Recurse -Include *.md | ForEach-Object { (Get-Content $_) -replace 'your-username','YOUR_GITHUB_USER' -replace 'your-project','YOUR_REPO' | Set-Content $_ }
```

## 快速开始示例

新部署的最小配置：

```yaml {filename="hugo.yaml"}
baseURL: "https://docs.mybusiness.com/"
title: "我的业务文档"

params:
  project:
    name: "我的业务"
    shortName: "MB"
    description: "我的业务产品文档"
    organization: "我的业务公司"
    github: "https://github.com/mybusiness/docs"
    githubEditBase: "https://github.com/mybusiness/docs/edit/main/docs/content"
    website: "https://mybusiness.com"
    currentVersion: "v1.0"
```

然后更新：
1. `menu.main`中的GitHub链接URL（identifier: github）
2. `static/images/`中的logo文件
3. 首页和关于页面内容

## 多部署技巧

1. **维护基础模板** - 保持一个没有业务特定内容的干净版本
2. **使用Git分支** - 为不同部署创建单独的分支
3. **记录更改** - 记录每次部署的自定义内容
4. **自动化设置** - 考虑创建提示输入项目信息的设置脚本
5. **搜索PROJECT_NAME** - 模板使用`PROJECT_NAME`作为占位符；搜索并替换为您的实际项目名称
