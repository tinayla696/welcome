# プロジェクト構成アーキテクチャ

## 概要
本プロジェクトは、GitHub Organizationを基盤とし、親子リポジトリ構成を採用します。  
親リポジトリはプロジェクト単位で管理し、  
複数の子リポジトリ（アプリケーションやモジュール）を **Git Subtree** により取り込みます。  
CI/CDは **GitHub Actions** を利用し、  
MkDocsによるドキュメント自動デプロイと子リポジトリ同期を実現します。

---

## 構成図

![chitecture.png](assets/architecture.png)

---

## 詳細構成

### **GitHub Organization**
- 全体の管理単位。
- 各プロジェクトは親リポジトリとして管理。

### **GitHub Project**
- 親リポジトリ単位でタスク管理。
- IssueやPull Requestを連携。

### **親リポジトリ**
- **docs/**: MkDocsによる開発ドキュメント。
- **appX/**: 子リポジトリをGit Subtreeで取り込み。
- **.github/workflows/**:
  - `mkdocs-deploy.yml`: MkDocsをGitHub Pagesへデプロイ。
  - `subtree-sync.yml`: 子リポジトリの同期を自動化。

### **子リポジトリ群**
- 独立管理されるアプリケーションやモジュール。
- 親リポジトリにGit Subtreeで取り込まれる。

---

## ブランチ作成ルール
- 新規開発：`feature/****`
- 修正対応：`bugfix/****`
- 公開準備：`release/****`
- 緊急対応：`hotfix/****`

**開発フロー**  
- クローンは `develop` ブランチから開始。
- 作業完了後、Pull Requestで `develop` にマージ。

---

## リポジトリ命名規則

```text
<your-id>/<parent-repo>/<children-repo>
```

### 意味

- <your-id>：開発者やチームの識別子（例: team-a）。
- <parent-repo>：プロジェクト単位の親リポジトリ名（例: vehicle-system）。
- <children-repo>：アプリケーションやモジュール単位の子リポジトリ名（例: camera-module）。

### 例

```text
team-a/vehicle-system
team-a/vehicle-system/gst_recording_py
team-a/vehicle-system/data_logger_go
```

---

## CI/CDフロー
1. **MkDocsデプロイ**  
   - 親リポジトリの `docs/` → GitHub Actions → GitHub Pages。
2. **子リポジトリ同期**  
   - GitHub Actionsで `git subtree pull` を定期実行。

---

## 関連ページ

- [index.md](index.md): ウェルカムページと概要。
- [ci-cd.md](ci-cd.md): CI/CDフローの詳細。
- [rules.md](rules.md): ブランチ戦略・命名規則の詳細。