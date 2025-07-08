# MaRu-link デプロイメント トラブルシューティングガイド v2.0

最終更新: 2025-07-07

---

## プロジェクト構成の理解

### リポジトリの役割分担
| リポジトリ | 役割 | 用途 |
|---|---|---|
| **MaRu-link** | 開発環境 (Development) | 新機能開発・テスト・実験 |
| **MaRu-portfolio-site** | 本番環境 (Production) | 実際のサイト運用・GitHub Pages |

### 重要な注意点
⚠️ **MaRu-link で開発しただけでは本番サイトは更新されません！**

---

## 正しいデプロイメント手順

### 1. 開発フェーズ (MaRu-link)
```bash
cd /home/wiwcw/MaRu-link
# ファイルを編集・更新
git add .
git commit -m "Update features"
git push origin main
```

### 2. 本番反映フェーズ (MaRu-portfolio-site)
```bash
cd /home/wiwcw/MaRu-portfolio-site

# 最新の開発版を本番環境にコピー
cp -r /home/wiwcw/MaRu-link/link/* ./link/

# 変更をステージング
git add link/

# コミット
git commit -m "Deploy latest version from MaRu-link development"

# プッシュ
git push origin main
```

---

## よくあるエラーと解決方法

### 1. サイトが更新されない
**症状**: `https://maru-vive.com/link/` が古いバージョンのまま

**原因**: 開発環境 (MaRu-link) だけ更新して本番環境に反映していない

**解決策**:
```bash
# 本番環境に最新ファイルをコピー
cd /home/wiwcw/MaRu-portfolio-site
cp -r /home/wiwcw/MaRu-link/link/* ./link/
git add link/ && git commit -m "Update from dev" && git push origin main
```

### 2. Jekyll ビルドエラー
**症状**: GitHub Actions でビルドが失敗

**よくある原因**:
- SCSS インポートパスの間違い
- 存在しないファイルの参照
- Jekyll 設定の問題

**解決策**:
```bash
# ローカルでビルドテスト
bundle exec jekyll build

# エラーが出た場合、ログを確認して修正
# 例: SCSS インポートパス修正
@import '../../_sass/simple';  # ❌ 間違い
@import 'simple';              # ✅ 正解
```

### 3. キャッシュ問題
**症状**: コミットしたのにサイトが更新されない

**解決策**:
```bash
# 空コミットで強制更新
git commit --allow-empty -m "Force GitHub Pages cache refresh"
git push origin main
```

---

## トラブルシューティング チェックリスト

### 更新が反映されない場合
- [ ] 正しいリポジトリ (`MaRu-portfolio-site`) で作業しているか？
- [ ] 開発版 (`MaRu-link`) から本番版にファイルをコピーしたか？
- [ ] GitHub Actions でビルドエラーが発生していないか？
- [ ] ブラウザキャッシュをクリアしたか？ (`Ctrl+Shift+R`)

### GitHub Actions ビルドエラーの場合
- [ ] Jekyll のローカルビルドは成功するか？ (`bundle exec jekyll build`)
- [ ] SCSS/CSS のインポートパスは正しいか？
- [ ] 存在しないファイルを参照していないか？
- [ ] `_config.yml` の設定は正しいか？

---

## ワークフロー図

```
開発環境 (MaRu-link)
    ↓ 開発・テスト
    ↓ git commit & push
    ↓
本番環境 (MaRu-portfolio-site)
    ↓ ファイルコピー
    ↓ git commit & push
    ↓
GitHub Pages
    ↓ Jekyll ビルド
    ↓
https://maru-vive.com/link/ 🚀
```

---

## コマンドテンプレート

### 開発から本番への完全デプロイ
```bash
#!/bin/bash
# 本番環境に移動
cd /home/wiwcw/MaRu-portfolio-site

# 最新の開発版を取得
git pull origin main

# 開発版から本番版にファイルコピー
cp -r /home/wiwcw/MaRu-link/link/* ./link/

# Jekyll ローカルビルドテスト
bundle exec jekyll build

# エラーがなければデプロイ
git add link/
git commit -m "Deploy latest version: $(date +'%Y-%m-%d %H:%M')"
git push origin main

echo "✅ デプロイ完了！5-10分後にサイトが更新されます。"
```

---

## 緊急時の対応

### サイトが完全に動かない場合
```bash
# 前のバージョンに戻す
git log --oneline -10  # コミット履歴を確認
git revert <コミットハッシュ>  # 問題のあるコミットを取り消し
git push origin main
```

### Jekyll ビルドが完全に壊れた場合
```bash
# Gemfile.lock を再生成
rm Gemfile.lock
bundle install
bundle exec jekyll build
```

---

## 予防策

### 1. 定期的なバックアップ
- 重要な更新前は必ずバックアップを作成
- タグ付けでバージョン管理 (`git tag -a v1.4 -m "Version 1.4"`)

### 2. ローカルテスト
- 本番プッシュ前に必ず `bundle exec jekyll build` でテスト
- ローカル環境で動作確認 (`bundle exec jekyll serve`)

### 3. 段階的デプロイ
- 大きな変更は小さな単位に分けてコミット
- 一度に多くのファイルを変更しない

---

## 問い合わせ先

このガイドで解決しない場合:
1. GitHub Actions のログを確認
2. Jekyll のエラーメッセージを詳しく読む
3. 該当するコミットハッシュとエラー内容をメモする

---

> 💡 **覚えておくべきポイント**: 開発環境で更新しただけでは本番サイトは更新されません！必ず `MaRu-portfolio-site` に反映してください。