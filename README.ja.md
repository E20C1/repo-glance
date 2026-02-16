*他の言語で読む: [English](README.md)*

# Repo Glance (Fully Offline) 📂

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Release](https://img.shields.io/github/v/release/E20C1/repo-glance?color=blue)](https://github.com/E20C1/repo-glance/releases/tag/v1.0.0)
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
  <tr>
    <td align="center">🌓<br><b>テーマ & I18N</b></td>
    <td align="center">📂<br><b>フォルダ対応</b></td>
    <td align="center">💅<br><b>モダンUI</b></td>
  </tr>
  <tr>
    <td align="center">ダーク/ライト切替<br>日英言語切替</td>
    <td align="center">ローカルフォルダを<br>直接解析可能</td>
    <td align="center">Glassmorphism<br>デザイン</td>
  </tr>
</table>

- **ポータビリティ**: 必要なライブラリ（JSZip）を含むすべてが `index.html` 1つに収まっています。
- **プライバシー重視**: ブラウザ内ですべて完結します。GitHub API以外への外部通信は行いません。
- **LLMフレンドリー**: ChatGPTやClaudeなどのAIに、リポジトリ全体のコンテキストを渡すのに最適化されたフォーマットで出力します。

## 使い方 👆

### タブ1: GitHub API（オンライン）

1. **「GitHubリポジトリ」** タブを選択します。
2. **Repository URL** を入力します。
3. (任意) トークンを入力し、**「URLから取得」** をクリックします。

### タブ2: ローカルフォルダ（オフライン）

1. **「ローカルフォルダ」** タブを選択します。
2. エリアをクリックしてフォルダを選択します。
3. ブラウザがフォルダ内のファイルを読み取り、テキスト化します。

### タブ3: ローカルZIP（オフライン）

1. **「ローカルZIP」** タブを選択します。
2. クリック（またはドラッグ＆ドロップ）でZIPファイルを選択します。
3. 自動的に解析が始まります。

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

- [x] ZIPファイルのドラッグ＆ドロップ対応
- [ ] プレビューエリアのシンタックスハイライト
- [x] ダークモード/ライトモード切り替えスイッチ
- [x] 日英言語切り替え (I18N)
- [x] ローカルフォルダ入力対応
- [ ] トークンのlocalStorage保存機能

## ライセンス 📄

[MIT License](LICENSE)

---

<p align="center">
  <a href="https://github.com/E20C1">Made with ❤️ by E20C1</a>
</p>
