# Welcome to Our GitHub Organization

このリポジトリは、組織の開発ガイドライン、リポジトリ構成、CI/CD方針をまとめた **Welcomeリポジトリ** です。

## ディレクトリ構成

```tree
welcome-repo/
├── docs/
│   ├── index.md           # トップページ
│   ├── architecture.md    # 親子リポジトリ構成
│   ├── ci-cd.md           # GitHub Actions設定例
│   └── rules.md           # ブランチ戦略・命名規則
├── mkdocs.yml             # MkDocs設定
├── README.md              # リポジトリ概要
└── .github/workflows/
    └── mkdocs-deploy.yml  # GitHub Pagesデプロイ用Actions
```

## 📚 内容
- **Architecture**: 親子リポジトリ構成（Git Subtree利用）
- **CI/CD**: GitHub Actionsによる自動化（MkDocsデプロイ、Subtree同期）
- **Rules**: ブランチ戦略、命名規則、Pull Requestルート

## 🌐 ドキュメント
GitHub Pagesで公開されます（自動デプロイ）。


---

## 🖥 スタンドアロンでの利用方法（ローカル確認）
MkDocsをローカルで起動してドキュメントを確認できます。

### 手順
```bash
# 仮想環境を作成
python -m venv .venv

# 仮想環境を有効化
source .venv/bin/activate   # macOS/Linux
# Windowsの場合: .venv\Scripts\activate

# 必要なパッケージをインストール
pip install -r requirements.txt

# MkDocsサーバーを起動
mkdocs serve

# ブラウザで http://localhost:8000 を開く
```
