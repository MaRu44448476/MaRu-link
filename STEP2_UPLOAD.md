# ステップ2: サーバーにアップロード

## 🤔 **まず確認すること**

### **maru-vive.com のサーバー管理方法は？**
以下のどれに該当しますか？

1. **レンタルサーバー（さくら、ロリポップ、Xserver等）**
   → cPanelまたはWebコントロールパネルあり

2. **WordPress管理画面のみ**
   → ファイルマネージャープラグインが必要

3. **FTP情報を持っている**
   → FileZilla等のFTPソフトを使用

4. **サーバー管理会社に依頼**
   → 管理会社にファイルを渡してアップロード依頼

---

## 🔧 **方法1: cPanel/Webコントロールパネル**

### **手順**
1. **管理画面にログイン**
   - サーバー会社から提供されたURL
   - 例: `https://maru-vive.com:2083` または `https://control.maru-vive.com`

2. **ファイルマネージャーを開く**
   - cPanelの場合：「ファイルマネージャー」アイコンをクリック
   - 他の場合：「ファイル管理」「Webファイル」等を探す

3. **public_htmlフォルダに移動**
   - 通常は最初に`public_html`フォルダが表示される
   - 表示されない場合は`public_html`をダブルクリック

4. **linkフォルダを作成**
   - 「新しいフォルダ」または「フォルダ作成」をクリック
   - フォルダ名: `link` (小文字)

5. **linkフォルダに移動**
   - 作成した`link`フォルダをダブルクリック

6. **ファイルをアップロード**
   - 「ファイルアップロード」または「アップロード」ボタンをクリック
   - 以下のファイルを1つずつアップロード：
     - `index.html`
     - `matome.html`
     - `matome-style.css`

7. **imagesフォルダをアップロード**
   - 「フォルダアップロード」または「フォルダごとアップロード」
   - `images`フォルダ全体を選択
   - または`images`フォルダを作成してファイルを個別アップロード

---

## 🔧 **方法2: FTPソフト（FileZilla）**

### **事前準備**
1. **FileZillaをダウンロード・インストール**
   - https://filezilla-project.org/
   - 無料のFTPソフト

2. **FTP接続情報を確認**
   - サーバー会社から提供された情報：
     - FTPサーバー: `ftp.maru-vive.com` 等
     - ユーザー名: 通常はドメイン名またはユーザーID
     - パスワード: 設定したパスワード
     - ポート: 通常は21（またはSFTPの場合22）

### **接続手順**
1. **FileZillaを起動**

2. **接続情報を入力**
   - ホスト: `ftp.maru-vive.com`
   - ユーザー名: （サーバー会社提供）
   - パスワード: （設定したもの）
   - ポート: 21

3. **接続ボタンをクリック**

4. **public_htmlフォルダに移動**
   - 右側（サーバー側）で`public_html`をダブルクリック

5. **linkフォルダを作成**
   - 右側で右クリック → 「ディレクトリの作成」
   - 名前: `link`

6. **linkフォルダに移動**
   - 作成した`link`フォルダをダブルクリック

7. **ファイルをドラッグ&ドロップ**
   - 左側（PC側）でダウンロードしたファイルを選択
   - 右側（サーバー側）にドラッグ&ドロップ

---

## 🔧 **方法3: 管理会社に依頼**

### **依頼内容のテンプレート**
```
件名: ウェブサイトファイルのアップロード依頼

お世話になっております。
maru-vive.com のファイルアップロードをお願いします。

【アップロード先】
https://maru-vive.com/link/

【ファイル一覧】
- index.html
- matome.html  
- matome-style.css
- images/favicon.png
- images/og-image.svg
- images/profile-placeholder.jpg

【ディレクトリ構造】
/link/
├── index.html
├── matome.html
├── matome-style.css  
└── images/
    ├── favicon.png
    ├── og-image.svg
    └── profile-placeholder.jpg

ファイルは添付またはファイル転送サービスでお送りします。
よろしくお願いいたします。
```