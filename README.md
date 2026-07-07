<div align="center">

**Language / 语言:** [English](README.md) · [中文](README.zh.md)

</div>

# Table Gap Remover

Hide the blank lines above and below tables in Obsidian **Live Preview** mode.

## Problem

In Live Preview, a table (`| ... |`) always renders with extra blank lines above and below it. Those lines are clickable and visually distracting.

Standard CSS snippets and inline-style hacks cannot remove it — Obsidian's CodeMirror 6 editor re-renders and overwrites any external style on every frame.

## Solution

This plugin uses the official **CodeMirror 6 Decoration + Theme** API to hide those blank lines as part of the editor's own rendering pipeline. The hidden line is removed from layout but the source markdown is never modified.

- Blank line **above a table** (`|`) → hidden
- Blank line **below a table** (`|`) → hidden
- Normal paragraph breaks (empty line between two text blocks) → **kept**

## Installation

### From Community Plugins (once approved)
1. Settings → Community plugins → Browse
2. Search "Table Gap Remover"
3. Install & enable

### Manual
Copy the `table-gap-remover` folder into your vault's `.obsidian/plugins/` directory, then enable it in Settings → Community plugins.

## How it works

The plugin registers a CodeMirror 6 `ViewPlugin` that adds a `rhg-gap-line` decoration class to empty lines directly above or below a table row. An `EditorView.theme` with maximum priority collapses those lines to zero height.

## Demo

Before (Table Gap Remover disabled — blank lines above and below the table are visible and clickable):

![before](测试图片-未打开插件.png)

After enabling Table Gap Remover, the gaps above and below the table disappear:

![after](测试图片-打开插件.png)

## License

[MIT](./LICENSE)
