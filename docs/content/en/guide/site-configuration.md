---
title: Site Config
linkTitle: Site Config
weight: 9
---

This guide explains how to configure this documentation site for your business or project. All project-specific information is centralized in a single configuration file, making it easy to rebrand and deploy for different organizations.

<!--more-->

## Overview

When deploying this documentation template for a new business, you need to update project metadata such as:
- Project/product name
- Description and tagline
- GitHub repository URL
- Logo and branding assets
- Contact and social links

All these settings are centralized in **one file**: `hugo.yaml`.

**Config file location:** In this repository structure, the main config file is **`docs/hugo.yaml`** when you run Hugo with `--source=docs` (e.g. `npm run dev:theme`). All paths in this guide refer to that file unless noted.

## Configuration File Structure

Open `hugo.yaml` (i.e. `docs/hugo.yaml`) and locate the `params.project` section. This is the **single source of truth** for all project metadata:

```yaml {filename="hugo.yaml"}
params:
  project:
    # Core identity
    name: "Your Project Name"                         # Project/product name
    shortName: "YPN"                                  # Short name for compact displays
    tagline: "Your Awesome Tagline"                   # Brief tagline/slogan
    
    # Descriptions
    description: "Full description of your project for SEO and meta tags."
    shortDescription: "Brief description for hero sections"
    
    # Organization/Author info
    author: "Your Name"
    organization: "Your Organization"
    email: "contact@example.com"
    
    # Links
    website: "https://your-website.com"
    github: "https://github.com/your-org/your-repo"
    githubEditBase: "https://github.com/your-org/your-repo/edit/main/docs/content"
    
    # Social links (optional - leave empty if not used)
    twitter: "https://twitter.com/yourhandle"
    discord: "https://discord.gg/yourserver"
    
    # Branding
    logo: "images/logo.svg"
    logoDark: "images/logo-dark.svg"
    
    # Version info
    currentVersion: "v1.0"
    
    # License
    license: "MIT"
    licenseUrl: "https://github.com/your-org/your-repo/blob/main/LICENSE"
```

## Step-by-Step Configuration

Follow these steps to configure the site for your business:

{{< steps >}}

### Update Base Settings

At the top of `hugo.yaml`, update:

```yaml {filename="hugo.yaml"}
baseURL: "https://docs.your-domain.com/"
title: "Your Project Name"
```

### Update Project Info

In the `params.project` section, update all fields with your business information:

| Field | Description | Example |
|-------|-------------|---------|
| `name` | Full project name | "My Product" |
| `shortName` | Abbreviated name | "MP" |
| `tagline` | Brief slogan | "Build faster, ship smarter" |
| `description` | Full description for SEO | "Complete documentation for..." |
| `author` | Author or team name | "DevTeam" |
| `organization` | Company/org name | "Acme Inc" |
| `github` | Repository URL | "https://github.com/acme/docs" |

### Update Language Titles

For each language in the `languages` section, update the `title`:

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

### Update Menu Links

Update the GitHub link in the main menu:

```yaml {filename="hugo.yaml"}
menu:
  main:
    - identifier: github
      name: GitHub
      url: "https://github.com/your-org/your-repo"
      params:
        icon: github
```

**Menu labels (Products, Versions, Showcase, Blog, Guide):** These are translated via **i18n**. To change the text shown in the header/navbar, edit the keys `products`, `versions`, `showcase`, `blog`, `guide`, `more` in each `i18n/*.yaml` file (e.g. `i18n/en.yaml`, `i18n/vi.yaml`).

### Update Edit URL

Update the base URL for the "Edit this page" feature:

```yaml {filename="hugo.yaml"}
params:
  editURL:
    base: "https://github.com/your-org/your-repo/edit/main/docs/content"
```

### Replace Branding Assets

Replace these files in `static/images/`:

| File | Purpose | Recommended Size |
|------|---------|------------------|
| `logo.svg` | Light mode logo | Height: 32-40px |
| `logo-dark.svg` | Dark mode logo | Height: 32-40px |
| `favicon.ico` | Browser favicon | 32x32px |

### Configure Comments (Optional)

If using Giscus for comments, update the repository settings:

```yaml {filename="hugo.yaml"}
params:
  comments:
    enable: true
    type: giscus
    giscus:
      repo: your-org/your-repo
      repoId: YOUR_REPO_ID
      category: General
      categoryId: YOUR_CATEGORY_ID
```

