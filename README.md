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
    <td align="center">Support for<br><b>GitHub, Folder & ZIP</b></td>
    <td align="center">Zero dependencies,<br><b>Single HTML file</b></td>
    <td align="center">Auto-generates<br><b>ASCII File Tree</b></td>
  </tr>
  <tr>
    <td align="center">🧹<br><b>Smart Filtering</b></td>
    <td align="center">📋<br><b>One-Click Copy</b></td>
    <td align="center">keys<br><b>Secure Token</b></td>
  </tr>
  <tr>
    <td align="center">Auto-ignores binaries<br>plus custom exclusions</td>
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

- **Single File Portability**: Everything (including JSZip library) is embedded in one `repo-glance.html`.
- **Privacy Focused**: Runs entirely in your browser. No data is sent to any external server (except GitHub API if used).
- **Smart Filtering**: Automatically excludes binary files (images, executables) and heavy directories like `.git` or `node_modules`.
- **Copy Exclusions**: Add project-specific or always-on path rules so selected folders/files never enter the generated LLM text.
- **Tree Search**: Filter the tree picker by file name, folder name, or relative path.

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

### Optional: Copy Exclusions

Before fetching or parsing, use **Copy Exclusions** to keep specific files or folders out of the generated text for **GitHub Repo**, **Local Folder**, and **Local ZIP**.

- **This Run**: Rules for the current repository or folder only.
- **Always Exclude**: Saved in your browser and applied to every project.
- **Choose from tree**: After analysis, open the dropdown and select files or folders with checkboxes. Checking a parent folder selects its child files; individual children can still be unchecked.
- **Tree search**: Search the picker by file name, folder name, or path. Matching folders show their child contents, while matching files keep their parent folders visible.
- **Always Exclude** matches still appear in the picker and in the generated `File Tree`, but their content is omitted. In the picker they are shown checked, dimmed, and locked.
- Missing files or folders are ignored silently, so you can keep global rules such as `.env` or `secrets/` even when a project does not contain them.
- The default always-exclude list is prefilled with common secret/key patterns and can be edited or cleared.
- When a Local Folder result is already ready to copy, editing **This Run** or saving **Always Exclude** automatically re-parses the selected folder so the output reflects the latest exclusions.

### Result

- The tool displays repository metadata, an ASCII file tree, and the text content of all files combined.
- Click **"Copy All to Clipboard"** to paste the context into LLMs (ChatGPT, Claude, etc.).

## Configuration 🛠️

### Ignore Settings
Built-in filters skip common binary files and heavy directories. Copy Exclusions add editable path rules on top:

```text
.env
.env.*
secrets/
src/generated.ts
*.pem
```

Rules can be file names, folder names, relative paths, or simple `*` / `?` patterns. Folder rules may end with `/`, but they do not have to.

You may include the project root folder in a rule, such as `BlurSubspace/src/assets/houston.webp`. Repo Glance also understands the equivalent relative path `src/assets/houston.webp`.

Tree selections are combined with the manual rules for the current output, but they do not remove the **This Run** text box for users who prefer direct path entry.

## File Structure 📁

The project consists of a single file for maximum portability.

```
repo-glance/
│
├── repo-glance.html          # The main application (HTML + CSS + JS + Libraries)
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

## License 📄

[MIT License](LICENSE)

---

<p align="center">
  <a href="https://github.com/E20C1">Made with ❤️ by E20C1</a>
</p>
