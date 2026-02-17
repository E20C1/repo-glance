# Repo Glance (Fully Offline) 📂

*Read this in other languages: [日本語](README.ja.md)*

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Release](https://img.shields.io/github/v/release/E20C1/repo-glance?color=blue)](https://github.com/E20C1/repo-glance/releases/tag/v1.0.0)
[![Security: Offline](https://img.shields.io/badge/Security-Fully%20Offline-success)](index.html)
[![Zero Dependency](https://img.shields.io/badge/Dependency-Zero-blueviolet)](index.html)

<p align="center">
  <b>Turn your repository into an LLM-ready prompt in seconds.</b><br>
  A standalone HTML tool to fetch, parse, and visualize codebases without sending data to any server.
</p>

---

### 🚀 Why Repo Glance?

> **🔰"Serverless & Secure"**<br>
> Designed for enterprise engineers and privacy-conscious users. Your code is processed entirely within your browser's memory. No data is ever sent to external servers (except standard GitHub API calls if you choose to use them).

> **🔒"No Install Required"**<br>
> Forget `npm install`, `pip install`, or environment setups. No `node_modules` hell. Just download the HTML file and open it.

> **💾"Ultimate Portability"**<br>
> Carry the single `index.html` file on a USB drive. Use it on air-gapped machines or restricted corporate environments where installing CLI tools is prohibited.

---

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
    <td align="center">keys<br><b>Secure Token</b></td>
  </tr>
  <tr>
    <td align="center">Auto-ignores binaries<br>and <code>node_modules</code></td>
    <td align="center">Copy entire repo<br>content to clipboard</td>
    <td align="center">Save GitHub Token<br>to localStorage (Optional)</td>
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
3. (Optional) Enter your **GitHub Personal Access Token**. Check **"Save Token"** to remember it.
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

### Ignore Settings
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
├── repoglance.html           # The main application (HTML + CSS + JS + Libraries)
│
├── README.md                # Documentation
│
└── README.ja.md            # Documentation (Japanese)
```

## Technical Specifications 💻

- **Core**: Vanilla HTML5, CSS3, JavaScript (ES6+)
- **Library**: [JSZip](https://stuk.github.io/jszip/) (v3.10.1) - Embedded directly into the file.
- **API**: GitHub REST API v3
- **Compatibility**: Chrome, Firefox, Edge, Safari (Modern Browsers)

## Todo 📝

- [ ] Syntax highlighting for code preview
- [ ] Collapsible file tree nodes
- [ ] File search / filtering in tree

## License 📄

[MIT License](LICENSE)

---

<p align="center">
  <a href="https://github.com/E20C1">Made with ❤️ by E20C1</a>
</p>
