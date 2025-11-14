# Welcome to Our GitHub Organization

このサイトは、組織の開発ガイドライン、リポジトリ構成、CI/CD方針をまとめた **Welcomeページ** です。

---

## 🎯 目的
- 開発標準の共有
- 親子リポジトリ構成の理解
- CI/CD自動化の利用方法
- ブランチ戦略・命名規則の確認

---

## 🏗 親子リポジトリ構成
- **親リポジトリ**：プロジェクト単位
  - MkDocsドキュメント
  - GitHub Actions（CI/CD）
  - 子リポジトリをGit Subtreeで取り込み
- **子リポジトリ**：アプリケーション単位
  - 独立管理
  - 親リポジトリにコードを同期

[詳細は architecture.md を参照。](architecture.md)

---

## 🔄 CI/CDフロー
- MkDocs → GitHub Pagesに自動デプロイ
- 子リポジトリ更新 → 親リポジトリに自動反映（GitHub Actions）

[詳細は ci-cd.md を参照。](ci-cd.md)

---

## 📌 開発ルール
- ブランチ作成規則
  - 新規開発：`feature/****`
  - 修正対応：`bugfix/****`
  - 公開準備：`release/****`
  - 緊急対応：`hotfix/****`
- リポジトリ命名規則

[詳細は rules.md を参照。](rules.md)