# ACR WASM Test Server

ACR（Across Report Renderer）のローカルプレビューサーバです。  
Chrome拡張とWASMを使って、ブラウザ上で帳票をPNG表示します。

## 特徴

- **サーバ不要** — ローカルで完結、データは外部に送信されません
- **クロスプラットフォーム** — Windows / Mac / Linux 対応
- **多言語対応** — 日本語 / English / Français
- **Chrome拡張連携** — WASMエンジンで高速レンダリング

## 必要な環境

| 項目 | 内容 |
|------|------|
| ブラウザ | Google Chrome |
| Chrome拡張 | ACR Report Renderer（無償） |
| ライセンス | [licensvr.acrossreport.com](https://licensvr.acrossreport.com) で無償登録 |

## 使い方

### 1. Chrome拡張をインストール

`chrome://extensions/` を開き、デベロッパーモードをONにして  
`extension/` フォルダを「パッケージ化されていない拡張機能を読み込む」で選択します。

### 2. ライセンス登録（初回のみ）

[https://licensvr.acrossreport.com](https://licensvr.acrossreport.com) にアクセスし、  
「ACR WASM」セクションの「Googleで登録」をクリックします。  
認証後、ライセンスがChrome拡張に自動保存されます。

### 3. サーバを起動

```bash
# Linux / Mac
./acr-preview

# Windows
acr-preview.exe
```

ブラウザが自動で開き `http://localhost:7878` にアクセスします。

### 4. 帳票をプレビュー

- **Sample** ボタン → サンプル仕入伝票を表示
- **テンプレート / データ** → 任意のJSONファイルをアップロード
- **Render** ボタン → PNG形式でプレビュー表示

## ビルド方法

```bash
# 依存関係
cargo build --release

# Windows向けクロスコンパイル（Linux上で）
cargo build --release --target x86_64-pc-windows-gnu
```

## ディレクトリ構成

```
acr-wasmtest/
├── src/
│   └── main.rs          # Axum Webサーバ
├── static/
│   └── index.html       # フロントエンドUI
├── sample/
│   ├── template.json    # サンプルテンプレート（仕入伝票）
│   └── data.json        # サンプルデータ
└── Cargo.toml
```

## ライセンス

© 2026 Across Systems Corporation  
本ソフトウェアは評価・テスト目的で提供されます。

## お問い合わせ

- Web: [acrossreport.com](https://acrossreport.com)
- Mail: [support@acrossreport.com](mailto:support@acrossreport.com)
