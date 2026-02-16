*他の言語で読む: [English](README.md)*

# Repo Glance (Fully Offline) 📂

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Release](https://img.shields.io/github/v/release/E20C1/repo-glance?color=blue)](https://github.com/E20C1/repo-glance/releases)
[![Offline Capable](https://img.shields.io/badge/Offline-Capable-orange.svg)](#)
[![Single File](https://img.shields.io/badge/Single-HTML_File-ff69b4.svg)](#)

<p align="center">
  <!-- スクリーンショットがある場合はここに配置 -->
  <b>GitHubリポジトリやローカルZIPファイルを解析し、<br>LLMへのプロンプト入力用にテキスト化する単一HTMLツール。</b>
</p>

> サーバー構築不要。`index.html` を開くだけで動作します。

## 📋 目次

- [機能概要](#機能概要-)
- [使い方](#使い方-)
- [設定・カスタマイズ](#設定カスタマイズ-)
- [ファイル構成](#ファイル構成-)
- [技術仕様](#技術仕様-)
- [Todo](#todo-)
- [ライセンス](#ライセンス-)

## 機能概要 💯

<table align="center">
  <tr>
    <td align="center">🌐 ⟷ 💻<br><b>ハイブリッドソース</b></td>
    <td align="center">🚀<br><b>完全オフライン</b></td>
    <td align="center">🌳<br><b>ツリー可視化</b></td>
  </tr>
  <tr>
    <td align="center"><b>GitHub API</b> と<br><b>ローカルZIP</b> の両対応</td>
    <td align="center">依存関係なし<br><b>単一HTMLファイル</b>で完結</td>
    <td align="center">ファイル構造の<br><b>ASCIIツリー</b>を自動生成</td>
  </tr>
  <tr>
    <td align="center">🧹<br><b>スマートフィルタ</b></td>
    <td align="center">📋<br><b>ワンクリックコピー</b></td>
    <td align="center">🔑<br><b>トークン対応</b></td>
  </tr>
  <tr>
    <td align="center">画像や <code>node_modules</code><br>などの不要ファイルを自動除外</td>
    <td align="center">全ソースコードを<br>クリップボードへ一括コピー</td>
    <td align="center">Privateリポジトリ用に<br>GitHubトークン埋め込み可</td>
  </tr>
</table>

- **ポータビリティ**: 必要なライブラリ（JSZip）を含むすべてが `index.html` 1つに収まっています。
- **プライバシー重視**: ブラウザ内ですべて完結します。GitHub API以外への外部通信は行いません。
- **LLMフレンドリー**: ChatGPTやClaudeなどのAIに、リポジトリ全体のコンテキストを渡すのに最適化されたフォーマットで出力します。

## 使い方 👆

### A. GitHub APIから取得（オンライン）

1. ブラウザで `index.html` を開きます。
2. **Repository URL** を入力します（例: `https://github.com/username/repo`）。
3. (任意) Privateリポジトリや大規模リポジトリの場合は **GitHub Token** を入力します。
4. **「URLから取得実行」** をクリックします。

### B. ローカルZIPから取得（オフライン）

1. GitHubなどからリポジトリをZIPとしてダウンロードします。
2. ブラウザで `index.html` を開きます。
3. **「ローカルのZIPから取得」** でファイルを選択します。
4. **「ZIP解析実行」** をクリックします。

### 結果の利用

- 画面下にリポジトリ情報、ファイル構成ツリー、各ファイルの中身が結合されて表示されます。
- **「全テキストをコピー」** ボタンを押して、AIチャットなどに貼り付けてください。

## 設定・カスタマイズ 🛠️

`index.html` 内の変数を編集することで、毎回入力する手間を省けます。

### 1. GitHubトークンの埋め込み
コード内の以下の部分にトークンを記述します：

```javascript
// ▼▼▼ 設定エリア ▼▼▼
const HTML_CONFIG_TOKEN = "ghp_xxxxxxxxxxxxxxxxx"; // ここにトークンを設定
// ==========================================
```

### 2. 除外設定
解析から除外したい拡張子やディレクトリをカスタマイズできます：

```javascript
const IGNORE_EXTENSIONS = ['.png', '.jpg', '.exe', '.zip', ...];
const IGNORE_DIRS = ['.git', 'node_modules', 'dist', ...];
```

## ファイル構成 📁

究極のポータビリティのため、ファイルは実質1つです。

```
repo-glance/
│
├── index.html           # アプリ本体（HTML, CSS, JS, ライブラリ全て入り）
│
├── env.js               # (任意) トークン設定を外部化したい場合に使用
│
└── README.md            # ドキュメント
```

## 技術仕様 💻

- **コア技術**: Vanilla HTML5, CSS3, JavaScript (ES6+)
- **ライブラリ**: [JSZip](https://stuk.github.io/jszip/) (v3.10.1) - コード内に埋め込み済み
- **API利用**: GitHub REST API v3
- **対応ブラウザ**: Chrome, Firefox, Edge, Safari (モダンブラウザ)

## Todo 📝

- [ ] ZIPファイルのドラッグ＆ドロップ対応
- [ ] プレビューエリアのシンタックスハイライト
- [ ] ダークモード/ライトモード切り替えスイッチ
- [ ] トークンのlocalStorage保存機能

## ライセンス 📄

[MIT License](LICENSE)

---

<p align="center">
  <a href="https://github.com/E20C1">Made with ❤️ by E20C1</a>
</p>
