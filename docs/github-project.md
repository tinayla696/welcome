# GitHub Project 設定ガイド

GitHub Projectは、親リポジトリ単位でタスク管理を行うためのツールです。  
本ガイドでは、プロジェクトの作成、設定、運用のベストプラクティスを説明します。

---

## 1. プロジェクトの目的
- 親リポジトリを軸に開発タスクを管理。
- IssueやPull Requestと連携し、進捗を可視化。
- 複数子リポジトリを含むプロジェクト全体の管理を効率化。

---

## 2. プロジェクト作成手順
1. GitHub Organizationで **Projects** を開く。
2. 「New Project」をクリック。
3. プロジェクト名を設定（例: `Vehicle System Project`）。
4. 親リポジトリをプロジェクトにリンク。

---

## 3. ビュー設定
- **Boardビュー**: カンバン形式でタスク管理。
- **Tableビュー**: IssueやPRを一覧で管理。
- **Timelineビュー**: スケジュール管理。

---

## 4. カラム構成例（Boardビュー）
- **Backlog**: 未着手タスク。
- **In Progress**: 開発中。
- **Review**: PRレビュー中。
- **Done**: 完了。

---

## 5. 自動化設定
- Issue作成時に自動で「Backlog」に追加。
- PR作成時に「Review」に移動。
- マージ後に「Done」に移動。

---

## 6. ベストプラクティス
- **親リポジトリのIssueを中心に管理**。
- 子リポジトリのIssueは親プロジェクトにリンク。
- ラベルを統一（例: `feature`, `bugfix`, `release`, `hotfix`）。
- 定期的に進捗レビューを実施。

---

## 関連ページ
- [architecture.md](architecture.md)
- [rules.md](rules.md)
- [ci-cd.md](ci-cd.md)