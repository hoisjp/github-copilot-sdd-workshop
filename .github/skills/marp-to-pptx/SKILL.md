---
name: marp-to-pptx
description: "Convert Markdown files to PowerPoint (PPTX), PDF, or HTML slides using Marp. Use when asked to generate slides quickly without a corporate template, create presentations from Markdown, preview slides in VS Code, or export to PPTX/PDF/HTML. Supports built-in themes (default, gaia, uncover), custom CSS themes, speaker notes, and GitHub Actions automation. USE FOR: Marp slides, Markdown to PPTX without template, quick slide generation, Marp VS Code preview, Marp CLI export, marp-team.marp-vscode, incremental slides, slide theme."
allowed-tools: Bash(npm:*) Bash(npx:*) Bash(marp:*) Bash(which:*)
---

# Markdown から PowerPoint / PDF / HTML スライドへの変換（Marp）

このスキルは [Marp](https://marp.app/) を使って Markdown ファイルを PPTX / PDF / HTML スライドに変換するワークフローを提供する。
社内テンプレート不要で最速に変換できる点が最大の強み。VS Code でリアルタイムプレビューも可能。

このリポジトリでは 指定がない場合、テーマは [docs/themes/microsoft-theme.css](../../../docs/themes/microsoft-theme.css) を使用する。

## 前提条件

| ツール | 確認コマンド | インストール |
|--------|-------------|-------------|
| Node.js 18 以上 | `node --version` | [nodejs.org](https://nodejs.org/) |
| Marp CLI | `marp --version` | `npm install -g @marp-team/marp-cli` |
| VS Code 拡張（任意） | — | `marp-team.marp-vscode` |

Marp CLI がインストールされていない場合は、作業前に以下を実行する:

```bash
npm install -g @marp-team/marp-cli
```

## ワークフロー

### Step 1. インストール確認

```bash
marp --version
```

出力例: `@marp-team/marp-cli v4.x.x (w/ @marp-team/marp-core v3.x.x)` — これが出れば OK。

---

### Step 2. Marp 用 Markdown の記法

Marp では YAML フロントマターに `marp: true` を記述することで Marp モードになる。

```markdown
---
marp: true
theme: default
paginate: true
---

# プレゼンタイトル

---

## スライド 2 のタイトル

- 箇条書き A
- 箇条書き B

<!--
スピーカーノートはHTMLコメント内に書く
-->

---

## スライド 3 のタイトル

内容テキスト
```

**記法のポイント:**
- `---`（水平線）がスライドの区切り
- YAML フロントマターの `marp: true` が必須
- スピーカーノートは `<!-- ... -->` のHTMLコメントで記述

---

### Step 3. エクスポートコマンド

```bash
# PPTX に変換（最も典型的）
marp docs/workshop-instructor-guide-marp.md --pptx --theme-set docs/themes/microsoft-theme.css -o output/workshop-instructor-guide.pptx

# PDF に変換
marp docs/workshop-instructor-guide-marp.md --pdf --theme-set docs/themes/microsoft-theme.css -o output/workshop-instructor-guide.pdf

# HTML に変換（ブラウザでプレゼン可能）
marp docs/workshop-instructor-guide-marp.md --theme-set docs/themes/microsoft-theme.css -o output/workshop-instructor-guide.html

# ローカル画像を含む場合
marp docs/workshop-instructor-guide-marp.md --pptx --theme-set docs/themes/microsoft-theme.css --allow-local-files -o output/workshop-instructor-guide.pptx
```

> PPTX / PDF へのエクスポートは、依頼された場合のみ実行すること。Markdown の作成・編集だけで完結する場合は変換コマンドを実行しない。

---

### Step 4. テーマの指定

Marp には 3 種の組み込みテーマと、CSS ファイルによるカスタムテーマがある。YAML フロントマターの `theme` で指定する。

| テーマ名 | 特徴 |
|---|---|
| `default` | 白背景・シンプル（デフォルト） |
| `gaia` | 濃色・モダン |
| `uncover` | ミニマル・白黒 |
| `microsoft-theme` | Microsoft Office 近似スタイル（本リポジトリの `docs/themes/microsoft-theme.css`） |

カスタムテーマ CSS は `/* @theme theme-name */` コメントを先頭に記述することで登録される。変換時は `--theme-set` でテーマ CSS ファイルを指定し、Markdown の `theme:` に名前を指定する。

**スライドクラスによる個別スタイル切り替え:**

```markdown
<!-- _class: title -->

# タイトルスライド（濃紺背景）

---

<!-- _class: section -->

## セクション区切りスライド（青背景）
```

---

### Step 5. VS Code でのプレビュー

VS Code 拡張 `marp-team.marp-vscode` をインストールすると、Markdown ファイルを開いた状態でリアルタイムプレビューが表示される。

1. コマンドパレット（`Cmd+Shift+P`）で `Marp: Open Preview` を実行
2. または、エディタ右上のプレビューアイコンをクリック

---

### Step 6. よく使うオプション一覧

| オプション | 説明 | 例 |
|---|---|---|
| `--pptx` | PPTX 形式で出力 | `marp slides.md --pptx` |
| `--pdf` | PDF 形式で出力 | `marp slides.md --pdf` |
| `--theme-set FILE` | カスタムテーマ CSS を登録 | `--theme-set docs/themes/microsoft-theme.css` |
| `--allow-local-files` | ローカルファイル（画像等）の読み込みを許可 | — |
| `--watch` | ファイル変更を検知して自動再変換 | `--watch` |
| `-o FILE` | 出力ファイル名 | `-o output.pptx` |

---

## トラブルシューティング

| 症状 | 原因 | 対処 |
|---|---|---|
| `marp: command not found` | Marp CLI 未インストール | `npm install -g @marp-team/marp-cli` |
| 画像が表示されない | ローカルファイルアクセスが制限されている | `--allow-local-files` を追加 |
| 日本語が文字化けする | フォント未埋め込み | PDF 出力に切り替えるか、カスタムテーマで日本語フォントを指定 |
| スライドが 1 枚しか生成されない | `marp: true` がフロントマターにない | YAML フロントマターに `marp: true` を追加 |
| テーマが反映されない | `--theme-set` の指定漏れ、またはテーマ名のスペルミス | `--theme-set docs/themes/microsoft-theme.css` を指定しているか確認 |
