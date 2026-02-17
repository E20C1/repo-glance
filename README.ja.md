# Repo Glance (Fully Offline) 📂

*他の言語で読む: [English](README.md)*

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Release](https://img.shields.io/github/v/release/E20C1/repo-glance?color=blue)](https://github.com/E20C1/repo-glance/releases/tag/v1.0.0)
[![Security: Offline](https://img.shields.io/badge/Security-完全オフライン-success)](index.html)
[![Zero Dependency](https://img.shields.io/badge/Dependency-インストール不要-blueviolet)](index.html)

<p align="center">
  <b>リポジトリを、AIが読める「ひとつのテキスト」へ。</b><br>
  GitHubリポジトリやローカルファイルを解析し、LLMへのプロンプト入力用に最適化する単一HTMLツール。
</p>

---

### 🚀 選ばれる3つの理由

> **🔰 インストール一切不要 (No Install Required)**
> `npm install` や Python環境の構築は必要ありません。`node_modules` の管理に疲れたエンジニアへ。HTMLファイルをダウンロードして開くだけで、数秒でセットアップが完了します。

> **🔒 完全オフライン & セキュア (Serverless & Secure)**
> データはすべてブラウザ内で処理されます。外部サーバーへのコード送信は一切行われません（GitHub API利用時を除く）。社内規定で外部サービスへのコード貼り付けが制限されている環境や、機密性の高いプロジェクトに最適です。

> **💾 持ち運べるツール (Portable Tool)**
> 依存ライブラリ（JSZip等）はすべて1つのHTMLファイルに内包されています。USBメモリに入れて持ち運べば、インターネット環境がないオフラインPCや、ソフトウェアインストールが制限された環境でも即座に利用可能です。

---

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
    <td align="center">keys<br><b>トークン保存</b></td>
  </tr>
  <tr>
    <td align="center">画像や <code>node_modules</code><br>などの不要ファイルを自動除外</td>
    <td align="center">全ソースコードを<br>クリップボードへ一括コピー</td>
    <td align="center">GitHubトークンを<br>ブラウザに保存可能(任意)</td>
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
3. (任意) トークンを入力します。**「ブラウザに保存する」** をチェックすると次回以降自動入力されます。
4. **「URLから取得」** をクリックします。

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

### 除外設定
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
- [x] ローカルフォルダ入力対応
- [x] トークンのlocalStorage保存機能
- [ ] プレビューエリアのシンタックスハイライト
- [ ] ファイルツリーの折りたたみ機能
- [ ] ツリー内のファイル検索・フィルタリング

## ライセンス 📄

[MIT License](LICENSE)

---

<p align="center">
  <a href="https://github.com/E20C1">Made with ❤️ by E20C1</a>
</p>