Visit [giscus.app](https://giscus.app/) to generate these values.

### Update Content

Update the main content pages:
- Homepage: `content/{lang}/_index.md`
- About page: `content/{lang}/about/index.md`
- Product documentation structure

{{< /steps >}}

## Using Project Info in Content

You can dynamically display project information in your content using shortcodes:

### Display Project Values

```markdown
Welcome to {{</* project "name" */>}}!

{{</* project "description" */>}}

Current version: {{</* project "currentVersion" */>}}
```

**Available fields:**
- `name`, `shortName`, `tagline`
- `description`, `shortDescription`
- `author`, `organization`, `email`
- `website`, `github`
- `currentVersion`, `license`, `licenseUrl`
- `twitter`, `discord`

### Create Links

```markdown
Check out our {{</* project-link "github" */>}}

Visit the {{</* project-link "website" "official website" */>}}

Licensed under {{</* project-link "license" */>}}
```

## Recommended Rebrand Order

Follow this order to avoid missing steps:

1. **Config** — `hugo.yaml`: `baseURL`, `title`, `params.project.*`, `languages.*.title`, `menu.main` (GitHub), `params.editURL.base`, `theme` (if you renamed the theme folder).
2. **i18n** — In **every** file in `i18n/*.yaml` (en, vi, ja, zh-cn, fa, de, fr, …): `copyright`, `poweredBy`, and menu keys (`products`, `versions`, `showcase`, etc.) if you need translated labels.
3. **Branding** — Replace `static/images/` logo and favicon.
4. **Banners** — Update `languages.<lang>.params.banner.message` in `hugo.yaml` for each language (see [Banner messages](#banner-messages-per-language) below).
5. **Content** — Homepage, About, and search/replace **PROJECT_NAME** in all content (front matter and body).
6. **Placeholders** — Replace GitHub URL placeholders (`{author}`, `{project_name}`, `your-username`, `your-project`) in the files listed in [Replacing GitHub URL Placeholders](#replacing-github-url-placeholders).

## Configuration Checklist

Use this checklist when setting up for a new business:

| Item | Location | Status |
|------|----------|--------|
| Base URL | `hugo.yaml` → `baseURL` | ☐ |
| Site title | `hugo.yaml` → `title` | ☐ |
| Project info | `hugo.yaml` → `params.project.*` | ☐ |
| Language titles | `hugo.yaml` → `languages.*.title` | ☐ |
| Theme key (if theme folder renamed) | `hugo.yaml` → `theme` | ☐ |
| GitHub menu link | `hugo.yaml` → `menu.main` | ☐ |
| Edit URL | `hugo.yaml` → `params.editURL.base` | ☐ |
| Logo files | `static/images/logo*.svg` | ☐ |
| Favicon | `static/images/favicon.ico` | ☐ |
| i18n: copyright & poweredBy | **All** `i18n/*.yaml` (en, vi, ja, zh-cn, fa, …) | ☐ |
| Banner messages | `hugo.yaml` → `languages.*.params.banner.message` | ☐ |
| Homepage content | `content/*/\_index.md` | ☐ |
| About page | `content/*/about/index.md` | ☐ |
| Replace PROJECT_NAME | All content (front matter + body) | ☐ |
| Giscus config (if used) | `hugo.yaml` → `params.comments.giscus` | ☐ |

## Theme Key

In `hugo.yaml` you will see `theme: hextra`. This is the **theme folder name** Hugo loads.

- **If you use this repo as-is** (theme in a subfolder named `hextra`), leave it as `theme: hextra`.
- **If you copy or rename the theme folder** (e.g. to `mytheme`), set `theme: mytheme` so Hugo loads the correct layout.

## Banner Messages (per language)

The top-of-page banner text is set **per language** in `hugo.yaml` under `languages.<lang>.params.banner.message`. Update each language you use:

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

To disable the banner for a language, remove the `params.banner` block or set `message` to an empty string.

## Files Requiring Manual Updates

Some files cannot use dynamic configuration and must be updated manually:

| File | What to Change |
|------|----------------|
| `go.mod` | Module path (if using Hugo Modules) |
| `README.md` | Project description and badges |
| `LICENSE` | License text if changing license type |
| `hugo.yaml` → `theme` | Set to your theme folder name if you renamed it |
| Content front matter & body | Page titles and any **PROJECT_NAME** text in content |
| Banner messages | `hugo.yaml` → `languages.<lang>.params.banner.message` (see above) |

## Replacing GitHub URL Placeholders

The template uses placeholder values for GitHub URLs throughout the codebase:
- **In documentation content**: `your-username` and `your-project` (human-readable)
- **In config files**: `{author}` and `{project_name}` (for automated replacement)

When forking this theme for your project, you need to replace these placeholders with your actual GitHub username and repository name.

### Search and Replace

Use your editor's find-and-replace feature to update:

| Placeholder | Replace With | Example |
|-------------|--------------|---------|
| `your-username` | Your GitHub username | `mycompany` |
| `your-project` | Your repository name | `my-docs` |
| `{author}` | Your GitHub username | `mycompany` |
| `{project_name}` | Your repository name | `my-docs` |

### Files Containing Placeholders

These files contain GitHub URL placeholders that need updating:

| File | Placeholder Format | Purpose |
|------|-------------------|---------|
| `go.mod` | `{author}/{project_name}` | Go module path |
| `docs/go.mod` | `{author}/{project_name}` | Docs module path |
| `theme.toml` | `{author}/{project_name}` | Theme metadata |
| `README.md`, `README.*.md` | `{author}/{project_name}` | Project documentation |
| `.github/CONTRIBUTING.md` | `{author}/{project_name}` | Contribution guide |
| `.github/FUNDING.yml` | `{author}` | GitHub Sponsors config |
| `docs/content/**/*.md` | `your-username/your-project` | Documentation content |
| `layouts/_partials/components/analytics/*.html` | `{author}.github.io/{project_name}` in error messages | Umami, Matomo, GoatCounter config hints |

### Quick Replace Commands

Before running: replace `YOUR_GITHUB_USER` and `YOUR_REPO` in the commands with your real GitHub username and repository name.

**Config files** (go.mod, theme.toml, etc.) use `{author}` and `{project_name}`. **Content files** (`docs/content/**/*.md`) use `your-username` and `your-project`. Run both:

```bash
# Linux/macOS - Config files ({author} → your value)
find . -type f \( -name "*.yaml" -o -name "*.toml" -o -name "go.mod" \) \
  -exec sed -i 's/{author}/YOUR_GITHUB_USER/g; s/{project_name}/YOUR_REPO/g' {} +

# Linux/macOS - Content files (your-username/your-project → your value)
find ./docs/content -type f -name "*.md" \
  -exec sed -i 's/your-username/YOUR_GITHUB_USER/g; s/your-project/YOUR_REPO/g' {} +
```

```powershell
# Windows PowerShell - Config files
Get-ChildItem -Recurse -Include *.yaml,*.toml,go.mod | 
  ForEach-Object { (Get-Content $_) -replace '\{author\}','YOUR_GITHUB_USER' -replace '\{project_name\}','YOUR_REPO' | Set-Content $_ }

# Windows PowerShell - Content files
Get-ChildItem -Path docs/content -Recurse -Include *.md |
  ForEach-Object { (Get-Content $_) -replace 'your-username','YOUR_GITHUB_USER' -replace 'your-project','YOUR_REPO' | Set-Content $_ }
```

## Quick Start Example

Minimum configuration for a new deployment:

```yaml {filename="hugo.yaml"}
baseURL: "https://docs.mybusiness.com/"
title: "My Business Docs"

params:
  project:
    name: "My Business"
    shortName: "MB"
    description: "Documentation for My Business products"
    organization: "My Business Inc"
    github: "https://github.com/mybusiness/docs"
    githubEditBase: "https://github.com/mybusiness/docs/edit/main/docs/content"
    website: "https://mybusiness.com"
    currentVersion: "v1.0"
```

Then update:
1. GitHub menu link URL in `menu.main` (identifier: github)
2. Logo files in `static/images/`
3. Homepage and About page content

## Tips for Multi-Deployment Use

1. **Maintain a base template** - Keep a clean version without business-specific content
2. **Use Git branches** - Create separate branches for different deployments
3. **Document changes** - Keep notes on what was customized for each deployment
4. **Automate setup** - Consider creating a setup script that prompts for project info
5. **Search for PROJECT_NAME** - The template uses `PROJECT_NAME` as a placeholder; search and replace it with your actual project name
