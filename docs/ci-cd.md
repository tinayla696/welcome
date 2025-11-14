# CI/CD 設定ガイド

本ページでは、GitHub Actionsを利用した **MkDocsによるドキュメント自動デプロイ** と  
**Git Subtreeによる子リポジトリ同期** の設定方法を説明します。

---

## 1. MkDocsによるドキュメント自動デプロイ

### 概要
- 親リポジトリの `docs/` ディレクトリを MkDocsでビルド。
- GitHub Pagesに自動デプロイ。

### ワークフロー例
```yaml
name: Deploy MkDocs to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Setup Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.x'

      - name: Install dependencies
        run: |
          pip install mkdocs mkdocs-material

      - name: Build and Deploy
        run: |
          mkdocs build
```

---

## 2. 子リポジトリ同期（Git Subtree）

### 概要

- 複数の子リポジトリを親リポジトリに取り込み。
- 定期的に同期することで、親リポジトリを最新状態に保つ。

### ワークフロー例
```yaml
name: Sync Subtree Repositories

on:
  schedule:
    - cron: '0 3 * * *' # 毎日午前3時に実行
  workflow_dispatch: # 手動実行も可能

jobs:
  sync-subtrees:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout parent repository
        uses: actions/checkout@v3
        with:
          fetch-depth: 0 # subtree操作には完全な履歴が必要

      - name: Configure Git
        run: |
          git config user.name "github-actions[bot]"
          git config user.email "github-actions[bot]@users.noreply.github.com"

      - name: Sync child repositories
        run: |
          declare -A repos=(
            ["app1"]="https://github.com/org/app1-repo.git"
            ["app2"]="https://github.com/org/app2-repo.git"
          )

          for prefix in "${!repos[@]}"; do
            url="${repos[$prefix]}"
            echo "Syncing $prefix from $url"
            git subtree pull --prefix="$prefix" "$url" main --squash
          done

      - name: Push changes
        run: |
          git push origin main
```

---

### ポイント

- MkDocsデプロイ： `mkdocs gh-deploy`でGitHub Pagesに公開。
- Subtree同期： `git subtree pull` で子リポジトリを親に取り込み。
- 複数子リポジトリ対応： `declare -A repos` で管理。
- 定期実行： `cron` で自動化、workflow_dispatchで手動実行も可能。

---

### 関連ページ

- [親子リポジトリ構成](architecture.md)
- [開発ルール](rules.md)