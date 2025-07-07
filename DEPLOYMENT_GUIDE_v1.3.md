# MaRu Link v1.3 デプロイメントガイド

## 🚀 デプロイメント概要

MaRu Link v1.3 は企業レベルのセキュリティとコンプライアンスを実装した、完全にプロダクション準備済みのWebサイトです。

### 📦 パッケージ内容

- **maru-link-v1.3.zip** (推奨) - ZIP圧縮版
- **maru-link-v1.3.tar.gz** - TAR.GZ圧縮版
- **deployment-v1.3/** - 展開済みファイル

## 📋 必要なファイル一覧

### メインファイル
- `index.html` - エントリーポイント（自動リダイレクト）
- `matome.html` - メインページ
- `matome-style.css` - 統合スタイルシート

### 法的文書（必須）
- `privacy-policy.html` - プライバシーポリシー
- `disclaimer.html` - 免責事項
- `terms.html` - 利用規約  
- `tokusho.html` - 特定商取引法表記

### 設定ファイル
- `.htaccess` - セキュリティ・パフォーマンス設定
- `robots.txt` - SEO設定
- `sitemap.xml` - サイトマップ

### リソース
- `images/` - 画像ファイルディレクトリ
  - `favicon.png` - サイトアイコン
  - `profile-placeholder.jpg` - プロフィール画像
  - `og-image.svg` - OGP用画像

## 🖥️ デプロイメント手順

### 1. ファイルのアップロード

#### レンタルサーバー（推奨）
```bash
# FTPクライアントまたはファイルマネージャーで
# サーバーのドキュメントルート/link/ に全ファイルをアップロード
/public_html/link/
├── index.html
├── matome.html
├── matome-style.css
├── privacy-policy.html
├── disclaimer.html
├── terms.html
├── tokusho.html
├── .htaccess
├── robots.txt
├── sitemap.xml
└── images/
```

#### GitHub Pages
```bash
# GitHubリポジトリに直接デプロイ済み
# URL: https://maru44448476.github.io/MaRu-link/
```

### 2. URLアクセス確認

#### メインページ
- https://maru-vive.com/link/
- https://maru-vive.com/link/matome.html

#### 法的文書
- https://maru-vive.com/link/privacy-policy.html
- https://maru-vive.com/link/disclaimer.html
- https://maru-vive.com/link/terms.html
- https://maru-vive.com/link/tokusho.html

### 3. 設定ファイル確認

#### .htaccess が有効か確認
```bash
# セキュリティヘッダーが設定されているかチェック
curl -I https://maru-vive.com/link/
```

期待される応答：
- `X-Frame-Options: DENY`
- `X-Content-Type-Options: nosniff`
- `Content-Security-Policy: ...`

## 🛡️ セキュリティ機能

### 自動適用されるセキュリティ
- **XSS Protection** - クロスサイトスクリプティング対策
- **Clickjacking Protection** - クリックジャッキング対策
- **MIME Type Protection** - MIMEタイプスニッフィング対策
- **Content Security Policy** - コンテンツセキュリティポリシー
- **HTTPS Enforcement** - HTTPS強制リダイレクト

### ファイルアクセス制限
- ログファイル・設定ファイルの直接アクセス禁止
- ディレクトリ一覧表示無効化
- 不要なファイル拡張子のアクセス拒否

## 📊 パフォーマンス最適化

### 自動適用される最適化
- **Gzip圧縮** - テキストファイルの圧縮配信
- **ブラウザキャッシュ** - 静的リソースのキャッシュ設定
- **条件付きリクエスト** - 304 Not Modified対応

### 期待されるパフォーマンス
- **ページ読み込み時間**: < 2秒
- **画像最適化**: WebP対応ブラウザで自動最適化
- **CSS/JS圧縮**: 81%圧縮率達成

## ⚖️ 法的コンプライアンス

### 完全対応法令
- ✅ **個人情報保護法** - プライバシーポリシー
- ✅ **特定商取引法** - 事業者情報・返品規定
- ✅ **景品表示法** - 誇大広告防止・免責事項
- ✅ **金融商品取引法** - 投資助言免責・リスク明示
- ✅ **著作権法** - 知的財産権保護

### リスク対策
- 投資関連コンテンツの強力な免責事項
- アフィリエイト収益の透明な開示
- 個人情報取扱いの明確な規定

## 🔧 トラブルシューティング

### よくある問題

#### 1. .htaccess が効かない
```bash
# Apache mod_rewrite が有効か確認
# サーバー管理者に AllowOverride All の設定を依頼
```

#### 2. フォントが表示されない
```bash
# CORS設定確認
# Google Fonts へのアクセスが許可されているか確認
```

#### 3. 画像が表示されない
```bash
# images/ ディレクトリのパーミッション確認
chmod 755 images/
chmod 644 images/*
```

#### 4. 法的文書にアクセスできない
```bash
# ファイルが正しくアップロードされているか確認
ls -la *.html
```

## 📝 デプロイ後の確認リスト

### 機能確認
- [ ] メインページが正常に表示される
- [ ] ローディングアニメーションが動作する
- [ ] 全てのカードリンクが正しく動作する
- [ ] パンダアニメーションが表示される
- [ ] 光る枠線エフェクトが動作する

### 法的文書確認
- [ ] プライバシーポリシーにアクセスできる
- [ ] 免責事項にアクセスできる
- [ ] 利用規約にアクセスできる
- [ ] 特定商取引法表記にアクセスできる
- [ ] フッターから全ての法的文書にアクセスできる

### SEO確認
- [ ] robots.txt にアクセスできる
- [ ] sitemap.xml にアクセスできる
- [ ] OGPメタタグが正しく設定されている
- [ ] 構造化データが有効

### セキュリティ確認
- [ ] HTTPSでアクセスできる
- [ ] セキュリティヘッダーが設定されている
- [ ] 不要なファイルへの直接アクセスが拒否される
- [ ] ディレクトリ一覧が表示されない

## 🎯 デプロイ完了

全ての確認項目をクリアしたら、MaRu Link v1.3 のデプロイが完了です！

企業レベルのセキュリティとコンプライアンスを備えた、プロフェッショナルなリンク集サイトとして運営を開始できます。

---

**デプロイ日**: 2025年7月7日  
**バージョン**: v1.3  
**リリースタグ**: https://github.com/MaRu44448476/MaRu-link/releases/tag/v1.3