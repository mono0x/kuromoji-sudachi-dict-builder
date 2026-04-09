# kuromoji-sudachi-dict-builder

kuromoji.js用のSudachi辞書変換ツール
Pii Jey さんの https://qiita.com/piijey/items/2517af039bbedddec7b8 を元にしています。

## 概要

`kuromoji-sudachi-dict-builder`は、Sudachi辞書を自動的にダウンロードして、kuromoji.js互換の形式に変換するツールです。
このスクリプトは、最新のSudachi辞書を取得し、必要なファイルをkuromoji.jsのフォーマットに整形してビルドを行います。

## 基本的な流れ

- Sudachi辞書の最新バージョンを自動で取得
- 必要なファイル（`small_lex`, `matrix.def`, `char.def`, `unk.def`）をダウンロード
- 辞書ファイルをkuromoji.js用に変換
- 辞書のビルド

## 必要環境

- awk コマンドが入っている環境

## インストール

1. リポジトリのクローン

```bash
git clone https://github.com/nyosegawa/kuromoji-sudachi-dict-builder.git
cd kuromoji-sudachi-dict-builder
```

2. 必要な依存パッケージをインストール

```bash
curl -O https://nodejs.org/dist/v10.16.3/node-v10.16.3-darwin-x64.tar.gz
mkdir .node
tar -xzf node-v10.16.3-darwin-x64.tar.gz --strip-components=1 -C .node
.node/bin/node --version # 10.16.3 になっていることを確認
.node/bin/npm install
```

## 使い方

以下を実行し辞書をビルドします。

```bash
PATH="$(pwd)/.node/bin:$PATH" .node/bin/npm run build-sudachi-dict
```

このコマンドを実行すると、Sudachi辞書の最新バージョンをダウンロードし、kuromoji.js互換の辞書を作成します。
ビルドされた辞書は `kuromoji-dict-sudachi` ディレクトリに出力されます。

## サンプルアプリケーション

NextJS + Mantine v7 でサンプルアプリケーションを用意しています。
詳細はsample-appのREADME.mdを参照してください。

## 注意点

- `awk` がインストールされている必要があります。macOSやLinuxではデフォルトで含まれていますが、Windowsを使用している場合は別途インストールが必要です
