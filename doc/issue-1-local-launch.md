# Issue #1: ローカル起動環境の追加

## Summary

TyranoScript の既存サンプルゲームを、Node.js 環境で `npm run dev` によりローカル HTTP サーバー起動・ブラウザー自動表示できるようにする。ゲーム本体のシナリオやアセットは変更しない。

## Key Changes

- `package.json` と lockfile を追加し、静的ファイルサーバー `http-server` を開発依存として固定する。
- `dev` スクリプトを `http-server` の起動、ポート `8000`、キャッシュ無効化、既定ブラウザーでの自動オープンとして定義する。
- `node_modules/` を `.gitignore` に追加する。
- 日本語の `README.md` を追加し、Node.js LTS の導入、`npm install`、`npm run dev`、アクセス URL、停止方法を案内する。`file://` 直開きではなく HTTP 経由で確認する理由も明記する。

## Test Plan

- Node.js LTS 環境で `npm install` 後、`npm run dev` が成功し、`http://localhost:8000/` を自動で開くことを確認する。
- タイトル画面が表示され、「はじめから」から `scene1.ks` のサンプルシナリオへ遷移できることを確認する。
- ブラウザーコンソールに、必須アセットやシナリオ読み込みの失敗がないことを確認する。

## Assumptions

- 対象はローカル開発・動作確認のみであり、公開・デプロイ・配布用パッケージ化は含めない。
- Node.js はリポジトリには同梱せず、開発者が LTS 版を導入する。
- 現在の環境には Node.js/npm が未導入のため、実装後の起動検証は Node.js LTS を導入済みの環境で行う。
