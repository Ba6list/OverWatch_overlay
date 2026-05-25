JOWS Overlay UI - Cloudinary版 セットアップメモ

入っているファイル
- login.html
- control.html
- settings.html
- overlay.html
- firebase-rules.txt

GitHub Pagesで試す手順
1. 新しいGitHubリポジトリを作成
2. このZIP内のファイルをそのリポジトリに配置
3. 既存の UI / icon / JOWS.png などの画像素材フォルダも同じ階層に配置
4. settings.html内のCloudinary設定を変更
5. GitHub Pagesを有効化
6. login.htmlへアクセス

settings.htmlで必ず変更する箇所

const cloudinaryCloudName = "YOUR_CLOUD_NAME";
const cloudinaryUploadPreset = "YOUR_UNSIGNED_UPLOAD_PRESET";

例:

const cloudinaryCloudName = "abc123";
const cloudinaryUploadPreset = "Team_logo";

Firebase側で必要な設定
- Authentication: メール/パスワードを有効化
- Authentication: GitHub Pagesのドメインを承認済みドメインに追加
- Firestore Rules: firebase-rules.txt の Firestore Rules を貼り付け

Firebase Storageは使いません。
チームロゴはCloudinaryに保存し、Firestoreには画像URLだけ保存します。

Cloudinary側の設定
- Upload preset name: Team_logo
- Mode: Unsigned
- Overwrite: false
- Asset folder: 任意。例 overlay/Team_logo

OBS用URL
管理画面 control.html にログイン後、「配信用URLコピー」ボタンから取得します。
overlay.html?uid=... の形になります。
