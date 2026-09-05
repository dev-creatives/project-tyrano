# Issue #1: ローカル起動環境の追加

## Summary

TyranoScript の既存サンプルゲームを、mise 管理の Node.js / pnpm 環境で `pnpm dev` によりローカル HTTP サーバー起動・ブラウザー自動表示できるようにする。ゲーム本体のシナリオやアセットは変更しない。

## Key Changes

- `mise.toml` に Node.js `24.20.0` と pnpm `12.3.2` を固定し、`mise install` で開発環境を準備できるようにする。
- `package.json` と `pnpm-lock.yaml` を追加し、`packageManager`、Node.js / pnpm の `engines`、静的ファイルサーバー `http-server` を固定する。
- `dev` スクリプトを `http-server` の起動、ポート `8000`、キャッシュ無効化、既定ブラウザーでの自動オープンとして定義する。
- `node_modules/` を `.gitignore` に追加する。
- 日本語の `README.md` を追加し、mise の導入、`mise install`、`pnpm install`、`pnpm dev`、アクセス URL、停止方法を案内する。`file://` 直開きではなく HTTP 経由で確認する理由も明記する。テンプレート付属の `readme.txt` は変更しない。

## Test Plan

- クリーンな mise 環境で `mise install` 後、Node.js `24.20.0` と pnpm `12.3.2` が利用可能になることを確認する。
- `pnpm install --frozen-lockfile` 後、`pnpm dev` が成功し、`http://localhost:8000/` を自動で開くことを確認する。
- タイトル画面が表示され、「はじめから」から `scene1.ks` のサンプルシナリオへ遷移できることを確認する。
- ブラウザーコンソールに、必須アセットやシナリオ読み込みの失敗がないことを確認する。

## Assumptions

- 対象はローカル開発・動作確認のみであり、公開・デプロイ・配布用パッケージ化は含めない。
- Node.js と pnpm はリポジトリには同梱せず、mise により取得・管理する。
- CI、公開・デプロイ、配布用パッケージ化は対象外とする。
