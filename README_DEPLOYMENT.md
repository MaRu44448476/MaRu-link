# MaRu Link - サブディレクトリ配置手順

## 📁 https://maru-vive.com/link/ への配置方法

### 1. ファイルのアップロード
サーバーの `/link/` ディレクトリに以下のファイルをアップロード：

```
/link/
├── index.html           # リダイレクト用
├── matome.html         # メインページ
├── matome-style.css    # スタイルシート
└── images/
    ├── favicon.png     # パンダファビコン
    ├── og-image.svg    # OGP画像
    └── profile-placeholder.jpg
```

### 2. 必要なサーバー設定
- DirectoryIndex: index.html
- MIME types: .css, .png, .svg, .jpg
- HTTPS リダイレクト推奨

### 3. アクセスURL
- メイン: https://maru-vive.com/link/
- 直接: https://maru-vive.com/link/matome.html

### 4. 動作確認項目
- ✅ ページの表示
- ✅ パンダファビコンの表示
- ✅ パンダアニメーション
- ✅ レスポンシブデザイン
- ✅ OGPメタデータ

## 📋 注意点
- 相対パス使用のため、ディレクトリ構造を維持
- 画像パスは絶対URL（SEO/OGP用）
- HTTPSでのアクセス推奨