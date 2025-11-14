# 開発ルール

本ページでは、リポジトリのブランチ戦略、命名規則、Pull Requestルートを定義します。

---

## 1. ブランチ作成ルール

### 基本ブランチ
- **main**: 本番リリース用。
- **develop**: 開発の基盤ブランチ。

### 作業ブランチ命名規則
- 新規開発: `feature/<機能名>`
- 修正対応: `bugfix/<修正内容>`
- 公開準備: `release/<バージョン>`
- 緊急対応: `hotfix/<修正内容>`

**例:**

```text
feature/add-login
bugfix/fix-api-timeout
release/1.0.0
hotfix/security-patch
```

---

## 2. 開発フロー
1. リポジトリのクローンは `develop` ブランチから開始。
2. 作業ブランチを作成し、開発を実施。
3. 作業完了後、Pull Requestを作成し、`develop` にマージ。
4. リリース時に `develop` → `main` へマージ。

---

## 3. リポジトリ命名規則

**意味:**
- `<your-id>`: 開発者やチームの識別子。
- `<parent-repo>`: プロジェクト単位の親リポジトリ名。
- `<children-repo>`: アプリケーションやモジュール単位の子リポジトリ名。

**例:**

```text
team-a/vehicle-system
team-a/vehicle-system/gst_recording_py
team-a/vehicle-system/data_logger_go
```

---

## 4. Pull Requestルート
- **子リポジトリ**: 子リポジトリ内でPRを作成し、レビュー後にマージ。
- **親リポジトリ**: 子リポジトリの更新を取り込んだ後、親リポジトリでPRを作成。

### PRルール
- 必須レビュー: 2名以上。
- CIチェック: 成功必須。
- PRテンプレートを利用。

---

## 5. コードレビューの基本方針
- 可読性、保守性、セキュリティを重視。
- コメントは具体的かつ建設的に。