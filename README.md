# Repo Glance (Fully Offline) 📂

*Read this in other languages: [日本語](README.ja.md)*

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Release](https://img.shields.io/github/v/release/E20C1/repo-glance?color=blue)](https://github.com/E20C1/repo-glance/releases/tag/v1.0.0)
[![Offline Capable](https://img.shields.io/badge/Offline-Capable-orange.svg)](#)
[![Single File](https://img.shields.io/badge/Single-HTML_File-ff69b4.svg)](#)

<p align="center">
  <!-- スクリーンショットがある場合はここに配置 -->
  <!-- <img src="screenshot.png" alt="Repo Glance Screenshot" width="600"> -->
  <b>A standalone HTML tool to fetch, parse, and visualize GitHub repositories or local ZIP files offline.</b>
</p>

> No server setup required. Just open the HTML file.

## 📋 Table of Contents

- [Features](#features-)
- [How to Use](#how-to-use-)
- [Configuration](#configuration-)
- [File Structure](#file-structure-)
- [Technical Specifications](#technical-specifications-)
- [Todo](#todo-)
- [License](#license-)

## Features 💯

<table align="center">
  <tr>
    <td align="center">🌐 ⟷ 💻<br><b>Hybrid Source</b></td>
    <td align="center">🚀<br><b>Fully Offline</b></td>
    <td align="center">🌳<br><b>Tree Visualization</b></td>
  </tr>
  <tr>
    <td align="center">Support for both<br><b>GitHub API & Local ZIP</b></td>
    <td align="center">Zero dependencies,<br><b>Single HTML file</b></td>
    <td align="center">Auto-generates<br><b>ASCII File Tree</b></td>
  </tr>
  <tr>
    <td align="center">🧹<br><b>Smart Filtering</b></td>
    <td align="center">📋<br><b>One-Click Copy</b></td>
    <td align="center">🔑<br><b>Token Support</b></td>
  </tr>
  <tr>
    <td align="center">Auto-ignores binaries<br>and <code>node_modules</code></td>
    <td align="center">Copy entire repo<br>content to clipboard</td>
    <td align="center">Embed GitHub Token<br>for higher rate limits</td>
  </tr>
  <tr>
    <td align="center">🌓<br><b>Theme & I18N</b></td>
    <td align="center">📂<br><b>Folder Support</b></td>
    <td align="center">💅<br><b>Modern UI</b></td>
  </tr>
  <tr>
    <td align="center">Dark/Light Mode<br>English/Japanese</td>
    <td align="center">Parse Local Folders<br>Directly</td>
    <td align="center">Glassmorphism<br>Design</td>
  </tr>
</table>

- **Single File Portability**: Everything (including JSZip library) is embedded in one `index.html`.
- **Privacy Focused**: Runs entirely in your browser. No data is sent to any external server (except GitHub API if used).
- **Smart Filtering**: Automatically excludes binary files (images, executables) and heavy directories like `.git` or `node_modules`.

## How to Use 👆

### Tab 1: GitHub API (Online)

1. Select **"GitHub Repo"** tab.
2. Enter the **Repository URL** (e.g., `https://github.com/username/repo`).
3. (Optional) Enter your **GitHub Personal Access Token**.
4. Click **"Fetch from URL"**.

### Tab 2: Local Folder (Offline)

1. Select **"Local Folder"** tab.
2. Click the upload area to select a folder from your computer.
3. The browser will parse files immediately.

### Tab 3: Local ZIP (Offline)

1. Select **"Local ZIP"** tab.
2. Click to select (or drag & drop) a ZIP file.
3. The tool will unzip and parse contents.

### Result

- The tool displays repository metadata, an ASCII file tree, and the text content of all files combined.
- Click **"Copy All to Clipboard"** to paste the context into LLMs (ChatGPT, Claude, etc.).

## Configuration 🛠️

You can hardcode your settings directly into the `index.html` file to skip manual entry.

### 1. Embed GitHub Token
Edit the `script` section in `index.html`:

```javascript
// ▼▼▼ CONFIGURATION AREA ▼▼▼
const HTML_CONFIG_TOKEN = "your_github_pat_token_here";
// ==========================
```

### 2. Ignore Settings
Customize the file extensions or directories to ignore:

```javascript
const IGNORE_EXTENSIONS = ['.png', '.jpg', '.exe', '.zip', ...];
const IGNORE_DIRS = ['.git', 'node_modules', 'dist', ...];
```

## File Structure 📁

The project consists of a single file for maximum portability.

```
repo-glance/
│
├── index.html           # The main application (HTML + CSS + JS + Libraries)
│
├── env.js               # (Optional) External config file for tokens
│
└── README.md            # Documentation
```

## Technical Specifications 💻

- **Core**: Vanilla HTML5, CSS3, JavaScript (ES6+)
- **Library**: [JSZip](https://stuk.github.io/jszip/) (v3.10.1) - Embedded directly into the file.
- **API**: GitHub REST API v3
- **Compatibility**: Chrome, Firefox, Edge, Safari (Modern Browsers)

## Todo 📝

- [x] Add drag-and-drop support for ZIP files
- [ ] Syntax highlighting for code preview
- [x] Dark/Light mode toggle
- [x] Internationalization (English/Japanese)
- [x] Local Folder input support
- [ ] Save API token to localStorage

## License 📄

[MIT License](LICENSE)

---

<p align="center">
  <a href="https://github.com/E20C1">Made with ❤️ by E20C1</a>
</p>
