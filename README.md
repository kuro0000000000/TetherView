# TetherView — 公式サイト

このフォルダは [GitHub Pages](https://docs.github.com/ja/pages) で配信される TetherView の公式サイト・ダウンロード配布ページです。

> **TetherView** は USB ケーブル 1 本で Android タブレットを Windows PC の拡張ディスプレイにできるツールです。

## ⚙️ 公開設定 (GitHub Pages)

1. このフォルダを GitHub リポジトリのルート（または `/docs` フォルダ）に push します。
2. GitHub のリポジトリ Settings → **Pages** → **Source** で「Deploy from a branch」を選択。
3. Branch: `main`(or `master`) / Folder: `/ (root)` または `/docs` を選択。
4. 数分後に `https://<username>.github.io/<repository>/` で公開されます。

独自ドメインを使う場合は同フォルダ内の `CNAME` ファイルにドメイン名を 1 行だけ記載してください。

## 📂 ファイル構成

| パス | 役割 |
|---|---|
| `index.html`                                   | ランディングページ (特長 / 動作イメージ / 動作環境) |
| `usage.html`                                   | 利用手順 (3 ステップ + トラブルシューティング) |
| `downloads.html`                               | Windows MSI と Android (Google Play) のダウンロード |
| `license.html`                                 | ライセンスと料金 (Windows 無料 / Android 課金) |
| `404.html`                                     | 404 ページ |
| `assets/icon.png`                              | アプリアイコン (1024 × 1024) |
| `assets/style.css`                             | サイト全体のスタイルシート |
| `assets/screenshots/demo_app_main.png`         | ① Windows メイン画面 |
| `assets/screenshots/demo_display_settings.png` | ② 「接続」中の画面イメージ |
| `assets/screenshots/demo_browser_extended.png` | ③ 「拡張ディスプレイとして追加」の動作 |
| `downloads/TetherView-1.0.0-x64.msi`           | Windows MSI インストーラー (44 MB) |
| `.nojekyll`                                    | GitHub Pages の Jekyll 処理を無効化 |
| `CNAME`                                        | (任意) 独自ドメイン設定 |

## 🔁 MSI 更新方法

新しい Windows ビルドができたら次の手順で差し替えます：

```powershell
Copy-Item `
  "C:\TetherView\windows\Installer\output\TetherView-1.0.0-x64.msi" `
  "C:\TetherView\GitHub Pages\downloads\TetherView-1.0.0-x64.msi" -Force
```

その後 `git add downloads/TetherView-1.0.0-x64.msi && git commit -m "Update Windows installer to vX.X.X" && git push` で配信されます。

## 📜 ライセンス概要

- **Windows 版**: 無料（個人利用）
- **Android 版**: 買い切り（初回 3 回まで無料、4 回目から課金）
- **同梱ドライバー (MttVDD)**: GPL-3.0
- 詳細は [`license.html`](license.html) を参照。

## 💻 ローカル確認

`index.html` をブラウザで直接開けば全ページが動作確認できます。Live サーバーで見たい場合：

```powershell
# Python 3 系がインストール済みの場合
cd "C:\TetherView\GitHub Pages"
python -m http.server 8000
# → http://localhost:8000/ で閲覧
```

## 🛠 開発者向け

- ソースコード: 別リポジトリ (`/windows`, `/android`)
- 本ページは静的 HTML のみ。ビルドプロセス不要。
- 改修時は `index.html` / `usage.html` 等を直接編集してください。
