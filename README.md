# project-tyrano

TyranoScript で作成したゲームをローカルで動作確認するためのリポジトリです。

## 公開版

ゲームは [GitHub Pages](https://dev-creatives.github.io/project-tyrano/) で遊べます。`main` ブランチへの push 時に自動で更新されます。GitHub Actions の "Deploy GitHub Pages" workflow は、Actions 画面から手動実行することもできます。

## 必要なもの

Node.js `24.20.0` と pnpm `12.3.2` が必要です。

[mise](https://mise.jdx.dev/) を使うと、`mise.toml` に定義されたこれらのバージョンを自動的に導入・管理できます。mise を使わない場合は、Node.js と pnpm をそれぞれインストールしてください。

## 起動方法

### mise を使う場合

```sh
mise install
pnpm install
pnpm dev
```

### mise を使わない場合

Node.js `24.20.0` と pnpm `12.3.2` をインストールしたうえで、以下を実行します。

```sh
pnpm install
pnpm dev
```

起動後、既定のブラウザーで <http://localhost:8000/> が開きます。開かない場合も、同じ URL にアクセスしてください。サーバーは `Ctrl+C` で停止します。

初回以降、依存関係が変わっていなければ `pnpm dev` のみで起動できます。

`index.html` を `file://` で直接開かず、HTTP サーバー経由で確認してください。ブラウザーのセキュリティ制約により、ゲームが読み込むシナリオやアセットの一部が直接起動では正しく動作しない場合があります。
