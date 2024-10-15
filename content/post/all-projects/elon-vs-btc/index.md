+++
title = 'Elon Musk vs Bitcoin'
description = '''
A "Google Causal Impact" Analysis Between Elon Musk Tweet's & BTC Downfall
'''
slug = "elon-vs-btc"
date = "2023-05-27"
image = "cover.jpg"
draft = false
categories = ["My Projects"]
tags= ["google causal impact", "python", "pandas", "data analytics", "statistics"]
+++
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
.button {
  background-color: #d9534f;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 16px;
}
</style>
</head>
<div align=center>
<a href="https://saiyanahmed.github.io/elon_vs_btc">
<button class="button">Full View</button>
</a>
</div>
</html>

<div>
<details>
<summary>Goal of this project</summary>
<br>
The main purpose of this project is to explore the aftermath of Elon Musk's tweet on May 13, 2022, where he announced that Tesla would no longer accept Bitcoin as a form of payment. This unexpected decision sent shockwaves through the Bitcoin community and had a noticeable impact on its price.

For that, I employed the powerful statistical package called Google Causal Impact to study this phenomenon. With its ability to estimate the causal impact of an event on a target variable while accounting for other influencing factors, it was the perfect tool for this analysis.

The results were truly enlightening! The analysis revealed a significant and negative causal effect of Musk's tweet on Bitcoin's price. It became clear that the tweet had triggered panic within the Bitcoin community and influenced investor sentiment, leading to a noticeable decrease in price.
</details>

<div>

<!DOCTYPE html>

<html lang="en">
<head><meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<title>Elon vs BTC</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<style type="text/css">
    pre { line-height: 125%; }
td.linenos .normal { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
span.linenos { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
td.linenos .special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
span.linenos.special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
.highlight .hll { background-color: var(--jp-cell-editor-active-background) }
.highlight { background: var(--jp-cell-editor-background); color: var(--jp-mirror-editor-variable-color) }
.highlight .c { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment */
.highlight .err { color: var(--jp-mirror-editor-error-color) } /* Error */
.highlight .k { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword */
.highlight .o { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator */
.highlight .p { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation */
.highlight .ch { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Multiline */
.highlight .cp { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Preproc */
.highlight .cpf { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Single */
.highlight .cs { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Special */
.highlight .kc { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Pseudo */
.highlight .kr { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Type */
.highlight .m { color: var(--jp-mirror-editor-number-color) } /* Literal.Number */
.highlight .s { color: var(--jp-mirror-editor-string-color) } /* Literal.String */
.highlight .ow { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator.Word */
.highlight .pm { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation.Marker */
.highlight .w { color: var(--jp-mirror-editor-variable-color) } /* Text.Whitespace */
.highlight .mb { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Bin */
.highlight .mf { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Float */
.highlight .mh { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Hex */
.highlight .mi { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer */
.highlight .mo { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Oct */
.highlight .sa { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Affix */
.highlight .sb { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Backtick */
.highlight .sc { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Char */
.highlight .dl { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Delimiter */
.highlight .sd { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Doc */
.highlight .s2 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Double */
.highlight .se { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Escape */
.highlight .sh { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Heredoc */
.highlight .si { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Interpol */
.highlight .sx { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Other */
.highlight .sr { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Regex */
.highlight .s1 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Single */
.highlight .ss { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Symbol */
.highlight .il { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer.Long */
  </style>
<style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
 * Mozilla scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */
[data-jp-theme-scrollbars='true'] {
  scrollbar-color: rgb(var(--jp-scrollbar-thumb-color))
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar. These selectors
 * will match lower in the tree, and so will override the above */
[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
}

/* tiny scrollbar */

.jp-scrollbar-tiny {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
  scrollbar-width: thin;
}

/* tiny scrollbar */

.jp-scrollbar-tiny::-webkit-scrollbar,
.jp-scrollbar-tiny::-webkit-scrollbar-corner {
  background-color: transparent;
  height: 4px;
  width: 4px;
}

.jp-scrollbar-tiny::-webkit-scrollbar-thumb {
  background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:horizontal {
  border-left: 0 solid transparent;
  border-right: 0 solid transparent;
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:vertical {
  border-top: 0 solid transparent;
  border-bottom: 0 solid transparent;
}

/*
 * Lumino
 */

.lm-ScrollBar[data-orientation='horizontal'] {
  min-height: 16px;
  max-height: 16px;
  min-width: 45px;
  border-top: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] {
  min-width: 16px;
  max-width: 16px;
  min-height: 45px;
  border-left: 1px solid #a0a0a0;
}

.lm-ScrollBar-button {
  background-color: #f0f0f0;
  background-position: center center;
  min-height: 15px;
  max-height: 15px;
  min-width: 15px;
  max-width: 15px;
}

.lm-ScrollBar-button:hover {
  background-color: #dadada;
}

.lm-ScrollBar-button.lm-mod-active {
  background-color: #cdcdcd;
}

.lm-ScrollBar-track {
  background: #f0f0f0;
}

.lm-ScrollBar-thumb {
  background: #cdcdcd;
}

.lm-ScrollBar-thumb:hover {
  background: #bababa;
}

.lm-ScrollBar-thumb.lm-mod-active {
  background: #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal'] .lm-ScrollBar-thumb {
  height: 100%;
  min-width: 15px;
  border-left: 1px solid #a0a0a0;
  border-right: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] .lm-ScrollBar-thumb {
  width: 100%;
  min-height: 15px;
  border-top: 1px solid #a0a0a0;
  border-bottom: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-left);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-right);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-up);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-down);
  background-size: 17px;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-Widget {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
}

.lm-Widget.lm-mod-hidden {
  display: none !important;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.lm-AccordionPanel[data-orientation='horizontal'] > .lm-AccordionPanel-title {
  /* Title is rotated for horizontal accordion panel using CSS */
  display: block;
  transform-origin: top left;
  transform: rotate(-90deg) translate(-100%);
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-CommandPalette {
  display: flex;
  flex-direction: column;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-CommandPalette-search {
  flex: 0 0 auto;
}

.lm-CommandPalette-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  min-height: 0;
  overflow: auto;
  list-style-type: none;
}

.lm-CommandPalette-header {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.lm-CommandPalette-item {
  display: flex;
  flex-direction: row;
}

.lm-CommandPalette-itemIcon {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemContent {
  flex: 1 1 auto;
  overflow: hidden;
}

.lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemLabel {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.lm-close-icon {
  border: 1px solid transparent;
  background-color: transparent;
  position: absolute;
  z-index: 1;
  right: 3%;
  top: 0;
  bottom: 0;
  margin: auto;
  padding: 7px 0;
  display: none;
  vertical-align: middle;
  outline: 0;
  cursor: pointer;
}
.lm-close-icon:after {
  content: 'X';
  display: block;
  width: 15px;
  height: 15px;
  text-align: center;
  color: #000;
  font-weight: normal;
  font-size: 12px;
  cursor: pointer;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-DockPanel {
  z-index: 0;
}

.lm-DockPanel-widget {
  z-index: 0;
}

.lm-DockPanel-tabBar {
  z-index: 1;
}

.lm-DockPanel-handle {
  z-index: 2;
}

.lm-DockPanel-handle.lm-mod-hidden {
  display: none !important;
}

.lm-DockPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}

.lm-DockPanel-handle[data-orientation='horizontal'] {
  cursor: ew-resize;
}

.lm-DockPanel-handle[data-orientation='vertical'] {
  cursor: ns-resize;
}

.lm-DockPanel-handle[data-orientation='horizontal']:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}

.lm-DockPanel-handle[data-orientation='vertical']:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}

.lm-DockPanel-overlay {
  z-index: 3;
  box-sizing: border-box;
  pointer-events: none;
}

.lm-DockPanel-overlay.lm-mod-hidden {
  display: none !important;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-Menu {
  z-index: 10000;
  position: absolute;
  white-space: nowrap;
  overflow-x: hidden;
  overflow-y: auto;
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-Menu-content {
  margin: 0;
  padding: 0;
  display: table;
  list-style-type: none;
}

.lm-Menu-item {
  display: table-row;
}

.lm-Menu-item.lm-mod-hidden,
.lm-Menu-item.lm-mod-collapsed {
  display: none !important;
}

.lm-Menu-itemIcon,
.lm-Menu-itemSubmenuIcon {
  display: table-cell;
  text-align: center;
}

.lm-Menu-itemLabel {
  display: table-cell;
  text-align: left;
}

.lm-Menu-itemShortcut {
  display: table-cell;
  text-align: right;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-MenuBar {
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-MenuBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: row;
  list-style-type: none;
}

.lm-MenuBar-item {
  box-sizing: border-box;
}

.lm-MenuBar-itemIcon,
.lm-MenuBar-itemLabel {
  display: inline-block;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-ScrollBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-ScrollBar[data-orientation='horizontal'] {
  flex-direction: row;
}

.lm-ScrollBar[data-orientation='vertical'] {
  flex-direction: column;
}

.lm-ScrollBar-button {
  box-sizing: border-box;
  flex: 0 0 auto;
}

.lm-ScrollBar-track {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  flex: 1 1 auto;
}

.lm-ScrollBar-thumb {
  box-sizing: border-box;
  position: absolute;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-SplitPanel-child {
  z-index: 0;
}

.lm-SplitPanel-handle {
  z-index: 1;
}

.lm-SplitPanel-handle.lm-mod-hidden {
  display: none !important;
}

.lm-SplitPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}

.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle {
  cursor: ew-resize;
}

.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle {
  cursor: ns-resize;
}

.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}

.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-TabBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-TabBar[data-orientation='horizontal'] {
  flex-direction: row;
  align-items: flex-end;
}

.lm-TabBar[data-orientation='vertical'] {
  flex-direction: column;
  align-items: flex-end;
}

.lm-TabBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex: 1 1 auto;
  list-style-type: none;
}

.lm-TabBar[data-orientation='horizontal'] > .lm-TabBar-content {
  flex-direction: row;
}

.lm-TabBar[data-orientation='vertical'] > .lm-TabBar-content {
  flex-direction: column;
}

.lm-TabBar-tab {
  display: flex;
  flex-direction: row;
  box-sizing: border-box;
  overflow: hidden;
  touch-action: none; /* Disable native Drag/Drop */
}

.lm-TabBar-tabIcon,
.lm-TabBar-tabCloseIcon {
  flex: 0 0 auto;
}

.lm-TabBar-tabLabel {
  flex: 1 1 auto;
  overflow: hidden;
  white-space: nowrap;
}

.lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing: border-box;
}

.lm-TabBar-tab.lm-mod-hidden {
  display: none !important;
}

.lm-TabBar-addButton.lm-mod-hidden {
  display: none !important;
}

.lm-TabBar.lm-mod-dragging .lm-TabBar-tab {
  position: relative;
}

.lm-TabBar.lm-mod-dragging[data-orientation='horizontal'] .lm-TabBar-tab {
  left: 0;
  transition: left 150ms ease;
}

.lm-TabBar.lm-mod-dragging[data-orientation='vertical'] .lm-TabBar-tab {
  top: 0;
  transition: top 150ms ease;
}

.lm-TabBar.lm-mod-dragging .lm-TabBar-tab.lm-mod-dragging {
  transition: none;
}

.lm-TabBar-tabLabel .lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing: border-box;
  background: inherit;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-TabPanel-tabBar {
  z-index: 1;
}

.lm-TabPanel-stackedPanel {
  z-index: 0;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapse {
  display: flex;
  flex-direction: column;
  align-items: stretch;
}

.jp-Collapse-header {
  padding: 1px 12px;
  background-color: var(--jp-layout-color1);
  border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
  color: var(--jp-ui-font-color1);
  cursor: pointer;
  display: flex;
  align-items: center;
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  text-transform: uppercase;
  user-select: none;
}

.jp-Collapser-icon {
  height: 16px;
}

.jp-Collapse-header-collapsed .jp-Collapser-icon {
  transform: rotate(-90deg);
  margin: auto 0;
}

.jp-Collapser-title {
  line-height: 25px;
}

.jp-Collapse-contents {
  padding: 0 12px;
  background-color: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  overflow: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensureUiComponents() in @jupyterlab/buildutils */

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

/* Icons urls */

:root {
  --jp-icon-add-above: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPGcgY2xpcC1wYXRoPSJ1cmwoI2NsaXAwXzEzN18xOTQ5MikiPgo8cGF0aCBjbGFzcz0ianAtaWNvbjMiIGQ9Ik00Ljc1IDQuOTMwNjZINi42MjVWNi44MDU2NkM2LjYyNSA3LjAxMTkxIDYuNzkzNzUgNy4xODA2NiA3IDcuMTgwNjZDNy4yMDYyNSA3LjE4MDY2IDcuMzc1IDcuMDExOTEgNy4zNzUgNi44MDU2NlY0LjkzMDY2SDkuMjVDOS40NTYyNSA0LjkzMDY2IDkuNjI1IDQuNzYxOTEgOS42MjUgNC41NTU2NkM5LjYyNSA0LjM0OTQxIDkuNDU2MjUgNC4xODA2NiA5LjI1IDQuMTgwNjZINy4zNzVWMi4zMDU2NkM3LjM3NSAyLjA5OTQxIDcuMjA2MjUgMS45MzA2NiA3IDEuOTMwNjZDNi43OTM3NSAxLjkzMDY2IDYuNjI1IDIuMDk5NDEgNi42MjUgMi4zMDU2NlY0LjE4MDY2SDQuNzVDNC41NDM3NSA0LjE4MDY2IDQuMzc1IDQuMzQ5NDEgNC4zNzUgNC41NTU2NkM0LjM3NSA0Ljc2MTkxIDQuNTQzNzUgNC45MzA2NiA0Ljc1IDQuOTMwNjZaIiBmaWxsPSIjNjE2MTYxIiBzdHJva2U9IiM2MTYxNjEiIHN0cm9rZS13aWR0aD0iMC43Ii8+CjwvZz4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTExLjUgOS41VjExLjVMMi41IDExLjVWOS41TDExLjUgOS41Wk0xMiA4QzEyLjU1MjMgOCAxMyA4LjQ0NzcyIDEzIDlWMTJDMTMgMTIuNTUyMyAxMi41NTIzIDEzIDEyIDEzTDIgMTNDMS40NDc3MiAxMyAxIDEyLjU1MjMgMSAxMlY5QzEgOC40NDc3MiAxLjQ0NzcxIDggMiA4TDEyIDhaIiBmaWxsPSIjNjE2MTYxIi8+CjxkZWZzPgo8Y2xpcFBhdGggaWQ9ImNsaXAwXzEzN18xOTQ5MiI+CjxyZWN0IGNsYXNzPSJqcC1pY29uMyIgd2lkdGg9IjYiIGhlaWdodD0iNiIgZmlsbD0id2hpdGUiIHRyYW5zZm9ybT0ibWF0cml4KC0xIDAgMCAxIDEwIDEuNTU1NjYpIi8+CjwvY2xpcFBhdGg+CjwvZGVmcz4KPC9zdmc+Cg==);
  --jp-icon-add-below: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPGcgY2xpcC1wYXRoPSJ1cmwoI2NsaXAwXzEzN18xOTQ5OCkiPgo8cGF0aCBjbGFzcz0ianAtaWNvbjMiIGQ9Ik05LjI1IDEwLjA2OTNMNy4zNzUgMTAuMDY5M0w3LjM3NSA4LjE5NDM0QzcuMzc1IDcuOTg4MDkgNy4yMDYyNSA3LjgxOTM0IDcgNy44MTkzNEM2Ljc5Mzc1IDcuODE5MzQgNi42MjUgNy45ODgwOSA2LjYyNSA4LjE5NDM0TDYuNjI1IDEwLjA2OTNMNC43NSAxMC4wNjkzQzQuNTQzNzUgMTAuMDY5MyA0LjM3NSAxMC4yMzgxIDQuMzc1IDEwLjQ0NDNDNC4zNzUgMTAuNjUwNiA0LjU0Mzc1IDEwLjgxOTMgNC43NSAxMC44MTkzTDYuNjI1IDEwLjgxOTNMNi42MjUgMTIuNjk0M0M2LjYyNSAxMi45MDA2IDYuNzkzNzUgMTMuMDY5MyA3IDEzLjA2OTNDNy4yMDYyNSAxMy4wNjkzIDcuMzc1IDEyLjkwMDYgNy4zNzUgMTIuNjk0M0w3LjM3NSAxMC44MTkzTDkuMjUgMTAuODE5M0M5LjQ1NjI1IDEwLjgxOTMgOS42MjUgMTAuNjUwNiA5LjYyNSAxMC40NDQzQzkuNjI1IDEwLjIzODEgOS40NTYyNSAxMC4wNjkzIDkuMjUgMTAuMDY5M1oiIGZpbGw9IiM2MTYxNjEiIHN0cm9rZT0iIzYxNjE2MSIgc3Ryb2tlLXdpZHRoPSIwLjciLz4KPC9nPgo8cGF0aCBjbGFzcz0ianAtaWNvbjMiIGZpbGwtcnVsZT0iZXZlbm9kZCIgY2xpcC1ydWxlPSJldmVub2RkIiBkPSJNMi41IDUuNUwyLjUgMy41TDExLjUgMy41TDExLjUgNS41TDIuNSA1LjVaTTIgN0MxLjQ0NzcyIDcgMSA2LjU1MjI4IDEgNkwxIDNDMSAyLjQ0NzcyIDEuNDQ3NzIgMiAyIDJMMTIgMkMxMi41NTIzIDIgMTMgMi40NDc3MiAxMyAzTDEzIDZDMTMgNi41NTIyOSAxMi41NTIzIDcgMTIgN0wyIDdaIiBmaWxsPSIjNjE2MTYxIi8+CjxkZWZzPgo8Y2xpcFBhdGggaWQ9ImNsaXAwXzEzN18xOTQ5OCI+CjxyZWN0IGNsYXNzPSJqcC1pY29uMyIgd2lkdGg9IjYiIGhlaWdodD0iNiIgZmlsbD0id2hpdGUiIHRyYW5zZm9ybT0ibWF0cml4KDEgMS43NDg0NmUtMDcgMS43NDg0NmUtMDcgLTEgNCAxMy40NDQzKSIvPgo8L2NsaXBQYXRoPgo8L2RlZnM+Cjwvc3ZnPgo=);
  --jp-icon-add: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDEzaC02djZoLTJ2LTZINXYtMmg2VjVoMnY2aDZ2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-bell: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE2IDE2IiB2ZXJzaW9uPSIxLjEiPgogICA8cGF0aCBjbGFzcz0ianAtaWNvbjIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMzMzMzMzIgogICAgICBkPSJtOCAwLjI5Yy0xLjQgMC0yLjcgMC43My0zLjYgMS44LTEuMiAxLjUtMS40IDMuNC0xLjUgNS4yLTAuMTggMi4yLTAuNDQgNC0yLjMgNS4zbDAuMjggMS4zaDVjMC4wMjYgMC42NiAwLjMyIDEuMSAwLjcxIDEuNSAwLjg0IDAuNjEgMiAwLjYxIDIuOCAwIDAuNTItMC40IDAuNi0xIDAuNzEtMS41aDVsMC4yOC0xLjNjLTEuOS0wLjk3LTIuMi0zLjMtMi4zLTUuMy0wLjEzLTEuOC0wLjI2LTMuNy0xLjUtNS4yLTAuODUtMS0yLjItMS44LTMuNi0xLjh6bTAgMS40YzAuODggMCAxLjkgMC41NSAyLjUgMS4zIDAuODggMS4xIDEuMSAyLjcgMS4yIDQuNCAwLjEzIDEuNyAwLjIzIDMuNiAxLjMgNS4yaC0xMGMxLjEtMS42IDEuMi0zLjQgMS4zLTUuMiAwLjEzLTEuNyAwLjMtMy4zIDEuMi00LjQgMC41OS0wLjcyIDEuNi0xLjMgMi41LTEuM3ptLTAuNzQgMTJoMS41Yy0wLjAwMTUgMC4yOCAwLjAxNSAwLjc5LTAuNzQgMC43OS0wLjczIDAuMDAxNi0wLjcyLTAuNTMtMC43NC0wLjc5eiIgLz4KPC9zdmc+Cg==);
  --jp-icon-bug-dot: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiPgogICAgICAgIDxwYXRoIGZpbGwtcnVsZT0iZXZlbm9kZCIgY2xpcC1ydWxlPSJldmVub2RkIiBkPSJNMTcuMTkgOEgyMFYxMEgxNy45MUMxNy45NiAxMC4zMyAxOCAxMC42NiAxOCAxMVYxMkgyMFYxNEgxOC41SDE4VjE0LjAyNzVDMTUuNzUgMTQuMjc2MiAxNCAxNi4xODM3IDE0IDE4LjVDMTQgMTkuMjA4IDE0LjE2MzUgMTkuODc3OSAxNC40NTQ5IDIwLjQ3MzlDMTMuNzA2MyAyMC44MTE3IDEyLjg3NTcgMjEgMTIgMjFDOS43OCAyMSA3Ljg1IDE5Ljc5IDYuODEgMThINFYxNkg2LjA5QzYuMDQgMTUuNjcgNiAxNS4zNCA2IDE1VjE0SDRWMTJINlYxMUM2IDEwLjY2IDYuMDQgMTAuMzMgNi4wOSAxMEg0VjhINi44MUM3LjI2IDcuMjIgNy44OCA2LjU1IDguNjIgNi4wNEw3IDQuNDFMOC40MSAzTDEwLjU5IDUuMTdDMTEuMDQgNS4wNiAxMS41MSA1IDEyIDVDMTIuNDkgNSAxMi45NiA1LjA2IDEzLjQyIDUuMTdMMTUuNTkgM0wxNyA0LjQxTDE1LjM3IDYuMDRDMTYuMTIgNi41NSAxNi43NCA3LjIyIDE3LjE5IDhaTTEwIDE2SDE0VjE0SDEwVjE2Wk0xMCAxMkgxNFYxMEgxMFYxMloiIGZpbGw9IiM2MTYxNjEiLz4KICAgICAgICA8cGF0aCBkPSJNMjIgMTguNUMyMiAyMC40MzMgMjAuNDMzIDIyIDE4LjUgMjJDMTYuNTY3IDIyIDE1IDIwLjQzMyAxNSAxOC41QzE1IDE2LjU2NyAxNi41NjcgMTUgMTguNSAxNUMyMC40MzMgMTUgMjIgMTYuNTY3IDIyIDE4LjVaIiBmaWxsPSIjNjE2MTYxIi8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-bug: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0yMCA4aC0yLjgxYy0uNDUtLjc4LTEuMDctMS40NS0xLjgyLTEuOTZMMTcgNC40MSAxNS41OSAzbC0yLjE3IDIuMTdDMTIuOTYgNS4wNiAxMi40OSA1IDEyIDVjLS40OSAwLS45Ni4wNi0xLjQxLjE3TDguNDEgMyA3IDQuNDFsMS42MiAxLjYzQzcuODggNi41NSA3LjI2IDcuMjIgNi44MSA4SDR2MmgyLjA5Yy0uMDUuMzMtLjA5LjY2LS4wOSAxdjFINHYyaDJ2MWMwIC4zNC4wNC42Ny4wOSAxSDR2MmgyLjgxYzEuMDQgMS43OSAyLjk3IDMgNS4xOSAzczQuMTUtMS4yMSA1LjE5LTNIMjB2LTJoLTIuMDljLjA1LS4zMy4wOS0uNjYuMDktMXYtMWgydi0yaC0ydi0xYzAtLjM0LS4wNC0uNjctLjA5LTFIMjBWOHptLTYgOGgtNHYtMmg0djJ6bTAtNGgtNHYtMmg0djJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-build: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE0LjkgMTcuNDVDMTYuMjUgMTcuNDUgMTcuMzUgMTYuMzUgMTcuMzUgMTVDMTcuMzUgMTMuNjUgMTYuMjUgMTIuNTUgMTQuOSAxMi41NUMxMy41NCAxMi41NSAxMi40NSAxMy42NSAxMi40NSAxNUMxMi40NSAxNi4zNSAxMy41NCAxNy40NSAxNC45IDE3LjQ1Wk0yMC4xIDE1LjY4TDIxLjU4IDE2Ljg0QzIxLjcxIDE2Ljk1IDIxLjc1IDE3LjEzIDIxLjY2IDE3LjI5TDIwLjI2IDE5LjcxQzIwLjE3IDE5Ljg2IDIwIDE5LjkyIDE5LjgzIDE5Ljg2TDE4LjA5IDE5LjE2QzE3LjczIDE5LjQ0IDE3LjMzIDE5LjY3IDE2LjkxIDE5Ljg1TDE2LjY0IDIxLjdDMTYuNjIgMjEuODcgMTYuNDcgMjIgMTYuMyAyMkgxMy41QzEzLjMyIDIyIDEzLjE4IDIxLjg3IDEzLjE1IDIxLjdMMTIuODkgMTkuODVDMTIuNDYgMTkuNjcgMTIuMDcgMTkuNDQgMTEuNzEgMTkuMTZMOS45NjAwMiAxOS44NkM5LjgxMDAyIDE5LjkyIDkuNjIwMDIgMTkuODYgOS41NDAwMiAxOS43MUw4LjE0MDAyIDE3LjI5QzguMDUwMDIgMTcuMTMgOC4wOTAwMiAxNi45NSA4LjIyMDAyIDE2Ljg0TDkuNzAwMDIgMTUuNjhMOS42NTAwMSAxNUw5LjcwMDAyIDE0LjMxTDguMjIwMDIgMTMuMTZDOC4wOTAwMiAxMy4wNSA4LjA1MDAyIDEyLjg2IDguMTQwMDIgMTIuNzFMOS41NDAwMiAxMC4yOUM5LjYyMDAyIDEwLjEzIDkuODEwMDIgMTAuMDcgOS45NjAwMiAxMC4xM0wxMS43MSAxMC44NEMxMi4wNyAxMC41NiAxMi40NiAxMC4zMiAxMi44OSAxMC4xNUwxMy4xNSA4LjI4OTk4QzEzLjE4IDguMTI5OTggMTMuMzIgNy45OTk5OCAxMy41IDcuOTk5OThIMTYuM0MxNi40NyA3Ljk5OTk4IDE2LjYyIDguMTI5OTggMTYuNjQgOC4yODk5OEwxNi45MSAxMC4xNUMxNy4zMyAxMC4zMiAxNy43MyAxMC41NiAxOC4wOSAxMC44NEwxOS44MyAxMC4xM0MyMCAxMC4wNyAyMC4xNyAxMC4xMyAyMC4yNiAxMC4yOUwyMS42NiAxMi43MUMyMS43NSAxMi44NiAyMS43MSAxMy4wNSAyMS41OCAxMy4xNkwyMC4xIDE0LjMxTDIwLjE1IDE1TDIwLjEgMTUuNjhaIi8+CiAgICA8cGF0aCBkPSJNNy4zMjk2NiA3LjQ0NDU0QzguMDgzMSA3LjAwOTU0IDguMzM5MzIgNi4wNTMzMiA3LjkwNDMyIDUuMjk5ODhDNy40NjkzMiA0LjU0NjQzIDYuNTA4MSA0LjI4MTU2IDUuNzU0NjYgNC43MTY1NkM1LjM5MTc2IDQuOTI2MDggNS4xMjY5NSA1LjI3MTE4IDUuMDE4NDkgNS42NzU5NEM0LjkxMDA0IDYuMDgwNzEgNC45NjY4MiA2LjUxMTk4IDUuMTc2MzQgNi44NzQ4OEM1LjYxMTM0IDcuNjI4MzIgNi41NzYyMiA3Ljg3OTU0IDcuMzI5NjYgNy40NDQ1NFpNOS42NTcxOCA0Ljc5NTkzTDEwLjg2NzIgNC45NTE3OUMxMC45NjI4IDQuOTc3NDEgMTEuMDQwMiA1LjA3MTMzIDExLjAzODIgNS4xODc5M0wxMS4wMzg4IDYuOTg4OTNDMTEuMDQ1NSA3LjEwMDU0IDEwLjk2MTYgNy4xOTUxOCAxMC44NTUgNy4yMTA1NEw5LjY2MDAxIDcuMzgwODNMOS4yMzkxNSA4LjEzMTg4TDkuNjY5NjEgOS4yNTc0NUM5LjcwNzI5IDkuMzYyNzEgOS42NjkzNCA5LjQ3Njk5IDkuNTc0MDggOS41MzE5OUw4LjAxNTIzIDEwLjQzMkM3LjkxMTMxIDEwLjQ5MiA3Ljc5MzM3IDEwLjQ2NzcgNy43MjEwNSAxMC4zODI0TDYuOTg3NDggOS40MzE4OEw2LjEwOTMxIDkuNDMwODNMNS4zNDcwNCAxMC4zOTA1QzUuMjg5MDkgMTAuNDcwMiA1LjE3MzgzIDEwLjQ5MDUgNS4wNzE4NyAxMC40MzM5TDMuNTEyNDUgOS41MzI5M0MzLjQxMDQ5IDkuNDc2MzMgMy4zNzY0NyA5LjM1NzQxIDMuNDEwNzUgOS4yNTY3OUwzLjg2MzQ3IDguMTQwOTNMMy42MTc0OSA3Ljc3NDg4TDMuNDIzNDcgNy4zNzg4M0wyLjIzMDc1IDcuMjEyOTdDMi4xMjY0NyA3LjE5MjM1IDIuMDQwNDkgNy4xMDM0MiAyLjA0MjQ1IDYuOTg2ODJMMi4wNDE4NyA1LjE4NTgyQzIuMDQzODMgNS4wNjkyMiAyLjExOTA5IDQuOTc5NTggMi4yMTcwNCA0Ljk2OTIyTDMuNDIwNjUgNC43OTM5M0wzLjg2NzQ5IDQuMDI3ODhMMy40MTEwNSAyLjkxNzMxQzMuMzczMzcgMi44MTIwNCAzLjQxMTMxIDIuNjk3NzYgMy41MTUyMyAyLjYzNzc2TDUuMDc0MDggMS43Mzc3NkM1LjE2OTM0IDEuNjgyNzYgNS4yODcyOSAxLjcwNzA0IDUuMzU5NjEgMS43OTIzMUw2LjExOTE1IDIuNzI3ODhMNi45ODAwMSAyLjczODkzTDcuNzI0OTYgMS43ODkyMkM3Ljc5MTU2IDEuNzA0NTggNy45MTU0OCAxLjY3OTIyIDguMDA4NzkgMS43NDA4Mkw5LjU2ODIxIDIuNjQxODJDOS42NzAxNyAyLjY5ODQyIDkuNzEyODUgMi44MTIzNCA5LjY4NzIzIDIuOTA3OTdMOS4yMTcxOCA0LjAzMzgzTDkuNDYzMTYgNC4zOTk4OEw5LjY1NzE4IDQuNzk1OTNaIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iOS45LDEzLjYgMy42LDcuNCA0LjQsNi42IDkuOSwxMi4yIDE1LjQsNi43IDE2LjEsNy40ICIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNS45TDksOS43bDMuOC0zLjhsMS4yLDEuMmwtNC45LDVsLTQuOS01TDUuMiw1Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNy41TDksMTEuMmwzLjgtMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-left: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik0xMC44LDEyLjhMNy4xLDlsMy44LTMuOGwwLDcuNkgxMC44eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-right: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik03LjIsNS4yTDEwLjksOWwtMy44LDMuOFY1LjJINy4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-up-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTUuNCwxMy4zIDkuOSw3LjcgNC40LDEzLjIgMy42LDEyLjUgOS45LDYuMyAxNi4xLDEyLjYgIi8+Cgk8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-up: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik01LjIsMTAuNUw5LDYuOGwzLjgsMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-case-sensitive: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWFjY2VudDIiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTcuNiw4aDAuOWwzLjUsOGgtMS4xTDEwLDE0SDZsLTAuOSwySDRMNy42LDh6IE04LDkuMUw2LjQsMTNoMy4yTDgsOS4xeiIvPgogICAgPHBhdGggZD0iTTE2LjYsOS44Yy0wLjIsMC4xLTAuNCwwLjEtMC43LDAuMWMtMC4yLDAtMC40LTAuMS0wLjYtMC4yYy0wLjEtMC4xLTAuMi0wLjQtMC4yLTAuNyBjLTAuMywwLjMtMC42LDAuNS0wLjksMC43Yy0wLjMsMC4xLTAuNywwLjItMS4xLDAuMmMtMC4zLDAtMC41LDAtMC43LTAuMWMtMC4yLTAuMS0wLjQtMC4yLTAuNi0wLjNjLTAuMi0wLjEtMC4zLTAuMy0wLjQtMC41IGMtMC4xLTAuMi0wLjEtMC40LTAuMS0wLjdjMC0wLjMsMC4xLTAuNiwwLjItMC44YzAuMS0wLjIsMC4zLTAuNCwwLjQtMC41QzEyLDcsMTIuMiw2LjksMTIuNSw2LjhjMC4yLTAuMSwwLjUtMC4xLDAuNy0wLjIgYzAuMy0wLjEsMC41LTAuMSwwLjctMC4xYzAuMiwwLDAuNC0wLjEsMC42LTAuMWMwLjIsMCwwLjMtMC4xLDAuNC0wLjJjMC4xLTAuMSwwLjItMC4yLDAuMi0wLjRjMC0xLTEuMS0xLTEuMy0xIGMtMC40LDAtMS40LDAtMS40LDEuMmgtMC45YzAtMC40LDAuMS0wLjcsMC4yLTFjMC4xLTAuMiwwLjMtMC40LDAuNS0wLjZjMC4yLTAuMiwwLjUtMC4zLDAuOC0wLjNDMTMuMyw0LDEzLjYsNCwxMy45LDQgYzAuMywwLDAuNSwwLDAuOCwwLjFjMC4zLDAsMC41LDAuMSwwLjcsMC4yYzAuMiwwLjEsMC40LDAuMywwLjUsMC41QzE2LDUsMTYsNS4yLDE2LDUuNnYyLjljMCwwLjIsMCwwLjQsMCwwLjUgYzAsMC4xLDAuMSwwLjIsMC4zLDAuMmMwLjEsMCwwLjIsMCwwLjMsMFY5Ljh6IE0xNS4yLDYuOWMtMS4yLDAuNi0zLjEsMC4yLTMuMSwxLjRjMCwxLjQsMy4xLDEsMy4xLTAuNVY2Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik05IDE2LjE3TDQuODMgMTJsLTEuNDIgMS40MUw5IDE5IDIxIDdsLTEuNDEtMS40MXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-circle-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDJDNi40NyAyIDIgNi40NyAyIDEyczQuNDcgMTAgMTAgMTAgMTAtNC40NyAxMC0xMFMxNy41MyAyIDEyIDJ6bTAgMThjLTQuNDEgMC04LTMuNTktOC04czMuNTktOCA4LTggOCAzLjU5IDggOC0zLjU5IDgtOCA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-circle: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iOSIgY3k9IjkiIHI9IjgiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-clear: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8bWFzayBpZD0iZG9udXRIb2xlIj4KICAgIDxyZWN0IHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgZmlsbD0id2hpdGUiIC8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSI4IiBmaWxsPSJibGFjayIvPgogIDwvbWFzaz4KCiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxyZWN0IGhlaWdodD0iMTgiIHdpZHRoPSIyIiB4PSIxMSIgeT0iMyIgdHJhbnNmb3JtPSJyb3RhdGUoMzE1LCAxMiwgMTIpIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIgbWFzaz0idXJsKCNkb251dEhvbGUpIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-close: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1ub25lIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIGpwLWljb24zLWhvdmVyIiBmaWxsPSJub25lIj4KICAgIDxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjExIi8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIGpwLWljb24tYWNjZW50Mi1ob3ZlciIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMTkgNi40MUwxNy41OSA1IDEyIDEwLjU5IDYuNDEgNSA1IDYuNDEgMTAuNTkgMTIgNSAxNy41OSA2LjQxIDE5IDEyIDEzLjQxIDE3LjU5IDE5IDE5IDE3LjU5IDEzLjQxIDEyeiIvPgogIDwvZz4KCiAgPGcgY2xhc3M9ImpwLWljb24tbm9uZSBqcC1pY29uLWJ1c3kiIGZpbGw9Im5vbmUiPgogICAgPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-code-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBzaGFwZS1yZW5kZXJpbmc9Imdlb21ldHJpY1ByZWNpc2lvbiI+CiAgICA8cGF0aCBkPSJNNi41OSwzLjQxTDIsOEw2LjU5LDEyLjZMOCwxMS4xOEw0LjgyLDhMOCw0LjgyTDYuNTksMy40MU0xMi40MSwzLjQxTDExLDQuODJMMTQuMTgsOEwxMSwxMS4xOEwxMi40MSwxMi42TDE3LDhMMTIuNDEsMy40MU0yMS41OSwxMS41OUwxMy41LDE5LjY4TDkuODMsMTZMOC40MiwxNy40MUwxMy41LDIyLjVMMjMsMTNMMjEuNTksMTEuNTlaIiAvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-code: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTExLjQgMTguNkw2LjggMTRMMTEuNCA5LjRMMTAgOEw0IDE0TDEwIDIwTDExLjQgMTguNlpNMTYuNiAxOC42TDIxLjIgMTRMMTYuNiA5LjRMMTggOEwyNCAxNEwxOCAyMEwxNi42IDE4LjZWMTguNloiLz4KCTwvZz4KPC9zdmc+Cg==);
  --jp-icon-collapse-all: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTggMmMxIDAgMTEgMCAxMiAwczIgMSAyIDJjMCAxIDAgMTEgMCAxMnMwIDItMiAyQzIwIDE0IDIwIDQgMjAgNFMxMCA0IDYgNGMwLTIgMS0yIDItMnoiIC8+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTE4IDhjMC0xLTEtMi0yLTJTNSA2IDQgNnMtMiAxLTIgMmMwIDEgMCAxMSAwIDEyczEgMiAyIDJjMSAwIDExIDAgMTIgMHMyLTEgMi0yYzAtMSAwLTExIDAtMTJ6bS0yIDB2MTJINFY4eiIgLz4KICAgICAgICA8cGF0aCBkPSJNNiAxM3YyaDh2LTJ6IiAvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-console: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwMCAyMDAiPgogIDxnIGNsYXNzPSJqcC1jb25zb2xlLWljb24tYmFja2dyb3VuZC1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMjg4RDEiPgogICAgPHBhdGggZD0iTTIwIDE5LjhoMTYwdjE1OS45SDIweiIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtY29uc29sZS1pY29uLWNvbG9yIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIj4KICAgIDxwYXRoIGQ9Ik0xMDUgMTI3LjNoNDB2MTIuOGgtNDB6TTUxLjEgNzdMNzQgOTkuOWwtMjMuMyAyMy4zIDEwLjUgMTAuNSAyMy4zLTIzLjNMOTUgOTkuOSA4NC41IDg5LjQgNjEuNiA2Ni41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-copy: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTExLjksMUgzLjJDMi40LDEsMS43LDEuNywxLjcsMi41djEwLjJoMS41VjIuNWg4LjdWMXogTTE0LjEsMy45aC04Yy0wLjgsMC0xLjUsMC43LTEuNSwxLjV2MTAuMmMwLDAuOCwwLjcsMS41LDEuNSwxLjVoOCBjMC44LDAsMS41LTAuNywxLjUtMS41VjUuNEMxNS41LDQuNiwxNC45LDMuOSwxNC4xLDMuOXogTTE0LjEsMTUuNWgtOFY1LjRoOFYxNS41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-copyright: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGVuYWJsZS1iYWNrZ3JvdW5kPSJuZXcgMCAwIDI0IDI0IiBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCI+CiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0xMS44OCw5LjE0YzEuMjgsMC4wNiwxLjYxLDEuMTUsMS42MywxLjY2aDEuNzljLTAuMDgtMS45OC0xLjQ5LTMuMTktMy40NS0zLjE5QzkuNjQsNy42MSw4LDksOCwxMi4xNCBjMCwxLjk0LDAuOTMsNC4yNCwzLjg0LDQuMjRjMi4yMiwwLDMuNDEtMS42NSwzLjQ0LTIuOTVoLTEuNzljLTAuMDMsMC41OS0wLjQ1LDEuMzgtMS42MywxLjQ0QzEwLjU1LDE0LjgzLDEwLDEzLjgxLDEwLDEyLjE0IEMxMCw5LjI1LDExLjI4LDkuMTYsMTEuODgsOS4xNHogTTEyLDJDNi40OCwyLDIsNi40OCwyLDEyczQuNDgsMTAsMTAsMTBzMTAtNC40OCwxMC0xMFMxNy41MiwyLDEyLDJ6IE0xMiwyMGMtNC40MSwwLTgtMy41OS04LTggczMuNTktOCw4LThzOCwzLjU5LDgsOFMxNi40MSwyMCwxMiwyMHoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-cut: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkuNjQgNy42NGMuMjMtLjUuMzYtMS4wNS4zNi0xLjY0IDAtMi4yMS0xLjc5LTQtNC00UzIgMy43OSAyIDZzMS43OSA0IDQgNGMuNTkgMCAxLjE0LS4xMyAxLjY0LS4zNkwxMCAxMmwtMi4zNiAyLjM2QzcuMTQgMTQuMTMgNi41OSAxNCA2IDE0Yy0yLjIxIDAtNCAxLjc5LTQgNHMxLjc5IDQgNCA0IDQtMS43OSA0LTRjMC0uNTktLjEzLTEuMTQtLjM2LTEuNjRMMTIgMTRsNyA3aDN2LTFMOS42NCA3LjY0ek02IDhjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTAgMTJjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTYtNy41Yy0uMjggMC0uNS0uMjItLjUtLjVzLjIyLS41LjUtLjUuNS4yMi41LjUtLjIyLjUtLjUuNXpNMTkgM2wtNiA2IDIgMiA3LTdWM3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-delete: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2cHgiIGhlaWdodD0iMTZweCI+CiAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIiAvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjI2MjYyIiBkPSJNNiAxOWMwIDEuMS45IDIgMiAyaDhjMS4xIDAgMi0uOSAyLTJWN0g2djEyek0xOSA0aC0zLjVsLTEtMWgtNWwtMSAxSDV2MmgxNFY0eiIgLz4KPC9zdmc+Cg==);
  --jp-icon-download: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDloLTRWM0g5djZINWw3IDcgNy03ek01IDE4djJoMTR2LTJINXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-duplicate: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTIuNzk5OTggMC44NzVIOC44OTU4MkM5LjIwMDYxIDAuODc1IDkuNDQ5OTggMS4xMzkxNCA5LjQ0OTk4IDEuNDYxOThDOS40NDk5OCAxLjc4NDgyIDkuMjAwNjEgMi4wNDg5NiA4Ljg5NTgyIDIuMDQ4OTZIMy4zNTQxNUMzLjA0OTM2IDIuMDQ4OTYgMi43OTk5OCAyLjMxMzEgMi43OTk5OCAyLjYzNTk0VjkuNjc5NjlDMi43OTk5OCAxMC4wMDI1IDIuNTUwNjEgMTAuMjY2NyAyLjI0NTgyIDEwLjI2NjdDMS45NDEwMyAxMC4yNjY3IDEuNjkxNjUgMTAuMDAyNSAxLjY5MTY1IDkuNjc5NjlWMi4wNDg5NkMxLjY5MTY1IDEuNDAzMjggMi4xOTA0IDAuODc1IDIuNzk5OTggMC44NzVaTTUuMzY2NjUgMTEuOVY0LjU1SDExLjA4MzNWMTEuOUg1LjM2NjY1Wk00LjE0MTY1IDQuMTQxNjdDNC4xNDE2NSAzLjY5MDYzIDQuNTA3MjggMy4zMjUgNC45NTgzMiAzLjMyNUgxMS40OTE3QzExLjk0MjcgMy4zMjUgMTIuMzA4MyAzLjY5MDYzIDEyLjMwODMgNC4xNDE2N1YxMi4zMDgzQzEyLjMwODMgMTIuNzU5NCAxMS45NDI3IDEzLjEyNSAxMS40OTE3IDEzLjEyNUg0Ljk1ODMyQzQuNTA3MjggMTMuMTI1IDQuMTQxNjUgMTIuNzU5NCA0LjE0MTY1IDEyLjMwODNWNC4xNDE2N1oiIGZpbGw9IiM2MTYxNjEiLz4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBkPSJNOS40MzU3NCA4LjI2NTA3SDguMzY0MzFWOS4zMzY1QzguMzY0MzEgOS40NTQzNSA4LjI2Nzg4IDkuNTUwNzggOC4xNTAwMiA5LjU1MDc4QzguMDMyMTcgOS41NTA3OCA3LjkzNTc0IDkuNDU0MzUgNy45MzU3NCA5LjMzNjVWOC4yNjUwN0g2Ljg2NDMxQzYuNzQ2NDUgOC4yNjUwNyA2LjY1MDAyIDguMTY4NjQgNi42NTAwMiA4LjA1MDc4QzYuNjUwMDIgNy45MzI5MiA2Ljc0NjQ1IDcuODM2NSA2Ljg2NDMxIDcuODM2NUg3LjkzNTc0VjYuNzY1MDdDNy45MzU3NCA2LjY0NzIxIDguMDMyMTcgNi41NTA3OCA4LjE1MDAyIDYuNTUwNzhDOC4yNjc4OCA2LjU1MDc4IDguMzY0MzEgNi42NDcyMSA4LjM2NDMxIDYuNzY1MDdWNy44MzY1SDkuNDM1NzRDOS41NTM2IDcuODM2NSA5LjY1MDAyIDcuOTMyOTIgOS42NTAwMiA4LjA1MDc4QzkuNjUwMDIgOC4xNjg2NCA5LjU1MzYgOC4yNjUwNyA5LjQzNTc0IDguMjY1MDdaIiBmaWxsPSIjNjE2MTYxIiBzdHJva2U9IiM2MTYxNjEiIHN0cm9rZS13aWR0aD0iMC41Ii8+Cjwvc3ZnPgo=);
  --jp-icon-edit: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMgMTcuMjVWMjFoMy43NUwxNy44MSA5Ljk0bC0zLjc1LTMuNzVMMyAxNy4yNXpNMjAuNzEgNy4wNGMuMzktLjM5LjM5LTEuMDIgMC0xLjQxbC0yLjM0LTIuMzRjLS4zOS0uMzktMS4wMi0uMzktMS40MSAwbC0xLjgzIDEuODMgMy43NSAzLjc1IDEuODMtMS44M3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-ellipses: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iNSIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxOSIgY3k9IjEyIiByPSIyIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-error: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj48Y2lyY2xlIGN4PSIxMiIgY3k9IjE5IiByPSIyIi8+PHBhdGggZD0iTTEwIDNoNHYxMmgtNHoiLz48L2c+CjxwYXRoIGZpbGw9Im5vbmUiIGQ9Ik0wIDBoMjR2MjRIMHoiLz4KPC9zdmc+Cg==);
  --jp-icon-expand-all: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTggMmMxIDAgMTEgMCAxMiAwczIgMSAyIDJjMCAxIDAgMTEgMCAxMnMwIDItMiAyQzIwIDE0IDIwIDQgMjAgNFMxMCA0IDYgNGMwLTIgMS0yIDItMnoiIC8+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTE4IDhjMC0xLTEtMi0yLTJTNSA2IDQgNnMtMiAxLTIgMmMwIDEgMCAxMSAwIDEyczEgMiAyIDJjMSAwIDExIDAgMTIgMHMyLTEgMi0yYzAtMSAwLTExIDAtMTJ6bS0yIDB2MTJINFY4eiIgLz4KICAgICAgICA8cGF0aCBkPSJNMTEgMTBIOXYzSDZ2MmgzdjNoMnYtM2gzdi0yaC0zeiIgLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-extension: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwLjUgMTFIMTlWN2MwLTEuMS0uOS0yLTItMmgtNFYzLjVDMTMgMi4xMiAxMS44OCAxIDEwLjUgMVM4IDIuMTIgOCAzLjVWNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAydjMuOEgzLjVjMS40OSAwIDIuNyAxLjIxIDIuNyAyLjdzLTEuMjEgMi43LTIuNyAyLjdIMlYyMGMwIDEuMS45IDIgMiAyaDMuOHYtMS41YzAtMS40OSAxLjIxLTIuNyAyLjctMi43IDEuNDkgMCAyLjcgMS4yMSAyLjcgMi43VjIySDE3YzEuMSAwIDItLjkgMi0ydi00aDEuNWMxLjM4IDAgMi41LTEuMTIgMi41LTIuNVMyMS44OCAxMSAyMC41IDExeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-fast-forward: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTQgMThsOC41LTZMNCA2djEyem05LTEydjEybDguNS02TDEzIDZ6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-file-upload: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTZoNnYtNmg0bC03LTctNyA3aDR6bS00IDJoMTR2Mkg1eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-file: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuMyA4LjJsLTUuNS01LjVjLS4zLS4zLS43LS41LTEuMi0uNUgzLjljLS44LjEtMS42LjktMS42IDEuOHYxNC4xYzAgLjkuNyAxLjYgMS42IDEuNmgxNC4yYy45IDAgMS42LS43IDEuNi0xLjZWOS40Yy4xLS41LS4xLS45LS40LTEuMnptLTUuOC0zLjNsMy40IDMuNmgtMy40VjQuOXptMy45IDEyLjdINC43Yy0uMSAwLS4yIDAtLjItLjJWNC43YzAtLjIuMS0uMy4yLS4zaDcuMnY0LjRzMCAuOC4zIDEuMWMuMy4zIDEuMS4zIDEuMS4zaDQuM3Y3LjJzLS4xLjItLjIuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-filter-dot: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTE0LDEyVjE5Ljg4QzE0LjA0LDIwLjE4IDEzLjk0LDIwLjUgMTMuNzEsMjAuNzFDMTMuMzIsMjEuMSAxMi42OSwyMS4xIDEyLjMsMjAuNzFMMTAuMjksMTguN0MxMC4wNiwxOC40NyA5Ljk2LDE4LjE2IDEwLDE3Ljg3VjEySDkuOTdMNC4yMSw0LjYyQzMuODcsNC4xOSAzLjk1LDMuNTYgNC4zOCwzLjIyQzQuNTcsMy4wOCA0Ljc4LDMgNSwzVjNIMTlWM0MxOS4yMiwzIDE5LjQzLDMuMDggMTkuNjIsMy4yMkMyMC4wNSwzLjU2IDIwLjEzLDQuMTkgMTkuNzksNC42MkwxNC4wMywxMkgxNFoiIC8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWRvdCIgZmlsbD0iI0ZGRiI+CiAgICA8Y2lyY2xlIGN4PSIxOCIgY3k9IjE3IiByPSIzIj48L2NpcmNsZT4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-filter-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEwIDE4aDR2LTJoLTR2MnpNMyA2djJoMThWNkgzem0zIDdoMTJ2LTJINnYyeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-filter: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTE0LDEyVjE5Ljg4QzE0LjA0LDIwLjE4IDEzLjk0LDIwLjUgMTMuNzEsMjAuNzFDMTMuMzIsMjEuMSAxMi42OSwyMS4xIDEyLjMsMjAuNzFMMTAuMjksMTguN0MxMC4wNiwxOC40NyA5Ljk2LDE4LjE2IDEwLDE3Ljg3VjEySDkuOTdMNC4yMSw0LjYyQzMuODcsNC4xOSAzLjk1LDMuNTYgNC4zOCwzLjIyQzQuNTcsMy4wOCA0Ljc4LDMgNSwzVjNIMTlWM0MxOS4yMiwzIDE5LjQzLDMuMDggMTkuNjIsMy4yMkMyMC4wNSwzLjU2IDIwLjEzLDQuMTkgMTkuNzksNC42MkwxNC4wMywxMkgxNFoiIC8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-folder-favorite: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjRweCIgdmlld0JveD0iMCAwIDI0IDI0IiB3aWR0aD0iMjRweCIgZmlsbD0iIzAwMDAwMCI+CiAgPHBhdGggZD0iTTAgMGgyNHYyNEgwVjB6IiBmaWxsPSJub25lIi8+PHBhdGggY2xhc3M9ImpwLWljb24zIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxNjE2MSIgZD0iTTIwIDZoLThsLTItMkg0Yy0xLjEgMC0yIC45LTIgMnYxMmMwIDEuMS45IDIgMiAyaDE2YzEuMSAwIDItLjkgMi0yVjhjMC0xLjEtLjktMi0yLTJ6bS0yLjA2IDExTDE1IDE1LjI4IDEyLjA2IDE3bC43OC0zLjMzLTIuNTktMi4yNCAzLjQxLS4yOUwxNSA4bDEuMzQgMy4xNCAzLjQxLjI5LTIuNTkgMi4yNC43OCAzLjMzeiIvPgo8L3N2Zz4K);
  --jp-icon-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY4YzAtMS4xLS45LTItMi0yaC04bC0yLTJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-home: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjRweCIgdmlld0JveD0iMCAwIDI0IDI0IiB3aWR0aD0iMjRweCIgZmlsbD0iIzAwMDAwMCI+CiAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPjxwYXRoIGNsYXNzPSJqcC1pY29uMyBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xMCAyMHYtNmg0djZoNXYtOGgzTDEyIDMgMiAxMmgzdjh6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-html5: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMDAiIGQ9Ik0xMDguNCAwaDIzdjIyLjhoMjEuMlYwaDIzdjY5aC0yM1Y0NmgtMjF2MjNoLTIzLjJNMjA2IDIzaC0yMC4zVjBoNjMuN3YyM0gyMjl2NDZoLTIzbTUzLjUtNjloMjQuMWwxNC44IDI0LjNMMzEzLjIgMGgyNC4xdjY5aC0yM1YzNC44bC0xNi4xIDI0LjgtMTYuMS0yNC44VjY5aC0yMi42bTg5LjItNjloMjN2NDYuMmgzMi42VjY5aC01NS42Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2U0NGQyNiIgZD0iTTEwNy42IDQ3MWwtMzMtMzcwLjRoMzYyLjhsLTMzIDM3MC4yTDI1NS43IDUxMiIvPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNmMTY1MjkiIGQ9Ik0yNTYgNDgwLjVWMTMxaDE0OC4zTDM3NiA0NDciLz4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNlYmViZWIiIGQ9Ik0xNDIgMTc2LjNoMTE0djQ1LjRoLTY0LjJsNC4yIDQ2LjVoNjB2NDUuM0gxNTQuNG0yIDIyLjhIMjAybDMuMiAzNi4zIDUwLjggMTMuNnY0Ny40bC05My4yLTI2Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIiBkPSJNMzY5LjYgMTc2LjNIMjU1Ljh2NDUuNGgxMDkuNm0tNC4xIDQ2LjVIMjU1Ljh2NDUuNGg1NmwtNS4zIDU5LTUwLjcgMTMuNnY0Ny4ybDkzLTI1LjgiLz4KPC9zdmc+Cg==);
  --jp-icon-image: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1icmFuZDQganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNGRkYiIGQ9Ik0yLjIgMi4yaDE3LjV2MTcuNUgyLjJ6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzNGNTFCNSIgZD0iTTIuMiAyLjJ2MTcuNWgxNy41bC4xLTE3LjVIMi4yem0xMi4xIDIuMmMxLjIgMCAyLjIgMSAyLjIgMi4ycy0xIDIuMi0yLjIgMi4yLTIuMi0xLTIuMi0yLjIgMS0yLjIgMi4yLTIuMnpNNC40IDE3LjZsMy4zLTguOCAzLjMgNi42IDIuMi0zLjIgNC40IDUuNEg0LjR6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-info: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUwLjk3OCA1MC45NzgiPgoJPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KCQk8cGF0aCBkPSJNNDMuNTIsNy40NThDMzguNzExLDIuNjQ4LDMyLjMwNywwLDI1LjQ4OSwwQzE4LjY3LDAsMTIuMjY2LDIuNjQ4LDcuNDU4LDcuNDU4CgkJCWMtOS45NDMsOS45NDEtOS45NDMsMjYuMTE5LDAsMzYuMDYyYzQuODA5LDQuODA5LDExLjIxMiw3LjQ1NiwxOC4wMzEsNy40NThjMCwwLDAuMDAxLDAsMC4wMDIsMAoJCQljNi44MTYsMCwxMy4yMjEtMi42NDgsMTguMDI5LTcuNDU4YzQuODA5LTQuODA5LDcuNDU3LTExLjIxMiw3LjQ1Ny0xOC4wM0M1MC45NzcsMTguNjcsNDguMzI4LDEyLjI2Niw0My41Miw3LjQ1OHoKCQkJIE00Mi4xMDYsNDIuMTA1Yy00LjQzMiw0LjQzMS0xMC4zMzIsNi44NzItMTYuNjE1LDYuODcyaC0wLjAwMmMtNi4yODUtMC4wMDEtMTIuMTg3LTIuNDQxLTE2LjYxNy02Ljg3MgoJCQljLTkuMTYyLTkuMTYzLTkuMTYyLTI0LjA3MSwwLTMzLjIzM0MxMy4zMDMsNC40NCwxOS4yMDQsMiwyNS40ODksMmM2LjI4NCwwLDEyLjE4NiwyLjQ0LDE2LjYxNyw2Ljg3MgoJCQljNC40MzEsNC40MzEsNi44NzEsMTAuMzMyLDYuODcxLDE2LjYxN0M0OC45NzcsMzEuNzcyLDQ2LjUzNiwzNy42NzUsNDIuMTA2LDQyLjEwNXoiLz4KCQk8cGF0aCBkPSJNMjMuNTc4LDMyLjIxOGMtMC4wMjMtMS43MzQsMC4xNDMtMy4wNTksMC40OTYtMy45NzJjMC4zNTMtMC45MTMsMS4xMS0xLjk5NywyLjI3Mi0zLjI1MwoJCQljMC40NjgtMC41MzYsMC45MjMtMS4wNjIsMS4zNjctMS41NzVjMC42MjYtMC43NTMsMS4xMDQtMS40NzgsMS40MzYtMi4xNzVjMC4zMzEtMC43MDcsMC40OTUtMS41NDEsMC40OTUtMi41CgkJCWMwLTEuMDk2LTAuMjYtMi4wODgtMC43NzktMi45NzljLTAuNTY1LTAuODc5LTEuNTAxLTEuMzM2LTIuODA2LTEuMzY5Yy0xLjgwMiwwLjA1Ny0yLjk4NSwwLjY2Ny0zLjU1LDEuODMyCgkJCWMtMC4zMDEsMC41MzUtMC41MDMsMS4xNDEtMC42MDcsMS44MTRjLTAuMTM5LDAuNzA3LTAuMjA3LDEuNDMyLTAuMjA3LDIuMTc0aC0yLjkzN2MtMC4wOTEtMi4yMDgsMC40MDctNC4xMTQsMS40OTMtNS43MTkKCQkJYzEuMDYyLTEuNjQsMi44NTUtMi40ODEsNS4zNzgtMi41MjdjMi4xNiwwLjAyMywzLjg3NCwwLjYwOCw1LjE0MSwxLjc1OGMxLjI3OCwxLjE2LDEuOTI5LDIuNzY0LDEuOTUsNC44MTEKCQkJYzAsMS4xNDItMC4xMzcsMi4xMTEtMC40MSwyLjkxMWMtMC4zMDksMC44NDUtMC43MzEsMS41OTMtMS4yNjgsMi4yNDNjLTAuNDkyLDAuNjUtMS4wNjgsMS4zMTgtMS43MywyLjAwMgoJCQljLTAuNjUsMC42OTctMS4zMTMsMS40NzktMS45ODcsMi4zNDZjLTAuMjM5LDAuMzc3LTAuNDI5LDAuNzc3LTAuNTY1LDEuMTk5Yy0wLjE2LDAuOTU5LTAuMjE3LDEuOTUxLTAuMTcxLDIuOTc5CgkJCUMyNi41ODksMzIuMjE4LDIzLjU3OCwzMi4yMTgsMjMuNTc4LDMyLjIxOHogTTIzLjU3OCwzOC4yMnYtMy40ODRoMy4wNzZ2My40ODRIMjMuNTc4eiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-inspector: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaW5zcGVjdG9yLWljb24tY29sb3IganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0tNSAxNEg0di00aDExdjR6bTAtNUg0VjloMTF2NHptNSA1aC00VjloNHY5eiIvPgo8L3N2Zz4K);
  --jp-icon-json: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtanNvbi1pY29uLWNvbG9yIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0Y5QTgyNSI+CiAgICA8cGF0aCBkPSJNMjAuMiAxMS44Yy0xLjYgMC0xLjcuNS0xLjcgMSAwIC40LjEuOS4xIDEuMy4xLjUuMS45LjEgMS4zIDAgMS43LTEuNCAyLjMtMy41IDIuM2gtLjl2LTEuOWguNWMxLjEgMCAxLjQgMCAxLjQtLjggMC0uMyAwLS42LS4xLTEgMC0uNC0uMS0uOC0uMS0xLjIgMC0xLjMgMC0xLjggMS4zLTItMS4zLS4yLTEuMy0uNy0xLjMtMiAwLS40LjEtLjguMS0xLjIuMS0uNC4xLS43LjEtMSAwLS44LS40LS43LTEuNC0uOGgtLjVWNC4xaC45YzIuMiAwIDMuNS43IDMuNSAyLjMgMCAuNC0uMS45LS4xIDEuMy0uMS41LS4xLjktLjEgMS4zIDAgLjUuMiAxIDEuNyAxdjEuOHpNMS44IDEwLjFjMS42IDAgMS43LS41IDEuNy0xIDAtLjQtLjEtLjktLjEtMS4zLS4xLS41LS4xLS45LS4xLTEuMyAwLTEuNiAxLjQtMi4zIDMuNS0yLjNoLjl2MS45aC0uNWMtMSAwLTEuNCAwLTEuNC44IDAgLjMgMCAuNi4xIDEgMCAuMi4xLjYuMSAxIDAgMS4zIDAgMS44LTEuMyAyQzYgMTEuMiA2IDExLjcgNiAxM2MwIC40LS4xLjgtLjEgMS4yLS4xLjMtLjEuNy0uMSAxIDAgLjguMy44IDEuNC44aC41djEuOWgtLjljLTIuMSAwLTMuNS0uNi0zLjUtMi4zIDAtLjQuMS0uOS4xLTEuMy4xLS41LjEtLjkuMS0xLjMgMC0uNS0uMi0xLTEuNy0xdi0xLjl6Ii8+CiAgICA8Y2lyY2xlIGN4PSIxMSIgY3k9IjEzLjgiIHI9IjIuMSIvPgogICAgPGNpcmNsZSBjeD0iMTEiIGN5PSI4LjIiIHI9IjIuMSIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-julia: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDMyNSAzMDAiPgogIDxnIGNsYXNzPSJqcC1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjY2IzYzMzIj4KICAgIDxwYXRoIGQ9Ik0gMTUwLjg5ODQzOCAyMjUgQyAxNTAuODk4NDM4IDI2Ni40MjE4NzUgMTE3LjMyMDMxMiAzMDAgNzUuODk4NDM4IDMwMCBDIDM0LjQ3NjU2MiAzMDAgMC44OTg0MzggMjY2LjQyMTg3NSAwLjg5ODQzOCAyMjUgQyAwLjg5ODQzOCAxODMuNTc4MTI1IDM0LjQ3NjU2MiAxNTAgNzUuODk4NDM4IDE1MCBDIDExNy4zMjAzMTIgMTUwIDE1MC44OTg0MzggMTgzLjU3ODEyNSAxNTAuODk4NDM4IDIyNSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzM4OTgyNiI+CiAgICA8cGF0aCBkPSJNIDIzNy41IDc1IEMgMjM3LjUgMTE2LjQyMTg3NSAyMDMuOTIxODc1IDE1MCAxNjIuNSAxNTAgQyAxMjEuMDc4MTI1IDE1MCA4Ny41IDExNi40MjE4NzUgODcuNSA3NSBDIDg3LjUgMzMuNTc4MTI1IDEyMS4wNzgxMjUgMCAxNjIuNSAwIEMgMjAzLjkyMTg3NSAwIDIzNy41IDMzLjU3ODEyNSAyMzcuNSA3NSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzk1NThiMiI+CiAgICA8cGF0aCBkPSJNIDMyNC4xMDE1NjIgMjI1IEMgMzI0LjEwMTU2MiAyNjYuNDIxODc1IDI5MC41MjM0MzggMzAwIDI0OS4xMDE1NjIgMzAwIEMgMjA3LjY3OTY4OCAzMDAgMTc0LjEwMTU2MiAyNjYuNDIxODc1IDE3NC4xMDE1NjIgMjI1IEMgMTc0LjEwMTU2MiAxODMuNTc4MTI1IDIwNy42Nzk2ODggMTUwIDI0OS4xMDE1NjIgMTUwIEMgMjkwLjUyMzQzOCAxNTAgMzI0LjEwMTU2MiAxODMuNTc4MTI1IDMyNC4xMDE1NjIgMjI1Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-jupyter-favicon: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUyIiBoZWlnaHQ9IjE2NSIgdmlld0JveD0iMCAwIDE1MiAxNjUiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgPGcgY2xhc3M9ImpwLWp1cHl0ZXItaWNvbi1jb2xvciIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA3ODk0NywgMTEwLjU4MjkyNykiIGQ9Ik03NS45NDIyODQyLDI5LjU4MDQ1NjEgQzQzLjMwMjM5NDcsMjkuNTgwNDU2MSAxNC43OTY3ODMyLDE3LjY1MzQ2MzQgMCwwIEM1LjUxMDgzMjExLDE1Ljg0MDY4MjkgMTUuNzgxNTM4OSwyOS41NjY3NzMyIDI5LjM5MDQ5NDcsMzkuMjc4NDE3MSBDNDIuOTk5Nyw0OC45ODk4NTM3IDU5LjI3MzcsNTQuMjA2NzgwNSA3NS45NjA1Nzg5LDU0LjIwNjc4MDUgQzkyLjY0NzQ1NzksNTQuMjA2NzgwNSAxMDguOTIxNDU4LDQ4Ljk4OTg1MzcgMTIyLjUzMDY2MywzOS4yNzg0MTcxIEMxMzYuMTM5NDUzLDI5LjU2Njc3MzIgMTQ2LjQxMDI4NCwxNS44NDA2ODI5IDE1MS45MjExNTgsMCBDMTM3LjA4Nzg2OCwxNy42NTM0NjM0IDEwOC41ODI1ODksMjkuNTgwNDU2MSA3NS45NDIyODQyLDI5LjU4MDQ1NjEgTDc1Ljk0MjI4NDIsMjkuNTgwNDU2MSBaIiAvPgogICAgPHBhdGggdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMzczNjgsIDAuNzA0ODc4KSIgZD0iTTc1Ljk3ODQ1NzksMjQuNjI2NDA3MyBDMTA4LjYxODc2MywyNC42MjY0MDczIDEzNy4xMjQ0NTgsMzYuNTUzNDQxNSAxNTEuOTIxMTU4LDU0LjIwNjc4MDUgQzE0Ni40MTAyODQsMzguMzY2MjIyIDEzNi4xMzk0NTMsMjQuNjQwMTMxNyAxMjIuNTMwNjYzLDE0LjkyODQ4NzggQzEwOC45MjE0NTgsNS4yMTY4NDM5IDkyLjY0NzQ1NzksMCA3NS45NjA1Nzg5LDAgQzU5LjI3MzcsMCA0Mi45OTk3LDUuMjE2ODQzOSAyOS4zOTA0OTQ3LDE0LjkyODQ4NzggQzE1Ljc4MTUzODksMjQuNjQwMTMxNyA1LjUxMDgzMjExLDM4LjM2NjIyMiAwLDU0LjIwNjc4MDUgQzE0LjgzMzA4MTYsMzYuNTg5OTI5MyA0My4zMzg1Njg0LDI0LjYyNjQwNzMgNzUuOTc4NDU3OSwyNC42MjY0MDczIEw3NS45Nzg0NTc5LDI0LjYyNjQwNzMgWiIgLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-jupyter: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzkiIGhlaWdodD0iNTEiIHZpZXdCb3g9IjAgMCAzOSA1MSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMTYzOCAtMjI4MSkiPgogICAgIDxnIGNsYXNzPSJqcC1qdXB5dGVyLWljb24tY29sb3IiIGZpbGw9IiNGMzc3MjYiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5Ljc0IDIzMTEuOTgpIiBkPSJNIDE4LjI2NDYgNy4xMzQxMUMgMTAuNDE0NSA3LjEzNDExIDMuNTU4NzIgNC4yNTc2IDAgMEMgMS4zMjUzOSAzLjgyMDQgMy43OTU1NiA3LjEzMDgxIDcuMDY4NiA5LjQ3MzAzQyAxMC4zNDE3IDExLjgxNTIgMTQuMjU1NyAxMy4wNzM0IDE4LjI2OSAxMy4wNzM0QyAyMi4yODIzIDEzLjA3MzQgMjYuMTk2MyAxMS44MTUyIDI5LjQ2OTQgOS40NzMwM0MgMzIuNzQyNCA3LjEzMDgxIDM1LjIxMjYgMy44MjA0IDM2LjUzOCAwQyAzMi45NzA1IDQuMjU3NiAyNi4xMTQ4IDcuMTM0MTEgMTguMjY0NiA3LjEzNDExWiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5LjczIDIyODUuNDgpIiBkPSJNIDE4LjI3MzMgNS45MzkzMUMgMjYuMTIzNSA1LjkzOTMxIDMyLjk3OTMgOC44MTU4MyAzNi41MzggMTMuMDczNEMgMzUuMjEyNiA5LjI1MzAzIDMyLjc0MjQgNS45NDI2MiAyOS40Njk0IDMuNjAwNEMgMjYuMTk2MyAxLjI1ODE4IDIyLjI4MjMgMCAxOC4yNjkgMEMgMTQuMjU1NyAwIDEwLjM0MTcgMS4yNTgxOCA3LjA2ODYgMy42MDA0QyAzLjc5NTU2IDUuOTQyNjIgMS4zMjUzOSA5LjI1MzAzIDAgMTMuMDczNEMgMy41Njc0NSA4LjgyNDYzIDEwLjQyMzIgNS45MzkzMSAxOC4yNzMzIDUuOTM5MzFaIi8+CiAgICA8L2c+CiAgICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjY5LjMgMjI4MS4zMSkiIGQ9Ik0gNS44OTM1MyAyLjg0NEMgNS45MTg4OSAzLjQzMTY1IDUuNzcwODUgNC4wMTM2NyA1LjQ2ODE1IDQuNTE2NDVDIDUuMTY1NDUgNS4wMTkyMiA0LjcyMTY4IDUuNDIwMTUgNC4xOTI5OSA1LjY2ODUxQyAzLjY2NDMgNS45MTY4OCAzLjA3NDQ0IDYuMDAxNTEgMi40OTgwNSA1LjkxMTcxQyAxLjkyMTY2IDUuODIxOSAxLjM4NDYzIDUuNTYxNyAwLjk1NDg5OCA1LjE2NDAxQyAwLjUyNTE3IDQuNzY2MzMgMC4yMjIwNTYgNC4yNDkwMyAwLjA4MzkwMzcgMy42Nzc1N0MgLTAuMDU0MjQ4MyAzLjEwNjExIC0wLjAyMTIzIDIuNTA2MTcgMC4xNzg3ODEgMS45NTM2NEMgMC4zNzg3OTMgMS40MDExIDAuNzM2ODA5IDAuOTIwODE3IDEuMjA3NTQgMC41NzM1MzhDIDEuNjc4MjYgMC4yMjYyNTkgMi4yNDA1NSAwLjAyNzU5MTkgMi44MjMyNiAwLjAwMjY3MjI5QyAzLjYwMzg5IC0wLjAzMDcxMTUgNC4zNjU3MyAwLjI0OTc4OSA0Ljk0MTQyIDAuNzgyNTUxQyA1LjUxNzExIDEuMzE1MzEgNS44NTk1NiAyLjA1Njc2IDUuODkzNTMgMi44NDRaIi8+CiAgICAgIDxwYXRoIHRyYW5zZm9ybT0idHJhbnNsYXRlKDE2MzkuOCAyMzIzLjgxKSIgZD0iTSA3LjQyNzg5IDMuNTgzMzhDIDcuNDYwMDggNC4zMjQzIDcuMjczNTUgNS4wNTgxOSA2Ljg5MTkzIDUuNjkyMTNDIDYuNTEwMzEgNi4zMjYwNyA1Ljk1MDc1IDYuODMxNTYgNS4yODQxMSA3LjE0NDZDIDQuNjE3NDcgNy40NTc2MyAzLjg3MzcxIDcuNTY0MTQgMy4xNDcwMiA3LjQ1MDYzQyAyLjQyMDMyIDcuMzM3MTIgMS43NDMzNiA3LjAwODcgMS4yMDE4NCA2LjUwNjk1QyAwLjY2MDMyOCA2LjAwNTIgMC4yNzg2MSA1LjM1MjY4IDAuMTA1MDE3IDQuNjMyMDJDIC0wLjA2ODU3NTcgMy45MTEzNSAtMC4wMjYyMzYxIDMuMTU0OTQgMC4yMjY2NzUgMi40NTg1NkMgMC40Nzk1ODcgMS43NjIxNyAwLjkzMTY5NyAxLjE1NzEzIDEuNTI1NzYgMC43MjAwMzNDIDIuMTE5ODMgMC4yODI5MzUgMi44MjkxNCAwLjAzMzQzOTUgMy41NjM4OSAwLjAwMzEzMzQ0QyA0LjU0NjY3IC0wLjAzNzQwMzMgNS41MDUyOSAwLjMxNjcwNiA2LjIyOTYxIDAuOTg3ODM1QyA2Ljk1MzkzIDEuNjU4OTYgNy4zODQ4NCAyLjU5MjM1IDcuNDI3ODkgMy41ODMzOEwgNy40Mjc4OSAzLjU4MzM4WiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM4LjM2IDIyODYuMDYpIiBkPSJNIDIuMjc0NzEgNC4zOTYyOUMgMS44NDM2MyA0LjQxNTA4IDEuNDE2NzEgNC4zMDQ0NSAxLjA0Nzk5IDQuMDc4NDNDIDAuNjc5MjY4IDMuODUyNCAwLjM4NTMyOCAzLjUyMTE0IDAuMjAzMzcxIDMuMTI2NTZDIDAuMDIxNDEzNiAyLjczMTk4IC0wLjA0MDM3OTggMi4yOTE4MyAwLjAyNTgxMTYgMS44NjE4MUMgMC4wOTIwMDMxIDEuNDMxOCAwLjI4MzIwNCAxLjAzMTI2IDAuNTc1MjEzIDAuNzEwODgzQyAwLjg2NzIyMiAwLjM5MDUxIDEuMjQ2OTEgMC4xNjQ3MDggMS42NjYyMiAwLjA2MjA1OTJDIDIuMDg1NTMgLTAuMDQwNTg5NyAyLjUyNTYxIC0wLjAxNTQ3MTQgMi45MzA3NiAwLjEzNDIzNUMgMy4zMzU5MSAwLjI4Mzk0MSAzLjY4NzkyIDAuNTUxNTA1IDMuOTQyMjIgMC45MDMwNkMgNC4xOTY1MiAxLjI1NDYyIDQuMzQxNjkgMS42NzQzNiA0LjM1OTM1IDIuMTA5MTZDIDQuMzgyOTkgMi42OTEwNyA0LjE3Njc4IDMuMjU4NjkgMy43ODU5NyAzLjY4NzQ2QyAzLjM5NTE2IDQuMTE2MjQgMi44NTE2NiA0LjM3MTE2IDIuMjc0NzEgNC4zOTYyOUwgMi4yNzQ3MSA0LjM5NjI5WiIvPgogICAgPC9nPgogIDwvZz4+Cjwvc3ZnPgo=);
  --jp-icon-jupyterlab-wordmark: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMDAiIHZpZXdCb3g9IjAgMCAxODYwLjggNDc1Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0RTRFNEUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDQ4MC4xMzY0MDEsIDY0LjI3MTQ5MykiPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMDAwMDAsIDU4Ljg3NTU2NikiPgogICAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA4NzYwMywgMC4xNDAyOTQpIj4KICAgICAgICA8cGF0aCBkPSJNLTQyNi45LDE2OS44YzAsNDguNy0zLjcsNjQuNy0xMy42LDc2LjRjLTEwLjgsMTAtMjUsMTUuNS0zOS43LDE1LjVsMy43LDI5IGMyMi44LDAuMyw0NC44LTcuOSw2MS45LTIzLjFjMTcuOC0xOC41LDI0LTQ0LjEsMjQtODMuM1YwSC00Mjd2MTcwLjFMLTQyNi45LDE2OS44TC00MjYuOSwxNjkuOHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTU1LjA0NTI5NiwgNTYuODM3MTA0KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuNTYyNDUzLCAxLjc5OTg0MikiPgogICAgICAgIDxwYXRoIGQ9Ik0tMzEyLDE0OGMwLDIxLDAsMzkuNSwxLjcsNTUuNGgtMzEuOGwtMi4xLTMzLjNoLTAuOGMtNi43LDExLjYtMTYuNCwyMS4zLTI4LDI3LjkgYy0xMS42LDYuNi0yNC44LDEwLTM4LjIsOS44Yy0zMS40LDAtNjktMTcuNy02OS04OVYwaDM2LjR2MTEyLjdjMCwzOC43LDExLjYsNjQuNyw0NC42LDY0LjdjMTAuMy0wLjIsMjAuNC0zLjUsMjguOS05LjQgYzguNS01LjksMTUuMS0xNC4zLDE4LjktMjMuOWMyLjItNi4xLDMuMy0xMi41LDMuMy0xOC45VjAuMmgzNi40VjE0OEgtMzEyTC0zMTIsMTQ4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzOTAuMDEzMzIyLCA1My40Nzk2MzgpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS43MDY0NTgsIDAuMjMxNDI1KSI+CiAgICAgICAgPHBhdGggZD0iTS00NzguNiw3MS40YzAtMjYtMC44LTQ3LTEuNy02Ni43aDMyLjdsMS43LDM0LjhoMC44YzcuMS0xMi41LDE3LjUtMjIuOCwzMC4xLTI5LjcgYzEyLjUtNywyNi43LTEwLjMsNDEtOS44YzQ4LjMsMCw4NC43LDQxLjcsODQuNywxMDMuM2MwLDczLjEtNDMuNywxMDkuMi05MSwxMDkuMmMtMTIuMSwwLjUtMjQuMi0yLjItMzUtNy44IGMtMTAuOC01LjYtMTkuOS0xMy45LTI2LjYtMjQuMmgtMC44VjI5MWgtMzZ2LTIyMEwtNDc4LjYsNzEuNEwtNDc4LjYsNzEuNHogTS00NDIuNiwxMjUuNmMwLjEsNS4xLDAuNiwxMC4xLDEuNywxNS4xIGMzLDEyLjMsOS45LDIzLjMsMTkuOCwzMS4xYzkuOSw3LjgsMjIuMSwxMi4xLDM0LjcsMTIuMWMzOC41LDAsNjAuNy0zMS45LDYwLjctNzguNWMwLTQwLjctMjEuMS03NS42LTU5LjUtNzUuNiBjLTEyLjksMC40LTI1LjMsNS4xLTM1LjMsMTMuNGMtOS45LDguMy0xNi45LDE5LjctMTkuNiwzMi40Yy0xLjUsNC45LTIuMywxMC0yLjUsMTUuMVYxMjUuNkwtNDQyLjYsMTI1LjZMLTQ0Mi42LDEyNS42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSg2MDYuNzQwNzI2LCA1Ni44MzcxMDQpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC43NTEyMjYsIDEuOTg5Mjk5KSI+CiAgICAgICAgPHBhdGggZD0iTS00NDAuOCwwbDQzLjcsMTIwLjFjNC41LDEzLjQsOS41LDI5LjQsMTIuOCw0MS43aDAuOGMzLjctMTIuMiw3LjktMjcuNywxMi44LTQyLjQgbDM5LjctMTE5LjJoMzguNUwtMzQ2LjksMTQ1Yy0yNiw2OS43LTQzLjcsMTA1LjQtNjguNiwxMjcuMmMtMTIuNSwxMS43LTI3LjksMjAtNDQuNiwyMy45bC05LjEtMzEuMSBjMTEuNy0zLjksMjIuNS0xMC4xLDMxLjgtMTguMWMxMy4yLTExLjEsMjMuNy0yNS4yLDMwLjYtNDEuMmMxLjUtMi44LDIuNS01LjcsMi45LTguOGMtMC4zLTMuMy0xLjItNi42LTIuNS05LjdMLTQ4MC4yLDAuMSBoMzkuN0wtNDQwLjgsMEwtNDQwLjgsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoODIyLjc0ODEwNCwgMC4wMDAwMDApIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS40NjQwNTAsIDAuMzc4OTE0KSI+CiAgICAgICAgPHBhdGggZD0iTS00MTMuNywwdjU4LjNoNTJ2MjguMmgtNTJWMTk2YzAsMjUsNywzOS41LDI3LjMsMzkuNWM3LjEsMC4xLDE0LjItMC43LDIxLjEtMi41IGwxLjcsMjcuN2MtMTAuMywzLjctMjEuMyw1LjQtMzIuMiw1Yy03LjMsMC40LTE0LjYtMC43LTIxLjMtMy40Yy02LjgtMi43LTEyLjktNi44LTE3LjktMTIuMWMtMTAuMy0xMC45LTE0LjEtMjktMTQuMS01Mi45IFY4Ni41aC0zMVY1OC4zaDMxVjkuNkwtNDEzLjcsMEwtNDEzLjcsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOTc0LjQzMzI4NiwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuOTkwMDM0LCAwLjYxMDMzOSkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDQ1LjgsMTEzYzAuOCw1MCwzMi4yLDcwLjYsNjguNiw3MC42YzE5LDAuNiwzNy45LTMsNTUuMy0xMC41bDYuMiwyNi40IGMtMjAuOSw4LjktNDMuNSwxMy4xLTY2LjIsMTIuNmMtNjEuNSwwLTk4LjMtNDEuMi05OC4zLTEwMi41Qy00ODAuMiw0OC4yLTQ0NC43LDAtMzg2LjUsMGM2NS4yLDAsODIuNyw1OC4zLDgyLjcsOTUuNyBjLTAuMSw1LjgtMC41LDExLjUtMS4yLDE3LjJoLTE0MC42SC00NDUuOEwtNDQ1LjgsMTEzeiBNLTMzOS4yLDg2LjZjMC40LTIzLjUtOS41LTYwLjEtNTAuNC02MC4xIGMtMzYuOCwwLTUyLjgsMzQuNC01NS43LDYwLjFILTMzOS4yTC0zMzkuMiw4Ni42TC0zMzkuMiw4Ni42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMjAxLjk2MTA1OCwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuMTc5NjQwLCAwLjcwNTA2OCkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDc4LjYsNjhjMC0yMy45LTAuNC00NC41LTEuNy02My40aDMxLjhsMS4yLDM5LjloMS43YzkuMS0yNy4zLDMxLTQ0LjUsNTUuMy00NC41IGMzLjUtMC4xLDcsMC40LDEwLjMsMS4ydjM0LjhjLTQuMS0wLjktOC4yLTEuMy0xMi40LTEuMmMtMjUuNiwwLTQzLjcsMTkuNy00OC43LDQ3LjRjLTEsNS43LTEuNiwxMS41LTEuNywxNy4ydjEwOC4zaC0zNlY2OCBMLTQ3OC42LDY4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCBkPSJNMTM1Mi4zLDMyNi4yaDM3VjI4aC0zN1YzMjYuMnogTTE2MDQuOCwzMjYuMmMtMi41LTEzLjktMy40LTMxLjEtMy40LTQ4Ljd2LTc2IGMwLTQwLjctMTUuMS04My4xLTc3LjMtODMuMWMtMjUuNiwwLTUwLDcuMS02Ni44LDE4LjFsOC40LDI0LjRjMTQuMy05LjIsMzQtMTUuMSw1My0xNS4xYzQxLjYsMCw0Ni4yLDMwLjIsNDYuMiw0N3Y0LjIgYy03OC42LTAuNC0xMjIuMywyNi41LTEyMi4zLDc1LjZjMCwyOS40LDIxLDU4LjQsNjIuMiw1OC40YzI5LDAsNTAuOS0xNC4zLDYyLjItMzAuMmgxLjNsMi45LDI1LjZIMTYwNC44eiBNMTU2NS43LDI1Ny43IGMwLDMuOC0wLjgsOC0yLjEsMTEuOGMtNS45LDE3LjItMjIuNywzNC00OS4yLDM0Yy0xOC45LDAtMzQuOS0xMS4zLTM0LjktMzUuM2MwLTM5LjUsNDUuOC00Ni42LDg2LjItNDUuOFYyNTcuN3ogTTE2OTguNSwzMjYuMiBsMS43LTMzLjZoMS4zYzE1LjEsMjYuOSwzOC43LDM4LjIsNjguMSwzOC4yYzQ1LjQsMCw5MS4yLTM2LjEsOTEuMi0xMDguOGMwLjQtNjEuNy0zNS4zLTEwMy43LTg1LjctMTAzLjcgYy0zMi44LDAtNTYuMywxNC43LTY5LjMsMzcuNGgtMC44VjI4aC0zNi42djI0NS43YzAsMTguMS0wLjgsMzguNi0xLjcsNTIuNUgxNjk4LjV6IE0xNzA0LjgsMjA4LjJjMC01LjksMS4zLTEwLjksMi4xLTE1LjEgYzcuNi0yOC4xLDMxLjEtNDUuNCw1Ni4zLTQ1LjRjMzkuNSwwLDYwLjUsMzQuOSw2MC41LDc1LjZjMCw0Ni42LTIzLjEsNzguMS02MS44LDc4LjFjLTI2LjksMC00OC4zLTE3LjYtNTUuNS00My4zIGMtMC44LTQuMi0xLjctOC44LTEuNy0xMy40VjIwOC4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzYxNjE2MSIgZD0iTTE1IDlIOXY2aDZWOXptLTIgNGgtMnYtMmgydjJ6bTgtMlY5aC0yVjdjMC0xLjEtLjktMi0yLTJoLTJWM2gtMnYyaC0yVjNIOXYySDdjLTEuMSAwLTIgLjktMiAydjJIM3YyaDJ2MkgzdjJoMnYyYzAgMS4xLjkgMiAyIDJoMnYyaDJ2LTJoMnYyaDJ2LTJoMmMxLjEgMCAyLS45IDItMnYtMmgydi0yaC0ydi0yaDJ6bS00IDZIN1Y3aDEwdjEweiIvPgo8L3N2Zz4K);
  --jp-icon-keyboard: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMTdjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY3YzAtMS4xLS45LTItMi0yem0tOSAzaDJ2MmgtMlY4em0wIDNoMnYyaC0ydi0yek04IDhoMnYySDhWOHptMCAzaDJ2Mkg4di0yem0tMSAySDV2LTJoMnYyem0wLTNINVY4aDJ2MnptOSA3SDh2LTJoOHYyem0wLTRoLTJ2LTJoMnYyem0wLTNoLTJWOGgydjJ6bTMgM2gtMnYtMmgydjJ6bTAtM2gtMlY4aDJ2MnoiLz4KPC9zdmc+Cg==);
  --jp-icon-launch: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMzIgMzIiIHdpZHRoPSIzMiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0yNiwyOEg2YTIuMDAyNywyLjAwMjcsMCwwLDEtMi0yVjZBMi4wMDI3LDIuMDAyNywwLDAsMSw2LDRIMTZWNkg2VjI2SDI2VjE2aDJWMjZBMi4wMDI3LDIuMDAyNywwLDAsMSwyNiwyOFoiLz4KICAgIDxwb2x5Z29uIHBvaW50cz0iMjAgMiAyMCA0IDI2LjU4NiA0IDE4IDEyLjU4NiAxOS40MTQgMTQgMjggNS40MTQgMjggMTIgMzAgMTIgMzAgMiAyMCAyIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-launcher: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkgMTlINVY1aDdWM0g1YTIgMiAwIDAwLTIgMnYxNGEyIDIgMCAwMDIgMmgxNGMxLjEgMCAyLS45IDItMnYtN2gtMnY3ek0xNCAzdjJoMy41OWwtOS44MyA5LjgzIDEuNDEgMS40MUwxOSA2LjQxVjEwaDJWM2gtN3oiLz4KPC9zdmc+Cg==);
  --jp-icon-line-form: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGZpbGw9IndoaXRlIiBkPSJNNS44OCA0LjEyTDEzLjc2IDEybC03Ljg4IDcuODhMOCAyMmwxMC0xMEw4IDJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-link: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMuOSAxMmMwLTEuNzEgMS4zOS0zLjEgMy4xLTMuMWg0VjdIN2MtMi43NiAwLTUgMi4yNC01IDVzMi4yNCA1IDUgNWg0di0xLjlIN2MtMS43MSAwLTMuMS0xLjM5LTMuMS0zLjF6TTggMTNoOHYtMkg4djJ6bTktNmgtNHYxLjloNGMxLjcxIDAgMy4xIDEuMzkgMy4xIDMuMXMtMS4zOSAzLjEtMy4xIDMuMWgtNFYxN2g0YzIuNzYgMCA1LTIuMjQgNS01cy0yLjI0LTUtNS01eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xOSA1djE0SDVWNWgxNG0xLjEtMkgzLjljLS41IDAtLjkuNC0uOS45djE2LjJjMCAuNC40LjkuOS45aDE2LjJjLjQgMCAuOS0uNS45LS45VjMuOWMwLS41LS41LS45LS45LS45ek0xMSA3aDZ2MmgtNlY3em0wIDRoNnYyaC02di0yem0wIDRoNnYyaC02ek03IDdoMnYySDd6bTAgNGgydjJIN3ptMCA0aDJ2Mkg3eiIvPgo8L3N2Zz4K);
  --jp-icon-markdown: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjN0IxRkEyIiBkPSJNNSAxNC45aDEybC02LjEgNnptOS40LTYuOGMwLTEuMy0uMS0yLjktLjEtNC41LS40IDEuNC0uOSAyLjktMS4zIDQuM2wtMS4zIDQuM2gtMkw4LjUgNy45Yy0uNC0xLjMtLjctMi45LTEtNC4zLS4xIDEuNi0uMSAzLjItLjIgNC42TDcgMTIuNEg0LjhsLjctMTFoMy4zTDEwIDVjLjQgMS4yLjcgMi43IDEgMy45LjMtMS4yLjctMi42IDEtMy45bDEuMi0zLjdoMy4zbC42IDExaC0yLjRsLS4zLTQuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-move-down: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBkPSJNMTIuNDcxIDcuNTI4OTlDMTIuNzYzMiA3LjIzNjg0IDEyLjc2MzIgNi43NjMxNiAxMi40NzEgNi40NzEwMVY2LjQ3MTAxQzEyLjE3OSA2LjE3OTA1IDExLjcwNTcgNi4xNzg4NCAxMS40MTM1IDYuNDcwNTRMNy43NSAxMC4xMjc1VjEuNzVDNy43NSAxLjMzNTc5IDcuNDE0MjEgMSA3IDFWMUM2LjU4NTc5IDEgNi4yNSAxLjMzNTc5IDYuMjUgMS43NVYxMC4xMjc1TDIuNTk3MjYgNi40NjgyMkMyLjMwMzM4IDYuMTczODEgMS44MjY0MSA2LjE3MzU5IDEuNTMyMjYgNi40Njc3NFY2LjQ2Nzc0QzEuMjM4MyA2Ljc2MTcgMS4yMzgzIDcuMjM4MyAxLjUzMjI2IDcuNTMyMjZMNi4yOTI4OSAxMi4yOTI5QzYuNjgzNDIgMTIuNjgzNCA3LjMxNjU4IDEyLjY4MzQgNy43MDcxMSAxMi4yOTI5TDEyLjQ3MSA3LjUyODk5WiIgZmlsbD0iIzYxNjE2MSIvPgo8L3N2Zz4K);
  --jp-icon-move-up: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBkPSJNMS41Mjg5OSA2LjQ3MTAxQzEuMjM2ODQgNi43NjMxNiAxLjIzNjg0IDcuMjM2ODQgMS41Mjg5OSA3LjUyODk5VjcuNTI4OTlDMS44MjA5NSA3LjgyMDk1IDIuMjk0MjYgNy44MjExNiAyLjU4NjQ5IDcuNTI5NDZMNi4yNSAzLjg3MjVWMTIuMjVDNi4yNSAxMi42NjQyIDYuNTg1NzkgMTMgNyAxM1YxM0M3LjQxNDIxIDEzIDcuNzUgMTIuNjY0MiA3Ljc1IDEyLjI1VjMuODcyNUwxMS40MDI3IDcuNTMxNzhDMTEuNjk2NiA3LjgyNjE5IDEyLjE3MzYgNy44MjY0MSAxMi40Njc3IDcuNTMyMjZWNy41MzIyNkMxMi43NjE3IDcuMjM4MyAxMi43NjE3IDYuNzYxNyAxMi40Njc3IDYuNDY3NzRMNy43MDcxMSAxLjcwNzExQzcuMzE2NTggMS4zMTY1OCA2LjY4MzQyIDEuMzE2NTggNi4yOTI4OSAxLjcwNzExTDEuNTI4OTkgNi40NzEwMVoiIGZpbGw9IiM2MTYxNjEiLz4KPC9zdmc+Cg==);
  --jp-icon-new-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDZoLThsLTItMkg0Yy0xLjExIDAtMS45OS44OS0xLjk5IDJMMiAxOGMwIDEuMTEuODkgMiAyIDJoMTZjMS4xMSAwIDItLjg5IDItMlY4YzAtMS4xMS0uODktMi0yLTJ6bS0xIDhoLTN2M2gtMnYtM2gtM3YtMmgzVjloMnYzaDN2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-not-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI1IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMTkgMTcuMTg0NCAyLjk2OTY4IDE0LjMwMzIgMS44NjA5NCAxMS40NDA5WiIvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24yIiBzdHJva2U9IiMzMzMzMzMiIHN0cm9rZS13aWR0aD0iMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOS4zMTU5MiA5LjMyMDMxKSIgZD0iTTcuMzY4NDIgMEwwIDcuMzY0NzkiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDkuMzE1OTIgMTYuNjgzNikgc2NhbGUoMSAtMSkiIGQ9Ik03LjM2ODQyIDBMMCA3LjM2NDc5Ii8+Cjwvc3ZnPgo=);
  --jp-icon-notebook: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtbm90ZWJvb2staWNvbi1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNFRjZDMDAiPgogICAgPHBhdGggZD0iTTE4LjcgMy4zdjE1LjRIMy4zVjMuM2gxNS40bTEuNS0xLjVIMS44djE4LjNoMTguM2wuMS0xOC4zeiIvPgogICAgPHBhdGggZD0iTTE2LjUgMTYuNWwtNS40LTQuMy01LjYgNC4zdi0xMWgxMXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-numbering: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTQgMTlINlYxOS41SDVWMjAuNUg2VjIxSDRWMjJIN1YxOEg0VjE5Wk01IDEwSDZWNkg0VjdINVYxMFpNNCAxM0g1LjhMNCAxNS4xVjE2SDdWMTVINS4yTDcgMTIuOVYxMkg0VjEzWk05IDdWOUgyM1Y3SDlaTTkgMjFIMjNWMTlIOVYyMVpNOSAxNUgyM1YxM0g5VjE1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-offline-bolt: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDIuMDJjLTUuNTEgMC05Ljk4IDQuNDctOS45OCA5Ljk4czQuNDcgOS45OCA5Ljk4IDkuOTggOS45OC00LjQ3IDkuOTgtOS45OFMxNy41MSAyLjAyIDEyIDIuMDJ6TTExLjQ4IDIwdi02LjI2SDhMMTMgNHY2LjI2aDMuMzVMMTEuNDggMjB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-palette: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE4IDEzVjIwSDRWNkg5LjAyQzkuMDcgNS4yOSA5LjI0IDQuNjIgOS41IDRINEMyLjkgNCAyIDQuOSAyIDZWMjBDMiAyMS4xIDIuOSAyMiA0IDIySDE4QzE5LjEgMjIgMjAgMjEuMSAyMCAyMFYxNUwxOCAxM1pNMTkuMyA4Ljg5QzE5Ljc0IDguMTkgMjAgNy4zOCAyMCA2LjVDMjAgNC4wMSAxNy45OSAyIDE1LjUgMkMxMy4wMSAyIDExIDQuMDEgMTEgNi41QzExIDguOTkgMTMuMDEgMTEgMTUuNDkgMTFDMTYuMzcgMTEgMTcuMTkgMTAuNzQgMTcuODggMTAuM0wyMSAxMy40MkwyMi40MiAxMkwxOS4zIDguODlaTTE1LjUgOUMxNC4xMiA5IDEzIDcuODggMTMgNi41QzEzIDUuMTIgMTQuMTIgNCAxNS41IDRDMTYuODggNCAxOCA1LjEyIDE4IDYuNUMxOCA3Ljg4IDE2Ljg4IDkgMTUuNSA5WiIvPgogICAgPHBhdGggZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik00IDZIOS4wMTg5NEM5LjAwNjM5IDYuMTY1MDIgOSA2LjMzMTc2IDkgNi41QzkgOC44MTU3NyAxMC4yMTEgMTAuODQ4NyAxMi4wMzQzIDEySDlWMTRIMTZWMTIuOTgxMUMxNi41NzAzIDEyLjkzNzcgMTcuMTIgMTIuODIwNyAxNy42Mzk2IDEyLjYzOTZMMTggMTNWMjBINFY2Wk04IDhINlYxMEg4VjhaTTYgMTJIOFYxNEg2VjEyWk04IDE2SDZWMThIOFYxNlpNOSAxNkgxNlYxOEg5VjE2WiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-paste: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE5IDJoLTQuMThDMTQuNC44NCAxMy4zIDAgMTIgMGMtMS4zIDAtMi40Ljg0LTIuODIgMkg1Yy0xLjEgMC0yIC45LTIgMnYxNmMwIDEuMS45IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjRjMC0xLjEtLjktMi0yLTJ6bS03IDBjLjU1IDAgMSAuNDUgMSAxcy0uNDUgMS0xIDEtMS0uNDUtMS0xIC40NS0xIDEtMXptNyAxOEg1VjRoMnYzaDEwVjRoMnYxNnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-pdf: url(data:image/svg+xml;base64,PHN2ZwogICB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyMiAyMiIgd2lkdGg9IjE2Ij4KICAgIDxwYXRoIHRyYW5zZm9ybT0icm90YXRlKDQ1KSIgY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0ZGMkEyQSIKICAgICAgIGQ9Im0gMjIuMzQ0MzY5LC0zLjAxNjM2NDIgaCA1LjYzODYwNCB2IDEuNTc5MjQzMyBoIC0zLjU0OTIyNyB2IDEuNTA4NjkyOTkgaCAzLjMzNzU3NiBWIDEuNjUwODE1NCBoIC0zLjMzNzU3NiB2IDMuNDM1MjYxMyBoIC0yLjA4OTM3NyB6IG0gLTcuMTM2NDQ0LDEuNTc5MjQzMyB2IDQuOTQzOTU0MyBoIDAuNzQ4OTIgcSAxLjI4MDc2MSwwIDEuOTUzNzAzLC0wLjYzNDk1MzUgMC42NzgzNjksLTAuNjM0OTUzNSAwLjY3ODM2OSwtMS44NDUxNjQxIDAsLTEuMjA0NzgzNTUgLTAuNjcyOTQyLC0xLjgzNDMxMDExIC0wLjY3Mjk0MiwtMC42Mjk1MjY1OSAtMS45NTkxMywtMC42Mjk1MjY1OSB6IG0gLTIuMDg5Mzc3LC0xLjU3OTI0MzMgaCAyLjIwMzM0MyBxIDEuODQ1MTY0LDAgMi43NDYwMzksMC4yNjU5MjA3IDAuOTA2MzAxLDAuMjYwNDkzNyAxLjU1MjEwOCwwLjg5MDAyMDMgMC41Njk4MywwLjU0ODEyMjMgMC44NDY2MDUsMS4yNjQ0ODAwNiAwLjI3Njc3NCwwLjcxNjM1NzgxIDAuMjc2Nzc0LDEuNjIyNjU4OTQgMCwwLjkxNzE1NTEgLTAuMjc2Nzc0LDEuNjM4OTM5OSAtMC4yNzY3NzUsMC43MTYzNTc4IC0wLjg0NjYwNSwxLjI2NDQ4IC0wLjY1MTIzNCwwLjYyOTUyNjYgLTEuNTYyOTYyLDAuODk1NDQ3MyAtMC45MTE3MjgsMC4yNjA0OTM3IC0yLjczNTE4NSwwLjI2MDQ5MzcgaCAtMi4yMDMzNDMgeiBtIC04LjE0NTg1NjUsMCBoIDMuNDY3ODIzIHEgMS41NDY2ODE2LDAgMi4zNzE1Nzg1LDAuNjg5MjIzIDAuODMwMzI0LDAuNjgzNzk2MSAwLjgzMDMyNCwxLjk1MzcwMzE0IDAsMS4yNzUzMzM5NyAtMC44MzAzMjQsMS45NjQ1NTcwNiBRIDkuOTg3MTk2MSwyLjI3NDkxNSA4LjQ0MDUxNDUsMi4yNzQ5MTUgSCA3LjA2MjA2ODQgViA1LjA4NjA3NjcgSCA0Ljk3MjY5MTUgWiBtIDIuMDg5Mzc2OSwxLjUxNDExOTkgdiAyLjI2MzAzOTQzIGggMS4xNTU5NDEgcSAwLjYwNzgxODgsMCAwLjkzODg2MjksLTAuMjkzMDU1NDcgMC4zMzEwNDQxLC0wLjI5ODQ4MjQxIDAuMzMxMDQ0MSwtMC44NDExNzc3MiAwLC0wLjU0MjY5NTMxIC0wLjMzMTA0NDEsLTAuODM1NzUwNzQgLTAuMzMxMDQ0MSwtMC4yOTMwNTU1IC0wLjkzODg2MjksLTAuMjkzMDU1NSB6IgovPgo8L3N2Zz4K);
  --jp-icon-python: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iLTEwIC0xMCAxMzEuMTYxMzYxNjk0MzM1OTQgMTMyLjM4ODk5OTkzODk2NDg0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMzA2OTk4IiBkPSJNIDU0LjkxODc4NSw5LjE5Mjc0MjFlLTQgQyA1MC4zMzUxMzIsMC4wMjIyMTcyNyA0NS45NTc4NDYsMC40MTMxMzY5NyA0Mi4xMDYyODUsMS4wOTQ2NjkzIDMwLjc2MDA2OSwzLjA5OTE3MzEgMjguNzAwMDM2LDcuMjk0NzcxNCAyOC43MDAwMzUsMTUuMDMyMTY5IHYgMTAuMjE4NzUgaCAyNi44MTI1IHYgMy40MDYyNSBoIC0yNi44MTI1IC0xMC4wNjI1IGMgLTcuNzkyNDU5LDAgLTE0LjYxNTc1ODgsNC42ODM3MTcgLTE2Ljc0OTk5OTgsMTMuNTkzNzUgLTIuNDYxODE5OTgsMTAuMjEyOTY2IC0yLjU3MTAxNTA4LDE2LjU4NjAyMyAwLDI3LjI1IDEuOTA1OTI4Myw3LjkzNzg1MiA2LjQ1NzU0MzIsMTMuNTkzNzQ4IDE0LjI0OTk5OTgsMTMuNTkzNzUgaCA5LjIxODc1IHYgLTEyLjI1IGMgMCwtOC44NDk5MDIgNy42NTcxNDQsLTE2LjY1NjI0OCAxNi43NSwtMTYuNjU2MjUgaCAyNi43ODEyNSBjIDcuNDU0OTUxLDAgMTMuNDA2MjUzLC02LjEzODE2NCAxMy40MDYyNSwtMTMuNjI1IHYgLTI1LjUzMTI1IGMgMCwtNy4yNjYzMzg2IC02LjEyOTk4LC0xMi43MjQ3NzcxIC0xMy40MDYyNSwtMTMuOTM3NDk5NyBDIDY0LjI4MTU0OCwwLjMyNzk0Mzk3IDU5LjUwMjQzOCwtMC4wMjAzNzkwMyA1NC45MTg3ODUsOS4xOTI3NDIxZS00IFogbSAtMTQuNSw4LjIxODc1MDEyNTc5IGMgMi43Njk1NDcsMCA1LjAzMTI1LDIuMjk4NjQ1NiA1LjAzMTI1LDUuMTI0OTk5NiAtMmUtNiwyLjgxNjMzNiAtMi4yNjE3MDMsNS4wOTM3NSAtNS4wMzEyNSw1LjA5Mzc1IC0yLjc3OTQ3NiwtMWUtNiAtNS4wMzEyNSwtMi4yNzc0MTUgLTUuMDMxMjUsLTUuMDkzNzUgLTEwZS03LC0yLjgyNjM1MyAyLjI1MTc3NCwtNS4xMjQ5OTk2IDUuMDMxMjUsLTUuMTI0OTk5NiB6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2ZmZDQzYiIgZD0ibSA4NS42Mzc1MzUsMjguNjU3MTY5IHYgMTEuOTA2MjUgYyAwLDkuMjMwNzU1IC03LjgyNTg5NSwxNi45OTk5OTkgLTE2Ljc1LDE3IGggLTI2Ljc4MTI1IGMgLTcuMzM1ODMzLDAgLTEzLjQwNjI0OSw2LjI3ODQ4MyAtMTMuNDA2MjUsMTMuNjI1IHYgMjUuNTMxMjQ3IGMgMCw3LjI2NjM0NCA2LjMxODU4OCwxMS41NDAzMjQgMTMuNDA2MjUsMTMuNjI1MDA0IDguNDg3MzMxLDIuNDk1NjEgMTYuNjI2MjM3LDIuOTQ2NjMgMjYuNzgxMjUsMCA2Ljc1MDE1NSwtMS45NTQzOSAxMy40MDYyNTMsLTUuODg3NjEgMTMuNDA2MjUsLTEzLjYyNTAwNCBWIDg2LjUwMDkxOSBoIC0yNi43ODEyNSB2IC0zLjQwNjI1IGggMjYuNzgxMjUgMTMuNDA2MjU0IGMgNy43OTI0NjEsMCAxMC42OTYyNTEsLTUuNDM1NDA4IDEzLjQwNjI0MSwtMTMuNTkzNzUgMi43OTkzMywtOC4zOTg4ODYgMi42ODAyMiwtMTYuNDc1Nzc2IDAsLTI3LjI1IC0xLjkyNTc4LC03Ljc1NzQ0MSAtNS42MDM4NywtMTMuNTkzNzUgLTEzLjQwNjI0MSwtMTMuNTkzNzUgeiBtIC0xNS4wNjI1LDY0LjY1NjI1IGMgMi43Nzk0NzgsM2UtNiA1LjAzMTI1LDIuMjc3NDE3IDUuMDMxMjUsNS4wOTM3NDcgLTJlLTYsMi44MjYzNTQgLTIuMjUxNzc1LDUuMTI1MDA0IC01LjAzMTI1LDUuMTI1MDA0IC0yLjc2OTU1LDAgLTUuMDMxMjUsLTIuMjk4NjUgLTUuMDMxMjUsLTUuMTI1MDA0IDJlLTYsLTIuODE2MzMgMi4yNjE2OTcsLTUuMDkzNzQ3IDUuMDMxMjUsLTUuMDkzNzQ3IHoiLz4KPC9zdmc+Cg==);
  --jp-icon-r-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjE5NkYzIiBkPSJNNC40IDIuNWMxLjItLjEgMi45LS4zIDQuOS0uMyAyLjUgMCA0LjEuNCA1LjIgMS4zIDEgLjcgMS41IDEuOSAxLjUgMy41IDAgMi0xLjQgMy41LTIuOSA0LjEgMS4yLjQgMS43IDEuNiAyLjIgMyAuNiAxLjkgMSAzLjkgMS4zIDQuNmgtMy44Yy0uMy0uNC0uOC0xLjctMS4yLTMuN3MtMS4yLTIuNi0yLjYtMi42aC0uOXY2LjRINC40VjIuNXptMy43IDYuOWgxLjRjMS45IDAgMi45LS45IDIuOS0yLjNzLTEtMi4zLTIuOC0yLjNjLS43IDAtMS4zIDAtMS42LjJ2NC41aC4xdi0uMXoiLz4KPC9zdmc+Cg==);
  --jp-icon-react: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMTUwIDE1MCA1NDEuOSAyOTUuMyI+CiAgPGcgY2xhc3M9ImpwLWljb24tYnJhbmQyIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxREFGQiI+CiAgICA8cGF0aCBkPSJNNjY2LjMgMjk2LjVjMC0zMi41LTQwLjctNjMuMy0xMDMuMS04Mi40IDE0LjQtNjMuNiA4LTExNC4yLTIwLjItMTMwLjQtNi41LTMuOC0xNC4xLTUuNi0yMi40LTUuNnYyMi4zYzQuNiAwIDguMy45IDExLjQgMi42IDEzLjYgNy44IDE5LjUgMzcuNSAxNC45IDc1LjctMS4xIDkuNC0yLjkgMTkuMy01LjEgMjkuNC0xOS42LTQuOC00MS04LjUtNjMuNS0xMC45LTEzLjUtMTguNS0yNy41LTM1LjMtNDEuNi01MCAzMi42LTMwLjMgNjMuMi00Ni45IDg0LTQ2LjlWNzhjLTI3LjUgMC02My41IDE5LjYtOTkuOSA1My42LTM2LjQtMzMuOC03Mi40LTUzLjItOTkuOS01My4ydjIyLjNjMjAuNyAwIDUxLjQgMTYuNSA4NCA0Ni42LTE0IDE0LjctMjggMzEuNC00MS4zIDQ5LjktMjIuNiAyLjQtNDQgNi4xLTYzLjYgMTEtMi4zLTEwLTQtMTkuNy01LjItMjktNC43LTM4LjIgMS4xLTY3LjkgMTQuNi03NS44IDMtMS44IDYuOS0yLjYgMTEuNS0yLjZWNzguNWMtOC40IDAtMTYgMS44LTIyLjYgNS42LTI4LjEgMTYuMi0zNC40IDY2LjctMTkuOSAxMzAuMS02Mi4yIDE5LjItMTAyLjcgNDkuOS0xMDIuNyA4Mi4zIDAgMzIuNSA0MC43IDYzLjMgMTAzLjEgODIuNC0xNC40IDYzLjYtOCAxMTQuMiAyMC4yIDEzMC40IDYuNSAzLjggMTQuMSA1LjYgMjIuNSA1LjYgMjcuNSAwIDYzLjUtMTkuNiA5OS45LTUzLjYgMzYuNCAzMy44IDcyLjQgNTMuMiA5OS45IDUzLjIgOC40IDAgMTYtMS44IDIyLjYtNS42IDI4LjEtMTYuMiAzNC40LTY2LjcgMTkuOS0xMzAuMSA2Mi0xOS4xIDEwMi41LTQ5LjkgMTAyLjUtODIuM3ptLTEzMC4yLTY2LjdjLTMuNyAxMi45LTguMyAyNi4yLTEzLjUgMzkuNS00LjEtOC04LjQtMTYtMTMuMS0yNC00LjYtOC05LjUtMTUuOC0xNC40LTIzLjQgMTQuMiAyLjEgMjcuOSA0LjcgNDEgNy45em0tNDUuOCAxMDYuNWMtNy44IDEzLjUtMTUuOCAyNi4zLTI0LjEgMzguMi0xNC45IDEuMy0zMCAyLTQ1LjIgMi0xNS4xIDAtMzAuMi0uNy00NS0xLjktOC4zLTExLjktMTYuNC0yNC42LTI0LjItMzgtNy42LTEzLjEtMTQuNS0yNi40LTIwLjgtMzkuOCA2LjItMTMuNCAxMy4yLTI2LjggMjAuNy0zOS45IDcuOC0xMy41IDE1LjgtMjYuMyAyNC4xLTM4LjIgMTQuOS0xLjMgMzAtMiA0NS4yLTIgMTUuMSAwIDMwLjIuNyA0NSAxLjkgOC4zIDExLjkgMTYuNCAyNC42IDI0LjIgMzggNy42IDEzLjEgMTQuNSAyNi40IDIwLjggMzkuOC02LjMgMTMuNC0xMy4yIDI2LjgtMjAuNyAzOS45em0zMi4zLTEzYzUuNCAxMy40IDEwIDI2LjggMTMuOCAzOS44LTEzLjEgMy4yLTI2LjkgNS45LTQxLjIgOCA0LjktNy43IDkuOC0xNS42IDE0LjQtMjMuNyA0LjYtOCA4LjktMTYuMSAxMy0yNC4xek00MjEuMiA0MzBjLTkuMy05LjYtMTguNi0yMC4zLTI3LjgtMzIgOSAuNCAxOC4yLjcgMjcuNS43IDkuNCAwIDE4LjctLjIgMjcuOC0uNy05IDExLjctMTguMyAyMi40LTI3LjUgMzJ6bS03NC40LTU4LjljLTE0LjItMi4xLTI3LjktNC43LTQxLTcuOSAzLjctMTIuOSA4LjMtMjYuMiAxMy41LTM5LjUgNC4xIDggOC40IDE2IDEzLjEgMjQgNC43IDggOS41IDE1LjggMTQuNCAyMy40ek00MjAuNyAxNjNjOS4zIDkuNiAxOC42IDIwLjMgMjcuOCAzMi05LS40LTE4LjItLjctMjcuNS0uNy05LjQgMC0xOC43LjItMjcuOC43IDktMTEuNyAxOC4zLTIyLjQgMjcuNS0zMnptLTc0IDU4LjljLTQuOSA3LjctOS44IDE1LjYtMTQuNCAyMy43LTQuNiA4LTguOSAxNi0xMyAyNC01LjQtMTMuNC0xMC0yNi44LTEzLjgtMzkuOCAxMy4xLTMuMSAyNi45LTUuOCA0MS4yLTcuOXptLTkwLjUgMTI1LjJjLTM1LjQtMTUuMS01OC4zLTM0LjktNTguMy01MC42IDAtMTUuNyAyMi45LTM1LjYgNTguMy01MC42IDguNi0zLjcgMTgtNyAyNy43LTEwLjEgNS43IDE5LjYgMTMuMiA0MCAyMi41IDYwLjktOS4yIDIwLjgtMTYuNiA0MS4xLTIyLjIgNjAuNi05LjktMy4xLTE5LjMtNi41LTI4LTEwLjJ6TTMxMCA0OTBjLTEzLjYtNy44LTE5LjUtMzcuNS0xNC45LTc1LjcgMS4xLTkuNCAyLjktMTkuMyA1LjEtMjkuNCAxOS42IDQuOCA0MSA4LjUgNjMuNSAxMC45IDEzLjUgMTguNSAyNy41IDM1LjMgNDEuNiA1MC0zMi42IDMwLjMtNjMuMiA0Ni45LTg0IDQ2LjktNC41LS4xLTguMy0xLTExLjMtMi43em0yMzcuMi03Ni4yYzQuNyAzOC4yLTEuMSA2Ny45LTE0LjYgNzUuOC0zIDEuOC02LjkgMi42LTExLjUgMi42LTIwLjcgMC01MS40LTE2LjUtODQtNDYuNiAxNC0xNC43IDI4LTMxLjQgNDEuMy00OS45IDIyLjYtMi40IDQ0LTYuMSA2My42LTExIDIuMyAxMC4xIDQuMSAxOS44IDUuMiAyOS4xem0zOC41LTY2LjdjLTguNiAzLjctMTggNy0yNy43IDEwLjEtNS43LTE5LjYtMTMuMi00MC0yMi41LTYwLjkgOS4yLTIwLjggMTYuNi00MS4xIDIyLjItNjAuNiA5LjkgMy4xIDE5LjMgNi41IDI4LjEgMTAuMiAzNS40IDE1LjEgNTguMyAzNC45IDU4LjMgNTAuNi0uMSAxNS43LTIzIDM1LjYtNTguNCA1MC42ek0zMjAuOCA3OC40eiIvPgogICAgPGNpcmNsZSBjeD0iNDIwLjkiIGN5PSIyOTYuNSIgcj0iNDUuNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-redo: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIi8+PHBhdGggZD0iTTE4LjQgMTAuNkMxNi41NSA4Ljk5IDE0LjE1IDggMTEuNSA4Yy00LjY1IDAtOC41OCAzLjAzLTkuOTYgNy4yMkwzLjkgMTZjMS4wNS0zLjE5IDQuMDUtNS41IDcuNi01LjUgMS45NSAwIDMuNzMuNzIgNS4xMiAxLjg4TDEzIDE2aDlWN2wtMy42IDMuNnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-refresh: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTkgMTMuNWMtMi40OSAwLTQuNS0yLjAxLTQuNS00LjVTNi41MSA0LjUgOSA0LjVjMS4yNCAwIDIuMzYuNTIgMy4xNyAxLjMzTDEwIDhoNVYzbC0xLjc2IDEuNzZDMTIuMTUgMy42OCAxMC42NiAzIDkgMyA1LjY5IDMgMy4wMSA1LjY5IDMuMDEgOVM1LjY5IDE1IDkgMTVjMi45NyAwIDUuNDMtMi4xNiA1LjktNWgtMS41MmMtLjQ2IDItMi4yNCAzLjUtNC4zOCAzLjV6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-regex: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiBmaWxsPSIjRkZGIj4KICAgIDxjaXJjbGUgY2xhc3M9InN0MiIgY3g9IjUuNSIgY3k9IjE0LjUiIHI9IjEuNSIvPgogICAgPHJlY3QgeD0iMTIiIHk9IjQiIGNsYXNzPSJzdDIiIHdpZHRoPSIxIiBoZWlnaHQ9IjgiLz4KICAgIDxyZWN0IHg9IjguNSIgeT0iNy41IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjg2NiAtMC41IDAuNSAwLjg2NiAtMi4zMjU1IDcuMzIxOSkiIGNsYXNzPSJzdDIiIHdpZHRoPSI4IiBoZWlnaHQ9IjEiLz4KICAgIDxyZWN0IHg9IjEyIiB5PSI0IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjUgLTAuODY2IDAuODY2IDAuNSAtMC42Nzc5IDE0LjgyNTIpIiBjbGFzcz0ic3QyIiB3aWR0aD0iMSIgaGVpZ2h0PSI4Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-run: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTggNXYxNGwxMS03eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-running: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMjU2IDhDMTE5IDggOCAxMTkgOCAyNTZzMTExIDI0OCAyNDggMjQ4IDI0OC0xMTEgMjQ4LTI0OFMzOTMgOCAyNTYgOHptOTYgMzI4YzAgOC44LTcuMiAxNi0xNiAxNkgxNzZjLTguOCAwLTE2LTcuMi0xNi0xNlYxNzZjMC04LjggNy4yLTE2IDE2LTE2aDE2MGM4LjggMCAxNiA3LjIgMTYgMTZ2MTYweiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-save: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE3IDNINWMtMS4xMSAwLTIgLjktMiAydjE0YzAgMS4xLjg5IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjdsLTQtNHptLTUgMTZjLTEuNjYgMC0zLTEuMzQtMy0zczEuMzQtMyAzLTMgMyAxLjM0IDMgMy0xLjM0IDMtMyAzem0zLTEwSDVWNWgxMHY0eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-search: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-settings: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuNDMgMTIuOThjLjA0LS4zMi4wNy0uNjQuMDctLjk4cy0uMDMtLjY2LS4wNy0uOThsMi4xMS0xLjY1Yy4xOS0uMTUuMjQtLjQyLjEyLS42NGwtMi0zLjQ2Yy0uMTItLjIyLS4zOS0uMy0uNjEtLjIybC0yLjQ5IDFjLS41Mi0uNC0xLjA4LS43My0xLjY5LS45OGwtLjM4LTIuNjVBLjQ4OC40ODggMCAwMDE0IDJoLTRjLS4yNSAwLS40Ni4xOC0uNDkuNDJsLS4zOCAyLjY1Yy0uNjEuMjUtMS4xNy41OS0xLjY5Ljk4bC0yLjQ5LTFjLS4yMy0uMDktLjQ5IDAtLjYxLjIybC0yIDMuNDZjLS4xMy4yMi0uMDcuNDkuMTIuNjRsMi4xMSAxLjY1Yy0uMDQuMzItLjA3LjY1LS4wNy45OHMuMDMuNjYuMDcuOThsLTIuMTEgMS42NWMtLjE5LjE1LS4yNC40Mi0uMTIuNjRsMiAzLjQ2Yy4xMi4yMi4zOS4zLjYxLjIybDIuNDktMWMuNTIuNCAxLjA4LjczIDEuNjkuOThsLjM4IDIuNjVjLjAzLjI0LjI0LjQyLjQ5LjQyaDRjLjI1IDAgLjQ2LS4xOC40OS0uNDJsLjM4LTIuNjVjLjYxLS4yNSAxLjE3LS41OSAxLjY5LS45OGwyLjQ5IDFjLjIzLjA5LjQ5IDAgLjYxLS4yMmwyLTMuNDZjLjEyLS4yMi4wNy0uNDktLjEyLS42NGwtMi4xMS0xLjY1ek0xMiAxNS41Yy0xLjkzIDAtMy41LTEuNTctMy41LTMuNXMxLjU3LTMuNSAzLjUtMy41IDMuNSAxLjU3IDMuNSAzLjUtMS41NyAzLjUtMy41IDMuNXoiLz4KPC9zdmc+Cg==);
  --jp-icon-share: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTSAxOCAyIEMgMTYuMzU0OTkgMiAxNSAzLjM1NDk5MDQgMTUgNSBDIDE1IDUuMTkwOTUyOSAxNS4wMjE3OTEgNS4zNzcxMjI0IDE1LjA1NjY0MSA1LjU1ODU5MzggTCA3LjkyMTg3NSA5LjcyMDcwMzEgQyA3LjM5ODUzOTkgOS4yNzc4NTM5IDYuNzMyMDc3MSA5IDYgOSBDIDQuMzU0OTkwNCA5IDMgMTAuMzU0OTkgMyAxMiBDIDMgMTMuNjQ1MDEgNC4zNTQ5OTA0IDE1IDYgMTUgQyA2LjczMjA3NzEgMTUgNy4zOTg1Mzk5IDE0LjcyMjE0NiA3LjkyMTg3NSAxNC4yNzkyOTcgTCAxNS4wNTY2NDEgMTguNDM5NDUzIEMgMTUuMDIxNTU1IDE4LjYyMTUxNCAxNSAxOC44MDgzODYgMTUgMTkgQyAxNSAyMC42NDUwMSAxNi4zNTQ5OSAyMiAxOCAyMiBDIDE5LjY0NTAxIDIyIDIxIDIwLjY0NTAxIDIxIDE5IEMgMjEgMTcuMzU0OTkgMTkuNjQ1MDEgMTYgMTggMTYgQyAxNy4yNjc0OCAxNiAxNi42MDE1OTMgMTYuMjc5MzI4IDE2LjA3ODEyNSAxNi43MjI2NTYgTCA4Ljk0MzM1OTQgMTIuNTU4NTk0IEMgOC45NzgyMDk1IDEyLjM3NzEyMiA5IDEyLjE5MDk1MyA5IDEyIEMgOSAxMS44MDkwNDcgOC45NzgyMDk1IDExLjYyMjg3OCA4Ljk0MzM1OTQgMTEuNDQxNDA2IEwgMTYuMDc4MTI1IDcuMjc5Mjk2OSBDIDE2LjYwMTQ2IDcuNzIyMTQ2MSAxNy4yNjc5MjMgOCAxOCA4IEMgMTkuNjQ1MDEgOCAyMSA2LjY0NTAwOTYgMjEgNSBDIDIxIDMuMzU0OTkwNCAxOS42NDUwMSAyIDE4IDIgeiBNIDE4IDQgQyAxOC41NjQxMjkgNCAxOSA0LjQzNTg3MDYgMTkgNSBDIDE5IDUuNTY0MTI5NCAxOC41NjQxMjkgNiAxOCA2IEMgMTcuNDM1ODcxIDYgMTcgNS41NjQxMjk0IDE3IDUgQyAxNyA0LjQzNTg3MDYgMTcuNDM1ODcxIDQgMTggNCB6IE0gNiAxMSBDIDYuNTY0MTI5NCAxMSA3IDExLjQzNTg3MSA3IDEyIEMgNyAxMi41NjQxMjkgNi41NjQxMjk0IDEzIDYgMTMgQyA1LjQzNTg3MDYgMTMgNSAxMi41NjQxMjkgNSAxMiBDIDUgMTEuNDM1ODcxIDUuNDM1ODcwNiAxMSA2IDExIHogTSAxOCAxOCBDIDE4LjU2NDEyOSAxOCAxOSAxOC40MzU4NzEgMTkgMTkgQyAxOSAxOS41NjQxMjkgMTguNTY0MTI5IDIwIDE4IDIwIEMgMTcuNDM1ODcxIDIwIDE3IDE5LjU2NDEyOSAxNyAxOSBDIDE3IDE4LjQzNTg3MSAxNy40MzU4NzEgMTggMTggMTggeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-spreadsheet: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNENBRjUwIiBkPSJNMi4yIDIuMnYxNy42aDE3LjZWMi4ySDIuMnptMTUuNCA3LjdoLTUuNVY0LjRoNS41djUuNXpNOS45IDQuNHY1LjVINC40VjQuNGg1LjV6bS01LjUgNy43aDUuNXY1LjVINC40di01LjV6bTcuNyA1LjV2LTUuNWg1LjV2NS41aC01LjV6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-stop: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik02IDZoMTJ2MTJINnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tab: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIxIDNIM2MtMS4xIDAtMiAuOS0yIDJ2MTRjMCAxLjEuOSAyIDIgMmgxOGMxLjEgMCAyLS45IDItMlY1YzAtMS4xLS45LTItMi0yem0wIDE2SDNWNWgxMHY0aDh2MTB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-table-rows: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMSw4SDNWNGgxOFY4eiBNMjEsMTBIM3Y0aDE4VjEweiBNMjEsMTZIM3Y0aDE4VjE2eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-tag: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjgiIGhlaWdodD0iMjgiIHZpZXdCb3g9IjAgMCA0MyAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTI4LjgzMzIgMTIuMzM0TDMyLjk5OTggMTYuNTAwN0wzNy4xNjY1IDEyLjMzNEgyOC44MzMyWiIvPgoJCTxwYXRoIGQ9Ik0xNi4yMDk1IDIxLjYxMDRDMTUuNjg3MyAyMi4xMjk5IDE0Ljg0NDMgMjIuMTI5OSAxNC4zMjQ4IDIxLjYxMDRMNi45ODI5IDE0LjcyNDVDNi41NzI0IDE0LjMzOTQgNi4wODMxMyAxMy42MDk4IDYuMDQ3ODYgMTMuMDQ4MkM1Ljk1MzQ3IDExLjUyODggNi4wMjAwMiA4LjYxOTQ0IDYuMDY2MjEgNy4wNzY5NUM2LjA4MjgxIDYuNTE0NzcgNi41NTU0OCA2LjA0MzQ3IDcuMTE4MDQgNi4wMzA1NUM5LjA4ODYzIDUuOTg0NzMgMTMuMjYzOCA1LjkzNTc5IDEzLjY1MTggNi4zMjQyNUwyMS43MzY5IDEzLjYzOUMyMi4yNTYgMTQuMTU4NSAyMS43ODUxIDE1LjQ3MjQgMjEuMjYyIDE1Ljk5NDZMMTYuMjA5NSAyMS42MTA0Wk05Ljc3NTg1IDguMjY1QzkuMzM1NTEgNy44MjU2NiA4LjYyMzUxIDcuODI1NjYgOC4xODI4IDguMjY1QzcuNzQzNDYgOC43MDU3MSA3Ljc0MzQ2IDkuNDE3MzMgOC4xODI4IDkuODU2NjdDOC42MjM4MiAxMC4yOTY0IDkuMzM1ODIgMTAuMjk2NCA5Ljc3NTg1IDkuODU2NjdDMTAuMjE1NiA5LjQxNzMzIDEwLjIxNTYgOC43MDUzMyA5Ljc3NTg1IDguMjY1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-terminal: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0IiA+CiAgICA8cmVjdCBjbGFzcz0ianAtdGVybWluYWwtaWNvbi1iYWNrZ3JvdW5kLWNvbG9yIGpwLWljb24tc2VsZWN0YWJsZSIgd2lkdGg9IjIwIiBoZWlnaHQ9IjIwIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgyIDIpIiBmaWxsPSIjMzMzMzMzIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtdGVybWluYWwtaWNvbi1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUtaW52ZXJzZSIgZD0iTTUuMDU2NjQgOC43NjE3MkM1LjA1NjY0IDguNTk3NjYgNS4wMzEyNSA4LjQ1MzEyIDQuOTgwNDcgOC4zMjgxMkM0LjkzMzU5IDguMTk5MjIgNC44NTU0NyA4LjA4MjAzIDQuNzQ2MDkgNy45NzY1NkM0LjY0MDYyIDcuODcxMDkgNC41IDcuNzc1MzkgNC4zMjQyMiA3LjY4OTQ1QzQuMTUyMzQgNy41OTk2MSAzLjk0MzM2IDcuNTExNzIgMy42OTcyNyA3LjQyNTc4QzMuMzAyNzMgNy4yODUxNiAyLjk0MzM2IDcuMTM2NzIgMi42MTkxNCA2Ljk4MDQ3QzIuMjk0OTIgNi44MjQyMiAyLjAxNzU4IDYuNjQyNTggMS43ODcxMSA2LjQzNTU1QzEuNTYwNTUgNi4yMjg1MiAxLjM4NDc3IDUuOTg4MjggMS4yNTk3NyA1LjcxNDg0QzEuMTM0NzcgNS40Mzc1IDEuMDcyMjcgNS4xMDkzOCAxLjA3MjI3IDQuNzMwNDdDMS4wNzIyNyA0LjM5ODQ0IDEuMTI4OTEgNC4wOTU3IDEuMjQyMTkgMy44MjIyN0MxLjM1NTQ3IDMuNTQ0OTIgMS41MTU2MiAzLjMwNDY5IDEuNzIyNjYgMy4xMDE1NkMxLjkyOTY5IDIuODk4NDQgMi4xNzk2OSAyLjczNDM3IDIuNDcyNjYgMi42MDkzOEMyLjc2NTYyIDIuNDg0MzggMy4wOTE4IDIuNDA0MyAzLjQ1MTE3IDIuMzY5MTRWMS4xMDkzOEg0LjM4ODY3VjIuMzgwODZDNC43NDAyMyAyLjQyNzczIDUuMDU2NjQgMi41MjM0NCA1LjMzNzg5IDIuNjY3OTdDNS42MTkxNCAyLjgxMjUgNS44NTc0MiAzLjAwMTk1IDYuMDUyNzMgMy4yMzYzM0M2LjI1MTk1IDMuNDY2OCA2LjQwNDMgMy43NDAyMyA2LjUwOTc3IDQuMDU2NjRDNi42MTkxNCA0LjM2OTE0IDYuNjczODMgNC43MjA3IDYuNjczODMgNS4xMTEzM0g1LjA0NDkyQzUuMDQ0OTIgNC42Mzg2NyA0LjkzNzUgNC4yODEyNSA0LjcyMjY2IDQuMDM5MDZDNC41MDc4MSAzLjc5Mjk3IDQuMjE2OCAzLjY2OTkyIDMuODQ5NjEgMy42Njk5MkMzLjY1MDM5IDMuNjY5OTIgMy40NzY1NiAzLjY5NzI3IDMuMzI4MTIgMy43NTE5NUMzLjE4MzU5IDMuODAyNzMgMy4wNjQ0NSAzLjg3Njk1IDIuOTcwNyAzLjk3NDYxQzIuODc2OTUgNC4wNjgzNiAyLjgwNjY0IDQuMTc5NjkgMi43NTk3NyA0LjMwODU5QzIuNzE2OCA0LjQzNzUgMi42OTUzMSA0LjU3ODEyIDIuNjk1MzEgNC43MzA0N0MyLjY5NTMxIDQuODgyODEgMi43MTY4IDUuMDE5NTMgMi43NTk3NyA1LjE0MDYyQzIuODA2NjQgNS4yNTc4MSAyLjg4MjgxIDUuMzY3MTkgMi45ODgyOCA1LjQ2ODc1QzMuMDk3NjYgNS41NzAzMSAzLjI0MDIzIDUuNjY3OTcgMy40MTYwMiA1Ljc2MTcyQzMuNTkxOCA1Ljg1MTU2IDMuODEwNTUgNS45NDMzNiA0LjA3MjI3IDYuMDM3MTFDNC40NjY4IDYuMTg1NTUgNC44MjQyMiA2LjMzOTg0IDUuMTQ0NTMgNi41QzUuNDY0ODQgNi42NTYyNSA1LjczODI4IDYuODM5ODQgNS45NjQ4NCA3LjA1MDc4QzYuMTk1MzEgNy4yNTc4MSA2LjM3MTA5IDcuNSA2LjQ5MjE5IDcuNzc3MzRDNi42MTcxOSA4LjA1MDc4IDYuNjc5NjkgOC4zNzUgNi42Nzk2OSA4Ljc1QzYuNjc5NjkgOS4wOTM3NSA2LjYyMzA1IDkuNDA0MyA2LjUwOTc3IDkuNjgxNjRDNi4zOTY0OCA5Ljk1NTA4IDYuMjM0MzggMTAuMTkxNCA2LjAyMzQ0IDEwLjM5MDZDNS44MTI1IDEwLjU4OTggNS41NTg1OSAxMC43NSA1LjI2MTcyIDEwLjg3MTFDNC45NjQ4NCAxMC45ODgzIDQuNjMyODEgMTEuMDY0NSA0LjI2NTYyIDExLjA5OTZWMTIuMjQ4SDMuMzMzOThWMTEuMDk5NkMzLjAwMTk1IDExLjA2ODQgMi42Nzk2OSAxMC45OTYxIDIuMzY3MTkgMTAuODgyOEMyLjA1NDY5IDEwLjc2NTYgMS43NzczNCAxMC41OTc3IDEuNTM1MTYgMTAuMzc4OUMxLjI5Njg4IDEwLjE2MDIgMS4xMDU0NyA5Ljg4NDc3IDAuOTYwOTM4IDkuNTUyNzNDMC44MTY0MDYgOS4yMTY4IDAuNzQ0MTQxIDguODE0NDUgMC43NDQxNDEgOC4zNDU3SDIuMzc4OTFDMi4zNzg5MSA4LjYyNjk1IDIuNDE5OTIgOC44NjMyOCAyLjUwMTk1IDkuMDU0NjlDMi41ODM5OCA5LjI0MjE5IDIuNjg5NDUgOS4zOTI1OCAyLjgxODM2IDkuNTA1ODZDMi45NTExNyA5LjYxNTIzIDMuMTAxNTYgOS42OTMzNiAzLjI2OTUzIDkuNzQwMjNDMy40Mzc1IDkuNzg3MTEgMy42MDkzOCA5LjgxMDU1IDMuNzg1MTYgOS44MTA1NUM0LjIwMzEyIDkuODEwNTUgNC41MTk1MyA5LjcxMjg5IDQuNzM0MzggOS41MTc1OEM0Ljk0OTIyIDkuMzIyMjcgNS4wNTY2NCA5LjA3MDMxIDUuMDU2NjQgOC43NjE3MlpNMTMuNDE4IDEyLjI3MTVIOC4wNzQyMlYxMUgxMy40MThWMTIuMjcxNVoiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMuOTUyNjQgNikiIGZpbGw9IndoaXRlIi8+Cjwvc3ZnPgo=);
  --jp-icon-text-editor: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtdGV4dC1lZGl0b3ItaWNvbi1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xNSAxNUgzdjJoMTJ2LTJ6bTAtOEgzdjJoMTJWN3pNMyAxM2gxOHYtMkgzdjJ6bTAgOGgxOHYtMkgzdjJ6TTMgM3YyaDE4VjNIM3oiLz4KPC9zdmc+Cg==);
  --jp-icon-toc: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik03LDVIMjFWN0g3VjVNNywxM1YxMUgyMVYxM0g3TTQsNC41QTEuNSwxLjUgMCAwLDEgNS41LDZBMS41LDEuNSAwIDAsMSA0LDcuNUExLjUsMS41IDAgMCwxIDIuNSw2QTEuNSwxLjUgMCAwLDEgNCw0LjVNNCwxMC41QTEuNSwxLjUgMCAwLDEgNS41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMy41QTEuNSwxLjUgMCAwLDEgMi41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMC41TTcsMTlWMTdIMjFWMTlIN000LDE2LjVBMS41LDEuNSAwIDAsMSA1LjUsMThBMS41LDEuNSAwIDAsMSA0LDE5LjVBMS41LDEuNSAwIDAsMSAyLjUsMThBMS41LDEuNSAwIDAsMSA0LDE2LjVaIiAvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tree-view: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMiAxMVYzaC03djNIOVYzSDJ2OGg3VjhoMnYxMGg0djNoN3YtOGgtN3YzaC0yVjhoMnYzeiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMiAxNy4xODQ0IDIuOTY5NjggMTQuMzAzMiAxLjg2MDk0IDExLjQ0MDlaIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiMzMzMzMzMiIHN0cm9rZT0iIzMzMzMzMyIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOCA5Ljg2NzE5KSIgZD0iTTIuODYwMTUgNC44NjUzNUwwLjcyNjU0OSAyLjk5OTU5TDAgMy42MzA0NUwyLjg2MDE1IDYuMTMxNTdMOCAwLjYzMDg3Mkw3LjI3ODU3IDBMMi44NjAxNSA0Ljg2NTM1WiIvPgo8L3N2Zz4K);
  --jp-icon-undo: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjUgOGMtMi42NSAwLTUuMDUuOTktNi45IDIuNkwyIDd2OWg5bC0zLjYyLTMuNjJjMS4zOS0xLjE2IDMuMTYtMS44OCA1LjEyLTEuODggMy41NCAwIDYuNTUgMi4zMSA3LjYgNS41bDIuMzctLjc4QzIxLjA4IDExLjAzIDE3LjE1IDggMTIuNSA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-user: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE2IDdhNCA0IDAgMTEtOCAwIDQgNCAwIDAxOCAwek0xMiAxNGE3IDcgMCAwMC03IDdoMTRhNyA3IDAgMDAtNy03eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-users: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDM2IDI0IiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPgogPGcgY2xhc3M9ImpwLWljb24zIiB0cmFuc2Zvcm09Im1hdHJpeCgxLjczMjcgMCAwIDEuNzMyNyAtMy42MjgyIC4wOTk1NzcpIiBmaWxsPSIjNjE2MTYxIj4KICA8cGF0aCB0cmFuc2Zvcm09Im1hdHJpeCgxLjUsMCwwLDEuNSwwLC02KSIgZD0ibTEyLjE4NiA3LjUwOThjLTEuMDUzNSAwLTEuOTc1NyAwLjU2NjUtMi40Nzg1IDEuNDEwMiAwLjc1MDYxIDAuMzEyNzcgMS4zOTc0IDAuODI2NDggMS44NzMgMS40NzI3aDMuNDg2M2MwLTEuNTkyLTEuMjg4OS0yLjg4MjgtMi44ODA5LTIuODgyOHoiLz4KICA8cGF0aCBkPSJtMjAuNDY1IDIuMzg5NWEyLjE4ODUgMi4xODg1IDAgMCAxLTIuMTg4NCAyLjE4ODUgMi4xODg1IDIuMTg4NSAwIDAgMS0yLjE4ODUtMi4xODg1IDIuMTg4NSAyLjE4ODUgMCAwIDEgMi4xODg1LTIuMTg4NSAyLjE4ODUgMi4xODg1IDAgMCAxIDIuMTg4NCAyLjE4ODV6Ii8+CiAgPHBhdGggdHJhbnNmb3JtPSJtYXRyaXgoMS41LDAsMCwxLjUsMCwtNikiIGQ9Im0zLjU4OTggOC40MjE5Yy0xLjExMjYgMC0yLjAxMzcgMC45MDExMS0yLjAxMzcgMi4wMTM3aDIuODE0NWMwLjI2Nzk3LTAuMzczMDkgMC41OTA3LTAuNzA0MzUgMC45NTg5OC0wLjk3ODUyLTAuMzQ0MzMtMC42MTY4OC0xLjAwMzEtMS4wMzUyLTEuNzU5OC0xLjAzNTJ6Ii8+CiAgPHBhdGggZD0ibTYuOTE1NCA0LjYyM2ExLjUyOTQgMS41Mjk0IDAgMCAxLTEuNTI5NCAxLjUyOTQgMS41Mjk0IDEuNTI5NCAwIDAgMS0xLjUyOTQtMS41Mjk0IDEuNTI5NCAxLjUyOTQgMCAwIDEgMS41Mjk0LTEuNTI5NCAxLjUyOTQgMS41Mjk0IDAgMCAxIDEuNTI5NCAxLjUyOTR6Ii8+CiAgPHBhdGggZD0ibTYuMTM1IDEzLjUzNWMwLTMuMjM5MiAyLjYyNTktNS44NjUgNS44NjUtNS44NjUgMy4yMzkyIDAgNS44NjUgMi42MjU5IDUuODY1IDUuODY1eiIvPgogIDxjaXJjbGUgY3g9IjEyIiBjeT0iMy43Njg1IiByPSIyLjk2ODUiLz4KIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-vega: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbjEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjEyMTIxIj4KICAgIDxwYXRoIGQ9Ik0xMC42IDUuNGwyLjItMy4ySDIuMnY3LjNsNC02LjZ6Ii8+CiAgICA8cGF0aCBkPSJNMTUuOCAyLjJsLTQuNCA2LjZMNyA2LjNsLTQuOCA4djUuNWgxNy42VjIuMmgtNHptLTcgMTUuNEg1LjV2LTQuNGgzLjN2NC40em00LjQgMEg5LjhWOS44aDMuNHY3Ljh6bTQuNCAwaC0zLjRWNi41aDMuNHYxMS4xeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-word: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KIDxnIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzQxNDE0MSI+CiAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiA8L2c+CiA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSguNDMgLjA0MDEpIiBmaWxsPSIjZmZmIj4KICA8cGF0aCBkPSJtNC4xNCA4Ljc2cTAuMDY4Mi0xLjg5IDIuNDItMS44OSAxLjE2IDAgMS42OCAwLjQyIDAuNTY3IDAuNDEgMC41NjcgMS4xNnYzLjQ3cTAgMC40NjIgMC41MTQgMC40NjIgMC4xMDMgMCAwLjItMC4wMjMxdjAuNzE0cS0wLjM5OSAwLjEwMy0wLjY1MSAwLjEwMy0wLjQ1MiAwLTAuNjkzLTAuMjItMC4yMzEtMC4yLTAuMjg0LTAuNjYyLTAuOTU2IDAuODcyLTIgMC44NzItMC45MDMgMC0xLjQ3LTAuNDcyLTAuNTI1LTAuNDcyLTAuNTI1LTEuMjYgMC0wLjI2MiAwLjA0NTItMC40NzIgMC4wNTY3LTAuMjIgMC4xMTYtMC4zNzggMC4wNjgyLTAuMTY4IDAuMjMxLTAuMzA0IDAuMTU4LTAuMTQ3IDAuMjYyLTAuMjQyIDAuMTE2LTAuMDkxNCAwLjM2OC0wLjE2OCAwLjI2Mi0wLjA5MTQgMC4zOTktMC4xMjYgMC4xMzYtMC4wNDUyIDAuNDcyLTAuMTAzIDAuMzM2LTAuMDU3OCAwLjUwNC0wLjA3OTggMC4xNTgtMC4wMjMxIDAuNTY3LTAuMDc5OCAwLjU1Ni0wLjA2ODIgMC43NzctMC4yMjEgMC4yMi0wLjE1MiAwLjIyLTAuNDQxdi0wLjI1MnEwLTAuNDMtMC4zNTctMC42NjItMC4zMzYtMC4yMzEtMC45NzYtMC4yMzEtMC42NjIgMC0wLjk5OCAwLjI2Mi0wLjMzNiAwLjI1Mi0wLjM5OSAwLjc5OHptMS44OSAzLjY4cTAuNzg4IDAgMS4yNi0wLjQxIDAuNTA0LTAuNDIgMC41MDQtMC45MDN2LTEuMDVxLTAuMjg0IDAuMTM2LTAuODYxIDAuMjMxLTAuNTY3IDAuMDkxNC0wLjk4NyAwLjE1OC0wLjQyIDAuMDY4Mi0wLjc2NiAwLjMyNi0wLjMzNiAwLjI1Mi0wLjMzNiAwLjcwNHQwLjMwNCAwLjcwNCAwLjg2MSAwLjI1MnoiIHN0cm9rZS13aWR0aD0iMS4wNSIvPgogIDxwYXRoIGQ9Im0xMCA0LjU2aDAuOTQ1djMuMTVxMC42NTEtMC45NzYgMS44OS0wLjk3NiAxLjE2IDAgMS44OSAwLjg0IDAuNjgyIDAuODQgMC42ODIgMi4zMSAwIDEuNDctMC43MDQgMi40Mi0wLjcwNCAwLjg4Mi0xLjg5IDAuODgyLTEuMjYgMC0xLjg5LTEuMDJ2MC43NjZoLTAuODV6bTIuNjIgMy4wNHEtMC43NDYgMC0xLjE2IDAuNjQtMC40NTIgMC42My0wLjQ1MiAxLjY4IDAgMS4wNSAwLjQ1MiAxLjY4dDEuMTYgMC42M3EwLjc3NyAwIDEuMjYtMC42MyAwLjQ5NC0wLjY0IDAuNDk0LTEuNjggMC0xLjA1LTAuNDcyLTEuNjgtMC40NjItMC42NC0xLjI2LTAuNjR6IiBzdHJva2Utd2lkdGg9IjEuMDUiLz4KICA8cGF0aCBkPSJtMi43MyAxNS44IDEzLjYgMC4wMDgxYzAuMDA2OSAwIDAtMi42IDAtMi42IDAtMC4wMDc4LTEuMTUgMC0xLjE1IDAtMC4wMDY5IDAtMC4wMDgzIDEuNS0wLjAwODMgMS41LTJlLTMgLTAuMDAxNC0xMS4zLTAuMDAxNC0xMS4zLTAuMDAxNGwtMC4wMDU5Mi0xLjVjMC0wLjAwNzgtMS4xNyAwLjAwMTMtMS4xNyAwLjAwMTN6IiBzdHJva2Utd2lkdGg9Ii45NzUiLz4KIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-yaml: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1jb250cmFzdDIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjRDgxQjYwIj4KICAgIDxwYXRoIGQ9Ik03LjIgMTguNnYtNS40TDMgNS42aDMuM2wxLjQgMy4xYy4zLjkuNiAxLjYgMSAyLjUuMy0uOC42LTEuNiAxLTIuNWwxLjQtMy4xaDMuNGwtNC40IDcuNnY1LjVsLTIuOS0uMXoiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxNi41IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxMSIgcj0iMi4xIi8+CiAgPC9nPgo8L3N2Zz4K);
}

/* Icon CSS class declarations */

.jp-AddAboveIcon {
  background-image: var(--jp-icon-add-above);
}

.jp-AddBelowIcon {
  background-image: var(--jp-icon-add-below);
}

.jp-AddIcon {
  background-image: var(--jp-icon-add);
}

.jp-BellIcon {
  background-image: var(--jp-icon-bell);
}

.jp-BugDotIcon {
  background-image: var(--jp-icon-bug-dot);
}

.jp-BugIcon {
  background-image: var(--jp-icon-bug);
}

.jp-BuildIcon {
  background-image: var(--jp-icon-build);
}

.jp-CaretDownEmptyIcon {
  background-image: var(--jp-icon-caret-down-empty);
}

.jp-CaretDownEmptyThinIcon {
  background-image: var(--jp-icon-caret-down-empty-thin);
}

.jp-CaretDownIcon {
  background-image: var(--jp-icon-caret-down);
}

.jp-CaretLeftIcon {
  background-image: var(--jp-icon-caret-left);
}

.jp-CaretRightIcon {
  background-image: var(--jp-icon-caret-right);
}

.jp-CaretUpEmptyThinIcon {
  background-image: var(--jp-icon-caret-up-empty-thin);
}

.jp-CaretUpIcon {
  background-image: var(--jp-icon-caret-up);
}

.jp-CaseSensitiveIcon {
  background-image: var(--jp-icon-case-sensitive);
}

.jp-CheckIcon {
  background-image: var(--jp-icon-check);
}

.jp-CircleEmptyIcon {
  background-image: var(--jp-icon-circle-empty);
}

.jp-CircleIcon {
  background-image: var(--jp-icon-circle);
}

.jp-ClearIcon {
  background-image: var(--jp-icon-clear);
}

.jp-CloseIcon {
  background-image: var(--jp-icon-close);
}

.jp-CodeCheckIcon {
  background-image: var(--jp-icon-code-check);
}

.jp-CodeIcon {
  background-image: var(--jp-icon-code);
}

.jp-CollapseAllIcon {
  background-image: var(--jp-icon-collapse-all);
}

.jp-ConsoleIcon {
  background-image: var(--jp-icon-console);
}

.jp-CopyIcon {
  background-image: var(--jp-icon-copy);
}

.jp-CopyrightIcon {
  background-image: var(--jp-icon-copyright);
}

.jp-CutIcon {
  background-image: var(--jp-icon-cut);
}

.jp-DeleteIcon {
  background-image: var(--jp-icon-delete);
}

.jp-DownloadIcon {
  background-image: var(--jp-icon-download);
}

.jp-DuplicateIcon {
  background-image: var(--jp-icon-duplicate);
}

.jp-EditIcon {
  background-image: var(--jp-icon-edit);
}

.jp-EllipsesIcon {
  background-image: var(--jp-icon-ellipses);
}

.jp-ErrorIcon {
  background-image: var(--jp-icon-error);
}

.jp-ExpandAllIcon {
  background-image: var(--jp-icon-expand-all);
}

.jp-ExtensionIcon {
  background-image: var(--jp-icon-extension);
}

.jp-FastForwardIcon {
  background-image: var(--jp-icon-fast-forward);
}

.jp-FileIcon {
  background-image: var(--jp-icon-file);
}

.jp-FileUploadIcon {
  background-image: var(--jp-icon-file-upload);
}

.jp-FilterDotIcon {
  background-image: var(--jp-icon-filter-dot);
}

.jp-FilterIcon {
  background-image: var(--jp-icon-filter);
}

.jp-FilterListIcon {
  background-image: var(--jp-icon-filter-list);
}

.jp-FolderFavoriteIcon {
  background-image: var(--jp-icon-folder-favorite);
}

.jp-FolderIcon {
  background-image: var(--jp-icon-folder);
}

.jp-HomeIcon {
  background-image: var(--jp-icon-home);
}

.jp-Html5Icon {
  background-image: var(--jp-icon-html5);
}

.jp-ImageIcon {
  background-image: var(--jp-icon-image);
}

.jp-InfoIcon {
  background-image: var(--jp-icon-info);
}

.jp-InspectorIcon {
  background-image: var(--jp-icon-inspector);
}

.jp-JsonIcon {
  background-image: var(--jp-icon-json);
}

.jp-JuliaIcon {
  background-image: var(--jp-icon-julia);
}

.jp-JupyterFaviconIcon {
  background-image: var(--jp-icon-jupyter-favicon);
}

.jp-JupyterIcon {
  background-image: var(--jp-icon-jupyter);
}

.jp-JupyterlabWordmarkIcon {
  background-image: var(--jp-icon-jupyterlab-wordmark);
}

.jp-KernelIcon {
  background-image: var(--jp-icon-kernel);
}

.jp-KeyboardIcon {
  background-image: var(--jp-icon-keyboard);
}

.jp-LaunchIcon {
  background-image: var(--jp-icon-launch);
}

.jp-LauncherIcon {
  background-image: var(--jp-icon-launcher);
}

.jp-LineFormIcon {
  background-image: var(--jp-icon-line-form);
}

.jp-LinkIcon {
  background-image: var(--jp-icon-link);
}

.jp-ListIcon {
  background-image: var(--jp-icon-list);
}

.jp-MarkdownIcon {
  background-image: var(--jp-icon-markdown);
}

.jp-MoveDownIcon {
  background-image: var(--jp-icon-move-down);
}

.jp-MoveUpIcon {
  background-image: var(--jp-icon-move-up);
}

.jp-NewFolderIcon {
  background-image: var(--jp-icon-new-folder);
}

.jp-NotTrustedIcon {
  background-image: var(--jp-icon-not-trusted);
}

.jp-NotebookIcon {
  background-image: var(--jp-icon-notebook);
}

.jp-NumberingIcon {
  background-image: var(--jp-icon-numbering);
}

.jp-OfflineBoltIcon {
  background-image: var(--jp-icon-offline-bolt);
}

.jp-PaletteIcon {
  background-image: var(--jp-icon-palette);
}

.jp-PasteIcon {
  background-image: var(--jp-icon-paste);
}

.jp-PdfIcon {
  background-image: var(--jp-icon-pdf);
}

.jp-PythonIcon {
  background-image: var(--jp-icon-python);
}

.jp-RKernelIcon {
  background-image: var(--jp-icon-r-kernel);
}

.jp-ReactIcon {
  background-image: var(--jp-icon-react);
}

.jp-RedoIcon {
  background-image: var(--jp-icon-redo);
}

.jp-RefreshIcon {
  background-image: var(--jp-icon-refresh);
}

.jp-RegexIcon {
  background-image: var(--jp-icon-regex);
}

.jp-RunIcon {
  background-image: var(--jp-icon-run);
}

.jp-RunningIcon {
  background-image: var(--jp-icon-running);
}

.jp-SaveIcon {
  background-image: var(--jp-icon-save);
}

.jp-SearchIcon {
  background-image: var(--jp-icon-search);
}

.jp-SettingsIcon {
  background-image: var(--jp-icon-settings);
}

.jp-ShareIcon {
  background-image: var(--jp-icon-share);
}

.jp-SpreadsheetIcon {
  background-image: var(--jp-icon-spreadsheet);
}

.jp-StopIcon {
  background-image: var(--jp-icon-stop);
}

.jp-TabIcon {
  background-image: var(--jp-icon-tab);
}

.jp-TableRowsIcon {
  background-image: var(--jp-icon-table-rows);
}

.jp-TagIcon {
  background-image: var(--jp-icon-tag);
}

.jp-TerminalIcon {
  background-image: var(--jp-icon-terminal);
}

.jp-TextEditorIcon {
  background-image: var(--jp-icon-text-editor);
}

.jp-TocIcon {
  background-image: var(--jp-icon-toc);
}

.jp-TreeViewIcon {
  background-image: var(--jp-icon-tree-view);
}

.jp-TrustedIcon {
  background-image: var(--jp-icon-trusted);
}

.jp-UndoIcon {
  background-image: var(--jp-icon-undo);
}

.jp-UserIcon {
  background-image: var(--jp-icon-user);
}

.jp-UsersIcon {
  background-image: var(--jp-icon-users);
}

.jp-VegaIcon {
  background-image: var(--jp-icon-vega);
}

.jp-WordIcon {
  background-image: var(--jp-icon-word);
}

.jp-YamlIcon {
  background-image: var(--jp-icon-yaml);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

.jp-Icon,
.jp-MaterialIcon {
  background-position: center;
  background-repeat: no-repeat;
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-cover {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

/**
 * (DEPRECATED) Support for specific CSS icon sizes
 */

.jp-Icon-16 {
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-18 {
  background-size: 18px;
  min-width: 18px;
  min-height: 18px;
}

.jp-Icon-20 {
  background-size: 20px;
  min-width: 20px;
  min-height: 20px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.lm-TabBar .lm-TabBar-addButton {
  align-items: center;
  display: flex;
  padding: 4px;
  padding-bottom: 5px;
  margin-right: 1px;
  background-color: var(--jp-layout-color2);
}

.lm-TabBar .lm-TabBar-addButton:hover {
  background-color: var(--jp-layout-color1);
}

.lm-DockPanel-tabBar .lm-TabBar-tab {
  width: var(--jp-private-horizontal-tab-width);
}

.lm-DockPanel-tabBar .lm-TabBar-content {
  flex: unset;
}

.lm-DockPanel-tabBar[data-orientation='horizontal'] {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for icons as inline SVG HTMLElements
 */

/* recolor the primary elements of an icon */
.jp-icon0[fill] {
  fill: var(--jp-inverse-layout-color0);
}

.jp-icon1[fill] {
  fill: var(--jp-inverse-layout-color1);
}

.jp-icon2[fill] {
  fill: var(--jp-inverse-layout-color2);
}

.jp-icon3[fill] {
  fill: var(--jp-inverse-layout-color3);
}

.jp-icon4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}

.jp-icon1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}

.jp-icon2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}

.jp-icon3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}

.jp-icon4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/* recolor the accent elements of an icon */
.jp-icon-accent0[fill] {
  fill: var(--jp-layout-color0);
}

.jp-icon-accent1[fill] {
  fill: var(--jp-layout-color1);
}

.jp-icon-accent2[fill] {
  fill: var(--jp-layout-color2);
}

.jp-icon-accent3[fill] {
  fill: var(--jp-layout-color3);
}

.jp-icon-accent4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-accent0[stroke] {
  stroke: var(--jp-layout-color0);
}

.jp-icon-accent1[stroke] {
  stroke: var(--jp-layout-color1);
}

.jp-icon-accent2[stroke] {
  stroke: var(--jp-layout-color2);
}

.jp-icon-accent3[stroke] {
  stroke: var(--jp-layout-color3);
}

.jp-icon-accent4[stroke] {
  stroke: var(--jp-layout-color4);
}

/* set the color of an icon to transparent */
.jp-icon-none[fill] {
  fill: none;
}

.jp-icon-none[stroke] {
  stroke: none;
}

/* brand icon colors. Same for light and dark */
.jp-icon-brand0[fill] {
  fill: var(--jp-brand-color0);
}

.jp-icon-brand1[fill] {
  fill: var(--jp-brand-color1);
}

.jp-icon-brand2[fill] {
  fill: var(--jp-brand-color2);
}

.jp-icon-brand3[fill] {
  fill: var(--jp-brand-color3);
}

.jp-icon-brand4[fill] {
  fill: var(--jp-brand-color4);
}

.jp-icon-brand0[stroke] {
  stroke: var(--jp-brand-color0);
}

.jp-icon-brand1[stroke] {
  stroke: var(--jp-brand-color1);
}

.jp-icon-brand2[stroke] {
  stroke: var(--jp-brand-color2);
}

.jp-icon-brand3[stroke] {
  stroke: var(--jp-brand-color3);
}

.jp-icon-brand4[stroke] {
  stroke: var(--jp-brand-color4);
}

/* warn icon colors. Same for light and dark */
.jp-icon-warn0[fill] {
  fill: var(--jp-warn-color0);
}

.jp-icon-warn1[fill] {
  fill: var(--jp-warn-color1);
}

.jp-icon-warn2[fill] {
  fill: var(--jp-warn-color2);
}

.jp-icon-warn3[fill] {
  fill: var(--jp-warn-color3);
}

.jp-icon-warn0[stroke] {
  stroke: var(--jp-warn-color0);
}

.jp-icon-warn1[stroke] {
  stroke: var(--jp-warn-color1);
}

.jp-icon-warn2[stroke] {
  stroke: var(--jp-warn-color2);
}

.jp-icon-warn3[stroke] {
  stroke: var(--jp-warn-color3);
}

/* icon colors that contrast well with each other and most backgrounds */
.jp-icon-contrast0[fill] {
  fill: var(--jp-icon-contrast-color0);
}

.jp-icon-contrast1[fill] {
  fill: var(--jp-icon-contrast-color1);
}

.jp-icon-contrast2[fill] {
  fill: var(--jp-icon-contrast-color2);
}

.jp-icon-contrast3[fill] {
  fill: var(--jp-icon-contrast-color3);
}

.jp-icon-contrast0[stroke] {
  stroke: var(--jp-icon-contrast-color0);
}

.jp-icon-contrast1[stroke] {
  stroke: var(--jp-icon-contrast-color1);
}

.jp-icon-contrast2[stroke] {
  stroke: var(--jp-icon-contrast-color2);
}

.jp-icon-contrast3[stroke] {
  stroke: var(--jp-icon-contrast-color3);
}

.jp-icon-dot[fill] {
  fill: var(--jp-warn-color0);
}

.jp-jupyter-icon-color[fill] {
  fill: var(--jp-jupyter-icon-color, var(--jp-warn-color0));
}

.jp-notebook-icon-color[fill] {
  fill: var(--jp-notebook-icon-color, var(--jp-warn-color0));
}

.jp-json-icon-color[fill] {
  fill: var(--jp-json-icon-color, var(--jp-warn-color1));
}

.jp-console-icon-color[fill] {
  fill: var(--jp-console-icon-color, white);
}

.jp-console-icon-background-color[fill] {
  fill: var(--jp-console-icon-background-color, var(--jp-brand-color1));
}

.jp-terminal-icon-color[fill] {
  fill: var(--jp-terminal-icon-color, var(--jp-layout-color2));
}

.jp-terminal-icon-background-color[fill] {
  fill: var(
    --jp-terminal-icon-background-color,
    var(--jp-inverse-layout-color2)
  );
}

.jp-text-editor-icon-color[fill] {
  fill: var(--jp-text-editor-icon-color, var(--jp-inverse-layout-color3));
}

.jp-inspector-icon-color[fill] {
  fill: var(--jp-inspector-icon-color, var(--jp-inverse-layout-color3));
}

/* CSS for icons in selected filebrowser listing items */
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}

.jp-DirListing-item.jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* stylelint-disable selector-max-class, selector-max-compound-selectors */

/**
* TODO: come up with non css-hack solution for showing the busy icon on top
*  of the close icon
* CSS for complex behavior of close icon of tabs in the main area tabbar
*/
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}

.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

/* stylelint-enable selector-max-class, selector-max-compound-selectors */

/* CSS for icons in status bar */
#jp-main-statusbar .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}

#jp-main-statusbar .jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* special handling for splash icon CSS. While the theme CSS reloads during
   splash, the splash icon can loose theming. To prevent that, we set a
   default for its color variable */
:root {
  --jp-warn-color0: var(--md-orange-700);
}

/* not sure what to do with this one, used in filebrowser listing */
.jp-DragIcon {
  margin-right: 4px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for alt colors for icons as inline SVG HTMLElements
 */

/* alt recolor the primary elements of an icon */
.jp-icon-alt .jp-icon0[fill] {
  fill: var(--jp-layout-color0);
}

.jp-icon-alt .jp-icon1[fill] {
  fill: var(--jp-layout-color1);
}

.jp-icon-alt .jp-icon2[fill] {
  fill: var(--jp-layout-color2);
}

.jp-icon-alt .jp-icon3[fill] {
  fill: var(--jp-layout-color3);
}

.jp-icon-alt .jp-icon4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-alt .jp-icon0[stroke] {
  stroke: var(--jp-layout-color0);
}

.jp-icon-alt .jp-icon1[stroke] {
  stroke: var(--jp-layout-color1);
}

.jp-icon-alt .jp-icon2[stroke] {
  stroke: var(--jp-layout-color2);
}

.jp-icon-alt .jp-icon3[stroke] {
  stroke: var(--jp-layout-color3);
}

.jp-icon-alt .jp-icon4[stroke] {
  stroke: var(--jp-layout-color4);
}

/* alt recolor the accent elements of an icon */
.jp-icon-alt .jp-icon-accent0[fill] {
  fill: var(--jp-inverse-layout-color0);
}

.jp-icon-alt .jp-icon-accent1[fill] {
  fill: var(--jp-inverse-layout-color1);
}

.jp-icon-alt .jp-icon-accent2[fill] {
  fill: var(--jp-inverse-layout-color2);
}

.jp-icon-alt .jp-icon-accent3[fill] {
  fill: var(--jp-inverse-layout-color3);
}

.jp-icon-alt .jp-icon-accent4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-alt .jp-icon-accent0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}

.jp-icon-alt .jp-icon-accent1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}

.jp-icon-alt .jp-icon-accent2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}

.jp-icon-alt .jp-icon-accent3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}

.jp-icon-alt .jp-icon-accent4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-icon-hoverShow:not(:hover) .jp-icon-hoverShow-content {
  display: none !important;
}

/**
 * Support for hover colors for icons as inline SVG HTMLElements
 */

/**
 * regular colors
 */

/* recolor the primary elements of an icon */
.jp-icon-hover :hover .jp-icon0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}

.jp-icon-hover :hover .jp-icon1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}

.jp-icon-hover :hover .jp-icon2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}

.jp-icon-hover :hover .jp-icon3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}

.jp-icon-hover :hover .jp-icon4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}

.jp-icon-hover :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}

.jp-icon-hover :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}

.jp-icon-hover :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}

.jp-icon-hover :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/* recolor the accent elements of an icon */
.jp-icon-hover :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-layout-color0);
}

.jp-icon-hover :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-layout-color1);
}

.jp-icon-hover :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-layout-color2);
}

.jp-icon-hover :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-layout-color3);
}

.jp-icon-hover :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}

.jp-icon-hover :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}

.jp-icon-hover :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}

.jp-icon-hover :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}

.jp-icon-hover :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* set the color of an icon to transparent */
.jp-icon-hover :hover .jp-icon-none-hover[fill] {
  fill: none;
}

.jp-icon-hover :hover .jp-icon-none-hover[stroke] {
  stroke: none;
}

/**
 * inverse colors
 */

/* inverse recolor the primary elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[fill] {
  fill: var(--jp-layout-color0);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[fill] {
  fill: var(--jp-layout-color1);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[fill] {
  fill: var(--jp-layout-color2);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[fill] {
  fill: var(--jp-layout-color3);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* inverse recolor the accent elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-IFrame {
  width: 100%;
  height: 100%;
}

.jp-IFrame > iframe {
  border: none;
}

/*
When drag events occur, `lm-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-IFrame {
  position: relative;
}

body.lm-mod-override-cursor .jp-IFrame::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-HoverBox {
  position: fixed;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-FormGroup-content fieldset {
  border: none;
  padding: 0;
  min-width: 0;
  width: 100%;
}

/* stylelint-disable selector-max-type */

.jp-FormGroup-content fieldset .jp-inputFieldWrapper input,
.jp-FormGroup-content fieldset .jp-inputFieldWrapper select,
.jp-FormGroup-content fieldset .jp-inputFieldWrapper textarea {
  font-size: var(--jp-content-font-size2);
  border-color: var(--jp-input-border-color);
  border-style: solid;
  border-radius: var(--jp-border-radius);
  border-width: 1px;
  padding: 6px 8px;
  background: none;
  color: var(--jp-ui-font-color0);
  height: inherit;
}

.jp-FormGroup-content fieldset input[type='checkbox'] {
  position: relative;
  top: 2px;
  margin-left: 0;
}

.jp-FormGroup-content button.jp-mod-styled {
  cursor: pointer;
}

.jp-FormGroup-content .checkbox label {
  cursor: pointer;
  font-size: var(--jp-content-font-size1);
}

.jp-FormGroup-content .jp-root > fieldset > legend {
  display: none;
}

.jp-FormGroup-content .jp-root > fieldset > p {
  display: none;
}

/** copy of `input.jp-mod-styled:focus` style */
.jp-FormGroup-content fieldset input:focus,
.jp-FormGroup-content fieldset select:focus {
  -moz-outline-radius: unset;
  outline: var(--jp-border-width) solid var(--md-blue-500);
  outline-offset: -1px;
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-FormGroup-content fieldset input:hover:not(:focus),
.jp-FormGroup-content fieldset select:hover:not(:focus) {
  background-color: var(--jp-border-color2);
}

/* stylelint-enable selector-max-type */

.jp-FormGroup-content .checkbox .field-description {
  /* Disable default description field for checkbox:
   because other widgets do not have description fields,
   we add descriptions to each widget on the field level.
  */
  display: none;
}

.jp-FormGroup-content #root__description {
  display: none;
}

.jp-FormGroup-content .jp-modifiedIndicator {
  width: 5px;
  background-color: var(--jp-brand-color2);
  margin-top: 0;
  margin-left: calc(var(--jp-private-settingeditor-modifier-indent) * -1);
  flex-shrink: 0;
}

.jp-FormGroup-content .jp-modifiedIndicator.jp-errorIndicator {
  background-color: var(--jp-error-color0);
  margin-right: 0.5em;
}

/* RJSF ARRAY style */

.jp-arrayFieldWrapper legend {
  font-size: var(--jp-content-font-size2);
  color: var(--jp-ui-font-color0);
  flex-basis: 100%;
  padding: 4px 0;
  font-weight: var(--jp-content-heading-font-weight);
  border-bottom: 1px solid var(--jp-border-color2);
}

.jp-arrayFieldWrapper .field-description {
  padding: 4px 0;
  white-space: pre-wrap;
}

.jp-arrayFieldWrapper .array-item {
  width: 100%;
  border: 1px solid var(--jp-border-color2);
  border-radius: 4px;
  margin: 4px;
}

.jp-ArrayOperations {
  display: flex;
  margin-left: 8px;
}

.jp-ArrayOperationsButton {
  margin: 2px;
}

.jp-ArrayOperationsButton .jp-icon3[fill] {
  fill: var(--jp-ui-font-color0);
}

button.jp-ArrayOperationsButton.jp-mod-styled:disabled {
  cursor: not-allowed;
  opacity: 0.5;
}

/* RJSF form validation error */

.jp-FormGroup-content .validationErrors {
  color: var(--jp-error-color0);
}

/* Hide panel level error as duplicated the field level error */
.jp-FormGroup-content .panel.errors {
  display: none;
}

/* RJSF normal content (settings-editor) */

.jp-FormGroup-contentNormal {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

.jp-FormGroup-contentNormal .jp-FormGroup-contentItem {
  margin-left: 7px;
  color: var(--jp-ui-font-color0);
}

.jp-FormGroup-contentNormal .jp-FormGroup-description {
  flex-basis: 100%;
  padding: 4px 7px;
}

.jp-FormGroup-contentNormal .jp-FormGroup-default {
  flex-basis: 100%;
  padding: 4px 7px;
}

.jp-FormGroup-contentNormal .jp-FormGroup-fieldLabel {
  font-size: var(--jp-content-font-size1);
  font-weight: normal;
  min-width: 120px;
}

.jp-FormGroup-contentNormal fieldset:not(:first-child) {
  margin-left: 7px;
}

.jp-FormGroup-contentNormal .field-array-of-string .array-item {
  /* Display `jp-ArrayOperations` buttons side-by-side with content except
    for small screens where flex-wrap will place them one below the other.
  */
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

.jp-FormGroup-contentNormal .jp-objectFieldWrapper .form-group {
  padding: 2px 8px 2px var(--jp-private-settingeditor-modifier-indent);
  margin-top: 2px;
}

/* RJSF compact content (metadata-form) */

.jp-FormGroup-content.jp-FormGroup-contentCompact {
  width: 100%;
}

.jp-FormGroup-contentCompact .form-group {
  display: flex;
  padding: 0.5em 0.2em 0.5em 0;
}

.jp-FormGroup-contentCompact
  .jp-FormGroup-compactTitle
  .jp-FormGroup-description {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color2);
}

.jp-FormGroup-contentCompact .jp-FormGroup-fieldLabel {
  padding-bottom: 0.3em;
}

.jp-FormGroup-contentCompact .jp-inputFieldWrapper .form-control {
  width: 100%;
  box-sizing: border-box;
}

.jp-FormGroup-contentCompact .jp-arrayFieldWrapper .jp-FormGroup-compactTitle {
  padding-bottom: 7px;
}

.jp-FormGroup-contentCompact
  .jp-objectFieldWrapper
  .jp-objectFieldWrapper
  .form-group {
  padding: 2px 8px 2px var(--jp-private-settingeditor-modifier-indent);
  margin-top: 2px;
}

.jp-FormGroup-contentCompact ul.error-detail {
  margin-block-start: 0.5em;
  margin-block-end: 0.5em;
  padding-inline-start: 1em;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-SidePanel {
  display: flex;
  flex-direction: column;
  min-width: var(--jp-sidebar-min-width);
  overflow-y: auto;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  font-size: var(--jp-ui-font-size1);
}

.jp-SidePanel-header {
  flex: 0 0 auto;
  display: flex;
  border-bottom: var(--jp-border-width) solid var(--jp-border-color2);
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  letter-spacing: 1px;
  margin: 0;
  padding: 2px;
  text-transform: uppercase;
}

.jp-SidePanel-toolbar {
  flex: 0 0 auto;
}

.jp-SidePanel-content {
  flex: 1 1 auto;
}

.jp-SidePanel-toolbar,
.jp-AccordionPanel-toolbar {
  height: var(--jp-private-toolbar-height);
}

.jp-SidePanel-toolbar.jp-Toolbar-micro {
  display: none;
}

.lm-AccordionPanel .jp-AccordionPanel-title {
  box-sizing: border-box;
  line-height: 25px;
  margin: 0;
  display: flex;
  align-items: center;
  background: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  font-size: var(--jp-ui-font-size0);
}

.jp-AccordionPanel-title {
  cursor: pointer;
  user-select: none;
  -moz-user-select: none;
  -webkit-user-select: none;
  text-transform: uppercase;
}

.lm-AccordionPanel[data-orientation='horizontal'] > .jp-AccordionPanel-title {
  /* Title is rotated for horizontal accordion panel using CSS */
  display: block;
  transform-origin: top left;
  transform: rotate(-90deg) translate(-100%);
}

.jp-AccordionPanel-title .lm-AccordionPanel-titleLabel {
  user-select: none;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}

.jp-AccordionPanel-title .lm-AccordionPanel-titleCollapser {
  transform: rotate(-90deg);
  margin: auto 0;
  height: 16px;
}

.jp-AccordionPanel-title.lm-mod-expanded .lm-AccordionPanel-titleCollapser {
  transform: rotate(0deg);
}

.lm-AccordionPanel .jp-AccordionPanel-toolbar {
  background: none;
  box-shadow: none;
  border: none;
  margin-left: auto;
}

.lm-AccordionPanel .lm-SplitPanel-handle:hover {
  background: var(--jp-layout-color3);
}

.jp-text-truncated {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Spinner {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 10;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-layout-color0);
  outline: none;
}

.jp-SpinnerContent {
  font-size: 10px;
  margin: 50px auto;
  text-indent: -9999em;
  width: 3em;
  height: 3em;
  border-radius: 50%;
  background: var(--jp-brand-color3);
  background: linear-gradient(
    to right,
    #f37626 10%,
    rgba(255, 255, 255, 0) 42%
  );
  position: relative;
  animation: load3 1s infinite linear, fadeIn 1s;
}

.jp-SpinnerContent::before {
  width: 50%;
  height: 50%;
  background: #f37626;
  border-radius: 100% 0 0;
  position: absolute;
  top: 0;
  left: 0;
  content: '';
}

.jp-SpinnerContent::after {
  background: var(--jp-layout-color0);
  width: 75%;
  height: 75%;
  border-radius: 50%;
  content: '';
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}

@keyframes load3 {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

button.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: none;
  box-sizing: border-box;
  text-align: center;
  line-height: 32px;
  height: 32px;
  padding: 0 12px;
  letter-spacing: 0.8px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input.jp-mod-styled {
  background: var(--jp-input-background);
  height: 28px;
  box-sizing: border-box;
  border: var(--jp-border-width) solid var(--jp-border-color1);
  padding-left: 7px;
  padding-right: 7px;
  font-size: var(--jp-ui-font-size2);
  color: var(--jp-ui-font-color0);
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input[type='checkbox'].jp-mod-styled {
  appearance: checkbox;
  -webkit-appearance: checkbox;
  -moz-appearance: checkbox;
  height: auto;
}

input.jp-mod-styled:focus {
  border: var(--jp-border-width) solid var(--md-blue-500);
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-select-wrapper {
  display: flex;
  position: relative;
  flex-direction: column;
  padding: 1px;
  background-color: var(--jp-layout-color1);
  box-sizing: border-box;
  margin-bottom: 12px;
}

.jp-select-wrapper:not(.multiple) {
  height: 28px;
}

.jp-select-wrapper.jp-mod-focused select.jp-mod-styled {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-input-active-background);
}

select.jp-mod-styled:hover {
  cursor: pointer;
  color: var(--jp-ui-font-color0);
  background-color: var(--jp-input-hover-background);
  box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.5);
}

select.jp-mod-styled {
  flex: 1 1 auto;
  width: 100%;
  font-size: var(--jp-ui-font-size2);
  background: var(--jp-input-background);
  color: var(--jp-ui-font-color0);
  padding: 0 25px 0 8px;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

select.jp-mod-styled:not([multiple]) {
  height: 32px;
}

select.jp-mod-styled[multiple] {
  max-height: 200px;
  overflow-y: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-switch {
  display: flex;
  align-items: center;
  padding-left: 4px;
  padding-right: 4px;
  font-size: var(--jp-ui-font-size1);
  background-color: transparent;
  color: var(--jp-ui-font-color1);
  border: none;
  height: 20px;
}

.jp-switch:hover {
  background-color: var(--jp-layout-color2);
}

.jp-switch-label {
  margin-right: 5px;
  font-family: var(--jp-ui-font-family);
}

.jp-switch-track {
  cursor: pointer;
  background-color: var(--jp-switch-color, var(--jp-border-color1));
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
  height: 16px;
  width: 35px;
  position: relative;
}

.jp-switch-track::before {
  content: '';
  position: absolute;
  height: 10px;
  width: 10px;
  margin: 3px;
  left: 0;
  background-color: var(--jp-ui-inverse-font-color1);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

.jp-switch[aria-checked='true'] .jp-switch-track {
  background-color: var(--jp-switch-true-position-color, var(--jp-warn-color0));
}

.jp-switch[aria-checked='true'] .jp-switch-track::before {
  /* track width (35) - margins (3 + 3) - thumb width (10) */
  left: 19px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

:root {
  --jp-private-toolbar-height: calc(
    28px + var(--jp-border-width)
  ); /* leave 28px for content */
}

.jp-Toolbar {
  color: var(--jp-ui-font-color1);
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  background: var(--jp-toolbar-background);
  min-height: var(--jp-toolbar-micro-height);
  padding: 2px;
  z-index: 8;
  overflow-x: hidden;
}

/* Toolbar items */

.jp-Toolbar > .jp-Toolbar-item.jp-Toolbar-spacer {
  flex-grow: 1;
  flex-shrink: 1;
}

.jp-Toolbar-item.jp-Toolbar-kernelStatus {
  display: inline-block;
  width: 32px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 16px;
}

.jp-Toolbar > .jp-Toolbar-item {
  flex: 0 0 auto;
  display: flex;
  padding-left: 1px;
  padding-right: 1px;
  font-size: var(--jp-ui-font-size1);
  line-height: var(--jp-private-toolbar-height);
  height: 100%;
}

/* Toolbar buttons */

/* This is the div we use to wrap the react component into a Widget */
div.jp-ToolbarButton {
  color: transparent;
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0;
  margin: 0;
}

button.jp-ToolbarButtonComponent {
  background: var(--jp-layout-color1);
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0 6px;
  margin: 0;
  height: 24px;
  border-radius: var(--jp-border-radius);
  display: flex;
  align-items: center;
  text-align: center;
  font-size: 14px;
  min-width: unset;
  min-height: unset;
}

button.jp-ToolbarButtonComponent:disabled {
  opacity: 0.4;
}

button.jp-ToolbarButtonComponent > span {
  padding: 0;
  flex: 0 0 auto;
}

button.jp-ToolbarButtonComponent .jp-ToolbarButtonComponent-label {
  font-size: var(--jp-ui-font-size1);
  line-height: 100%;
  padding-left: 2px;
  color: var(--jp-ui-font-color1);
  font-family: var(--jp-ui-font-family);
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar.jp-Toolbar-micro {
  padding: 0;
  min-height: 0;
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar {
  border: none;
  box-shadow: none;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-WindowedPanel-outer {
  position: relative;
  overflow-y: auto;
}

.jp-WindowedPanel-inner {
  position: relative;
}

.jp-WindowedPanel-window {
  position: absolute;
  left: 0;
  right: 0;
  overflow: visible;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* Sibling imports */

body {
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
}

/* Disable native link decoration styles everywhere outside of dialog boxes */
a {
  text-decoration: unset;
  color: unset;
}

a:hover {
  text-decoration: unset;
  color: unset;
}

/* Accessibility for links inside dialog box text */
.jp-Dialog-content a {
  text-decoration: revert;
  color: var(--jp-content-link-color);
}

.jp-Dialog-content a:hover {
  text-decoration: revert;
}

/* Styles for ui-components */
.jp-Button {
  color: var(--jp-ui-font-color2);
  border-radius: var(--jp-border-radius);
  padding: 0 12px;
  font-size: var(--jp-ui-font-size1);

  /* Copy from blueprint 3 */
  display: inline-flex;
  flex-direction: row;
  border: none;
  cursor: pointer;
  align-items: center;
  justify-content: center;
  text-align: left;
  vertical-align: middle;
  min-height: 30px;
  min-width: 30px;
}

.jp-Button:disabled {
  cursor: not-allowed;
}

.jp-Button:empty {
  padding: 0 !important;
}

.jp-Button.jp-mod-small {
  min-height: 24px;
  min-width: 24px;
  font-size: 12px;
  padding: 0 7px;
}

/* Use our own theme for hover styles */
.jp-Button.jp-mod-minimal:hover {
  background-color: var(--jp-layout-color2);
}

.jp-Button.jp-mod-minimal {
  background: none;
}

.jp-InputGroup {
  display: block;
  position: relative;
}

.jp-InputGroup input {
  box-sizing: border-box;
  border: none;
  border-radius: 0;
  background-color: transparent;
  color: var(--jp-ui-font-color0);
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
  padding-bottom: 0;
  padding-top: 0;
  padding-left: 10px;
  padding-right: 28px;
  position: relative;
  width: 100%;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  font-size: 14px;
  font-weight: 400;
  height: 30px;
  line-height: 30px;
  outline: none;
  vertical-align: middle;
}

.jp-InputGroup input:focus {
  box-shadow: inset 0 0 0 var(--jp-border-width)
      var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-InputGroup input:disabled {
  cursor: not-allowed;
  resize: block;
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color2);
}

.jp-InputGroup input:disabled ~ span {
  cursor: not-allowed;
  color: var(--jp-ui-font-color2);
}

.jp-InputGroup input::placeholder,
input::placeholder {
  color: var(--jp-ui-font-color2);
}

.jp-InputGroupAction {
  position: absolute;
  bottom: 1px;
  right: 0;
  padding: 6px;
}

.jp-HTMLSelect.jp-DefaultStyle select {
  background-color: initial;
  border: none;
  border-radius: 0;
  box-shadow: none;
  color: var(--jp-ui-font-color0);
  display: block;
  font-size: var(--jp-ui-font-size1);
  font-family: var(--jp-ui-font-family);
  height: 24px;
  line-height: 14px;
  padding: 0 25px 0 10px;
  text-align: left;
  -moz-appearance: none;
  -webkit-appearance: none;
}

.jp-HTMLSelect.jp-DefaultStyle select:disabled {
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color2);
  cursor: not-allowed;
  resize: block;
}

.jp-HTMLSelect.jp-DefaultStyle select:disabled ~ span {
  cursor: not-allowed;
}

/* Use our own theme for hover and option styles */
/* stylelint-disable-next-line selector-max-type */
.jp-HTMLSelect.jp-DefaultStyle select:hover,
.jp-HTMLSelect.jp-DefaultStyle select > option {
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color0);
}

select {
  box-sizing: border-box;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-StatusBar-Widget {
  display: flex;
  align-items: center;
  background: var(--jp-layout-color2);
  min-height: var(--jp-statusbar-height);
  justify-content: space-between;
  padding: 0 10px;
}

.jp-StatusBar-Left {
  display: flex;
  align-items: center;
  flex-direction: row;
}

.jp-StatusBar-Middle {
  display: flex;
  align-items: center;
}

.jp-StatusBar-Right {
  display: flex;
  align-items: center;
  flex-direction: row-reverse;
}

.jp-StatusBar-Item {
  max-height: var(--jp-statusbar-height);
  margin: 0 2px;
  height: var(--jp-statusbar-height);
  white-space: nowrap;
  text-overflow: ellipsis;
  color: var(--jp-ui-font-color1);
  padding: 0 6px;
}

.jp-mod-highlighted:hover {
  background-color: var(--jp-layout-color3);
}

.jp-mod-clicked {
  background-color: var(--jp-brand-color1);
}

.jp-mod-clicked:hover {
  background-color: var(--jp-brand-color0);
}

.jp-mod-clicked .jp-StatusBar-TextItem {
  color: var(--jp-ui-inverse-font-color1);
}

.jp-StatusBar-HoverItem {
  box-shadow: '0px 4px 4px rgba(0, 0, 0, 0.25)';
}

.jp-StatusBar-TextItem {
  font-size: var(--jp-ui-font-size1);
  font-family: var(--jp-ui-font-family);
  line-height: 24px;
  color: var(--jp-ui-font-color1);
}

.jp-StatusBar-GroupItem {
  display: flex;
  align-items: center;
  flex-direction: row;
}

.jp-Statusbar-ProgressCircle svg {
  display: block;
  margin: 0 auto;
  width: 16px;
  height: 24px;
  align-self: normal;
}

.jp-Statusbar-ProgressCircle path {
  fill: var(--jp-inverse-layout-color3);
}

.jp-Statusbar-ProgressBar-progress-bar {
  height: 10px;
  width: 100px;
  border: solid 0.25px var(--jp-brand-color2);
  border-radius: 3px;
  overflow: hidden;
  align-self: center;
}

.jp-Statusbar-ProgressBar-progress-bar > div {
  background-color: var(--jp-brand-color2);
  background-image: linear-gradient(
    -45deg,
    rgba(255, 255, 255, 0.2) 25%,
    transparent 25%,
    transparent 50%,
    rgba(255, 255, 255, 0.2) 50%,
    rgba(255, 255, 255, 0.2) 75%,
    transparent 75%,
    transparent
  );
  background-size: 40px 40px;
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 14px;
  color: #fff;
  text-align: center;
  animation: jp-Statusbar-ExecutionTime-progress-bar 2s linear infinite;
}

.jp-Statusbar-ProgressBar-progress-bar p {
  color: var(--jp-ui-font-color1);
  font-family: var(--jp-ui-font-family);
  font-size: var(--jp-ui-font-size1);
  line-height: 10px;
  width: 100px;
}

@keyframes jp-Statusbar-ExecutionTime-progress-bar {
  0% {
    background-position: 0 0;
  }

  100% {
    background-position: 40px 40px;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-commandpalette-search-height: 28px;
}

/*-----------------------------------------------------------------------------
| Overall styles
|----------------------------------------------------------------------------*/

.lm-CommandPalette {
  padding-bottom: 0;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);

  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Modal variant
|----------------------------------------------------------------------------*/

.jp-ModalCommandPalette {
  position: absolute;
  z-index: 10000;
  top: 38px;
  left: 30%;
  margin: 0;
  padding: 4px;
  width: 40%;
  box-shadow: var(--jp-elevation-z4);
  border-radius: 4px;
  background: var(--jp-layout-color0);
}

.jp-ModalCommandPalette .lm-CommandPalette {
  max-height: 40vh;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-close-icon::after {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-header {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-item {
  margin-left: 4px;
  margin-right: 4px;
}

.jp-ModalCommandPalette
  .lm-CommandPalette
  .lm-CommandPalette-item.lm-mod-disabled {
  display: none;
}

/*-----------------------------------------------------------------------------
| Search
|----------------------------------------------------------------------------*/

.lm-CommandPalette-search {
  padding: 4px;
  background-color: var(--jp-layout-color1);
  z-index: 2;
}

.lm-CommandPalette-wrapper {
  overflow: overlay;
  padding: 0 9px;
  background-color: var(--jp-input-active-background);
  height: 30px;
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.lm-CommandPalette.lm-mod-focused .lm-CommandPalette-wrapper {
  box-shadow: inset 0 0 0 1px var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-SearchIconGroup {
  color: white;
  background-color: var(--jp-brand-color1);
  position: absolute;
  top: 4px;
  right: 4px;
  padding: 5px 5px 1px;
}

.jp-SearchIconGroup svg {
  height: 20px;
  width: 20px;
}

.jp-SearchIconGroup .jp-icon3[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-input {
  background: transparent;
  width: calc(100% - 18px);
  float: left;
  border: none;
  outline: none;
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  line-height: var(--jp-private-commandpalette-search-height);
}

.lm-CommandPalette-input::-webkit-input-placeholder,
.lm-CommandPalette-input::-moz-placeholder,
.lm-CommandPalette-input:-ms-input-placeholder {
  color: var(--jp-ui-font-color2);
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Results
|----------------------------------------------------------------------------*/

.lm-CommandPalette-header:first-child {
  margin-top: 0;
}

.lm-CommandPalette-header {
  border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
  color: var(--jp-ui-font-color1);
  cursor: pointer;
  display: flex;
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  letter-spacing: 1px;
  margin-top: 8px;
  padding: 8px 0 8px 12px;
  text-transform: uppercase;
}

.lm-CommandPalette-header.lm-mod-active {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-header > mark {
  background-color: transparent;
  font-weight: bold;
  color: var(--jp-ui-font-color1);
}

.lm-CommandPalette-item {
  padding: 4px 12px 4px 4px;
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  font-weight: 400;
  display: flex;
}

.lm-CommandPalette-item.lm-mod-disabled {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item.lm-mod-active {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item.lm-mod-active .lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-inverse-font-color0);
}

.lm-CommandPalette-item.lm-mod-active .jp-icon-selectable[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-item.lm-mod-active:hover:not(.lm-mod-disabled) {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item:hover:not(.lm-mod-active):not(.lm-mod-disabled) {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-itemContent {
  overflow: hidden;
}

.lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.lm-CommandPalette-item.lm-mod-disabled mark {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item .lm-CommandPalette-itemIcon {
  margin: 0 4px 0 0;
  position: relative;
  width: 16px;
  top: 2px;
  flex: 0 0 auto;
}

.lm-CommandPalette-item.lm-mod-disabled .lm-CommandPalette-itemIcon {
  opacity: 0.6;
}

.lm-CommandPalette-item .lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemCaption {
  display: none;
}

.lm-CommandPalette-content {
  background-color: var(--jp-layout-color1);
}

.lm-CommandPalette-content:empty::after {
  content: 'No results';
  margin: auto;
  margin-top: 20px;
  width: 100px;
  display: block;
  font-size: var(--jp-ui-font-size2);
  font-family: var(--jp-ui-font-family);
  font-weight: lighter;
}

.lm-CommandPalette-emptyMessage {
  text-align: center;
  margin-top: 24px;
  line-height: 1.32;
  padding: 0 8px;
  color: var(--jp-content-font-color3);
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Dialog {
  position: absolute;
  z-index: 10000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  top: 0;
  left: 0;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-dialog-background);
}

.jp-Dialog-content {
  display: flex;
  flex-direction: column;
  margin-left: auto;
  margin-right: auto;
  background: var(--jp-layout-color1);
  padding: 24px 24px 12px;
  min-width: 300px;
  min-height: 150px;
  max-width: 1000px;
  max-height: 500px;
  box-sizing: border-box;
  box-shadow: var(--jp-elevation-z20);
  word-wrap: break-word;
  border-radius: var(--jp-border-radius);

  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color1);
  resize: both;
}

.jp-Dialog-content.jp-Dialog-content-small {
  max-width: 500px;
}

.jp-Dialog-button {
  overflow: visible;
}

button.jp-Dialog-button:focus {
  outline: 1px solid var(--jp-brand-color1);
  outline-offset: 4px;
  -moz-outline-radius: 0;
}

button.jp-Dialog-button:focus::-moz-focus-inner {
  border: 0;
}

button.jp-Dialog-button.jp-mod-styled.jp-mod-accept:focus,
button.jp-Dialog-button.jp-mod-styled.jp-mod-warn:focus,
button.jp-Dialog-button.jp-mod-styled.jp-mod-reject:focus {
  outline-offset: 4px;
  -moz-outline-radius: 0;
}

button.jp-Dialog-button.jp-mod-styled.jp-mod-accept:focus {
  outline: 1px solid var(--jp-accept-color-normal, var(--jp-brand-color1));
}

button.jp-Dialog-button.jp-mod-styled.jp-mod-warn:focus {
  outline: 1px solid var(--jp-warn-color-normal, var(--jp-error-color1));
}

button.jp-Dialog-button.jp-mod-styled.jp-mod-reject:focus {
  outline: 1px solid var(--jp-reject-color-normal, var(--md-grey-600));
}

button.jp-Dialog-close-button {
  padding: 0;
  height: 100%;
  min-width: unset;
  min-height: unset;
}

.jp-Dialog-header {
  display: flex;
  justify-content: space-between;
  flex: 0 0 auto;
  padding-bottom: 12px;
  font-size: var(--jp-ui-font-size3);
  font-weight: 400;
  color: var(--jp-ui-font-color1);
}

.jp-Dialog-body {
  display: flex;
  flex-direction: column;
  flex: 1 1 auto;
  font-size: var(--jp-ui-font-size1);
  background: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  overflow: auto;
}

.jp-Dialog-footer {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  align-items: center;
  flex: 0 0 auto;
  margin-left: -12px;
  margin-right: -12px;
  padding: 12px;
}

.jp-Dialog-checkbox {
  padding-right: 5px;
}

.jp-Dialog-checkbox > input:focus-visible {
  outline: 1px solid var(--jp-input-active-border-color);
  outline-offset: 1px;
}

.jp-Dialog-spacer {
  flex: 1 1 auto;
}

.jp-Dialog-title {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.jp-Dialog-body > .jp-select-wrapper {
  width: 100%;
}

.jp-Dialog-body > button {
  padding: 0 16px;
}

.jp-Dialog-body > label {
  line-height: 1.4;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-button.jp-mod-styled:not(:last-child) {
  margin-right: 12px;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-Input-Boolean-Dialog {
  flex-direction: row-reverse;
  align-items: end;
  width: 100%;
}

.jp-Input-Boolean-Dialog > label {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MainAreaWidget > :focus {
  outline: none;
}

.jp-MainAreaWidget .jp-MainAreaWidget-error {
  padding: 6px;
}

.jp-MainAreaWidget .jp-MainAreaWidget-error > pre {
  width: auto;
  padding: 10px;
  background: var(--jp-error-color3);
  border: var(--jp-border-width) solid var(--jp-error-color1);
  border-radius: var(--jp-border-radius);
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  white-space: pre-wrap;
  word-wrap: break-word;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/**
 * google-material-color v1.2.6
 * https://github.com/danlevan/google-material-color
 */
:root {
  --md-red-50: #ffebee;
  --md-red-100: #ffcdd2;
  --md-red-200: #ef9a9a;
  --md-red-300: #e57373;
  --md-red-400: #ef5350;
  --md-red-500: #f44336;
  --md-red-600: #e53935;
  --md-red-700: #d32f2f;
  --md-red-800: #c62828;
  --md-red-900: #b71c1c;
  --md-red-A100: #ff8a80;
  --md-red-A200: #ff5252;
  --md-red-A400: #ff1744;
  --md-red-A700: #d50000;
  --md-pink-50: #fce4ec;
  --md-pink-100: #f8bbd0;
  --md-pink-200: #f48fb1;
  --md-pink-300: #f06292;
  --md-pink-400: #ec407a;
  --md-pink-500: #e91e63;
  --md-pink-600: #d81b60;
  --md-pink-700: #c2185b;
  --md-pink-800: #ad1457;
  --md-pink-900: #880e4f;
  --md-pink-A100: #ff80ab;
  --md-pink-A200: #ff4081;
  --md-pink-A400: #f50057;
  --md-pink-A700: #c51162;
  --md-purple-50: #f3e5f5;
  --md-purple-100: #e1bee7;
  --md-purple-200: #ce93d8;
  --md-purple-300: #ba68c8;
  --md-purple-400: #ab47bc;
  --md-purple-500: #9c27b0;
  --md-purple-600: #8e24aa;
  --md-purple-700: #7b1fa2;
  --md-purple-800: #6a1b9a;
  --md-purple-900: #4a148c;
  --md-purple-A100: #ea80fc;
  --md-purple-A200: #e040fb;
  --md-purple-A400: #d500f9;
  --md-purple-A700: #a0f;
  --md-deep-purple-50: #ede7f6;
  --md-deep-purple-100: #d1c4e9;
  --md-deep-purple-200: #b39ddb;
  --md-deep-purple-300: #9575cd;
  --md-deep-purple-400: #7e57c2;
  --md-deep-purple-500: #673ab7;
  --md-deep-purple-600: #5e35b1;
  --md-deep-purple-700: #512da8;
  --md-deep-purple-800: #4527a0;
  --md-deep-purple-900: #311b92;
  --md-deep-purple-A100: #b388ff;
  --md-deep-purple-A200: #7c4dff;
  --md-deep-purple-A400: #651fff;
  --md-deep-purple-A700: #6200ea;
  --md-indigo-50: #e8eaf6;
  --md-indigo-100: #c5cae9;
  --md-indigo-200: #9fa8da;
  --md-indigo-300: #7986cb;
  --md-indigo-400: #5c6bc0;
  --md-indigo-500: #3f51b5;
  --md-indigo-600: #3949ab;
  --md-indigo-700: #303f9f;
  --md-indigo-800: #283593;
  --md-indigo-900: #1a237e;
  --md-indigo-A100: #8c9eff;
  --md-indigo-A200: #536dfe;
  --md-indigo-A400: #3d5afe;
  --md-indigo-A700: #304ffe;
  --md-blue-50: #e3f2fd;
  --md-blue-100: #bbdefb;
  --md-blue-200: #90caf9;
  --md-blue-300: #64b5f6;
  --md-blue-400: #42a5f5;
  --md-blue-500: #2196f3;
  --md-blue-600: #1e88e5;
  --md-blue-700: #1976d2;
  --md-blue-800: #1565c0;
  --md-blue-900: #0d47a1;
  --md-blue-A100: #82b1ff;
  --md-blue-A200: #448aff;
  --md-blue-A400: #2979ff;
  --md-blue-A700: #2962ff;
  --md-light-blue-50: #e1f5fe;
  --md-light-blue-100: #b3e5fc;
  --md-light-blue-200: #81d4fa;
  --md-light-blue-300: #4fc3f7;
  --md-light-blue-400: #29b6f6;
  --md-light-blue-500: #03a9f4;
  --md-light-blue-600: #039be5;
  --md-light-blue-700: #0288d1;
  --md-light-blue-800: #0277bd;
  --md-light-blue-900: #01579b;
  --md-light-blue-A100: #80d8ff;
  --md-light-blue-A200: #40c4ff;
  --md-light-blue-A400: #00b0ff;
  --md-light-blue-A700: #0091ea;
  --md-cyan-50: #e0f7fa;
  --md-cyan-100: #b2ebf2;
  --md-cyan-200: #80deea;
  --md-cyan-300: #4dd0e1;
  --md-cyan-400: #26c6da;
  --md-cyan-500: #00bcd4;
  --md-cyan-600: #00acc1;
  --md-cyan-700: #0097a7;
  --md-cyan-800: #00838f;
  --md-cyan-900: #006064;
  --md-cyan-A100: #84ffff;
  --md-cyan-A200: #18ffff;
  --md-cyan-A400: #00e5ff;
  --md-cyan-A700: #00b8d4;
  --md-teal-50: #e0f2f1;
  --md-teal-100: #b2dfdb;
  --md-teal-200: #80cbc4;
  --md-teal-300: #4db6ac;
  --md-teal-400: #26a69a;
  --md-teal-500: #009688;
  --md-teal-600: #00897b;
  --md-teal-700: #00796b;
  --md-teal-800: #00695c;
  --md-teal-900: #004d40;
  --md-teal-A100: #a7ffeb;
  --md-teal-A200: #64ffda;
  --md-teal-A400: #1de9b6;
  --md-teal-A700: #00bfa5;
  --md-green-50: #e8f5e9;
  --md-green-100: #c8e6c9;
  --md-green-200: #a5d6a7;
  --md-green-300: #81c784;
  --md-green-400: #66bb6a;
  --md-green-500: #4caf50;
  --md-green-600: #43a047;
  --md-green-700: #388e3c;
  --md-green-800: #2e7d32;
  --md-green-900: #1b5e20;
  --md-green-A100: #b9f6ca;
  --md-green-A200: #69f0ae;
  --md-green-A400: #00e676;
  --md-green-A700: #00c853;
  --md-light-green-50: #f1f8e9;
  --md-light-green-100: #dcedc8;
  --md-light-green-200: #c5e1a5;
  --md-light-green-300: #aed581;
  --md-light-green-400: #9ccc65;
  --md-light-green-500: #8bc34a;
  --md-light-green-600: #7cb342;
  --md-light-green-700: #689f38;
  --md-light-green-800: #558b2f;
  --md-light-green-900: #33691e;
  --md-light-green-A100: #ccff90;
  --md-light-green-A200: #b2ff59;
  --md-light-green-A400: #76ff03;
  --md-light-green-A700: #64dd17;
  --md-lime-50: #f9fbe7;
  --md-lime-100: #f0f4c3;
  --md-lime-200: #e6ee9c;
  --md-lime-300: #dce775;
  --md-lime-400: #d4e157;
  --md-lime-500: #cddc39;
  --md-lime-600: #c0ca33;
  --md-lime-700: #afb42b;
  --md-lime-800: #9e9d24;
  --md-lime-900: #827717;
  --md-lime-A100: #f4ff81;
  --md-lime-A200: #eeff41;
  --md-lime-A400: #c6ff00;
  --md-lime-A700: #aeea00;
  --md-yellow-50: #fffde7;
  --md-yellow-100: #fff9c4;
  --md-yellow-200: #fff59d;
  --md-yellow-300: #fff176;
  --md-yellow-400: #ffee58;
  --md-yellow-500: #ffeb3b;
  --md-yellow-600: #fdd835;
  --md-yellow-700: #fbc02d;
  --md-yellow-800: #f9a825;
  --md-yellow-900: #f57f17;
  --md-yellow-A100: #ffff8d;
  --md-yellow-A200: #ff0;
  --md-yellow-A400: #ffea00;
  --md-yellow-A700: #ffd600;
  --md-amber-50: #fff8e1;
  --md-amber-100: #ffecb3;
  --md-amber-200: #ffe082;
  --md-amber-300: #ffd54f;
  --md-amber-400: #ffca28;
  --md-amber-500: #ffc107;
  --md-amber-600: #ffb300;
  --md-amber-700: #ffa000;
  --md-amber-800: #ff8f00;
  --md-amber-900: #ff6f00;
  --md-amber-A100: #ffe57f;
  --md-amber-A200: #ffd740;
  --md-amber-A400: #ffc400;
  --md-amber-A700: #ffab00;
  --md-orange-50: #fff3e0;
  --md-orange-100: #ffe0b2;
  --md-orange-200: #ffcc80;
  --md-orange-300: #ffb74d;
  --md-orange-400: #ffa726;
  --md-orange-500: #ff9800;
  --md-orange-600: #fb8c00;
  --md-orange-700: #f57c00;
  --md-orange-800: #ef6c00;
  --md-orange-900: #e65100;
  --md-orange-A100: #ffd180;
  --md-orange-A200: #ffab40;
  --md-orange-A400: #ff9100;
  --md-orange-A700: #ff6d00;
  --md-deep-orange-50: #fbe9e7;
  --md-deep-orange-100: #ffccbc;
  --md-deep-orange-200: #ffab91;
  --md-deep-orange-300: #ff8a65;
  --md-deep-orange-400: #ff7043;
  --md-deep-orange-500: #ff5722;
  --md-deep-orange-600: #f4511e;
  --md-deep-orange-700: #e64a19;
  --md-deep-orange-800: #d84315;
  --md-deep-orange-900: #bf360c;
  --md-deep-orange-A100: #ff9e80;
  --md-deep-orange-A200: #ff6e40;
  --md-deep-orange-A400: #ff3d00;
  --md-deep-orange-A700: #dd2c00;
  --md-brown-50: #efebe9;
  --md-brown-100: #d7ccc8;
  --md-brown-200: #bcaaa4;
  --md-brown-300: #a1887f;
  --md-brown-400: #8d6e63;
  --md-brown-500: #795548;
  --md-brown-600: #6d4c41;
  --md-brown-700: #5d4037;
  --md-brown-800: #4e342e;
  --md-brown-900: #3e2723;
  --md-grey-50: #fafafa;
  --md-grey-100: #f5f5f5;
  --md-grey-200: #eee;
  --md-grey-300: #e0e0e0;
  --md-grey-400: #bdbdbd;
  --md-grey-500: #9e9e9e;
  --md-grey-600: #757575;
  --md-grey-700: #616161;
  --md-grey-800: #424242;
  --md-grey-900: #212121;
  --md-blue-grey-50: #eceff1;
  --md-blue-grey-100: #cfd8dc;
  --md-blue-grey-200: #b0bec5;
  --md-blue-grey-300: #90a4ae;
  --md-blue-grey-400: #78909c;
  --md-blue-grey-500: #607d8b;
  --md-blue-grey-600: #546e7a;
  --md-blue-grey-700: #455a64;
  --md-blue-grey-800: #37474f;
  --md-blue-grey-900: #263238;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| RenderedText
|----------------------------------------------------------------------------*/

:root {
  /* This is the padding value to fill the gaps between lines containing spans with background color. */
  --jp-private-code-span-padding: calc(
    (var(--jp-code-line-height) - 1) * var(--jp-code-font-size) / 2
  );
}

.jp-RenderedText {
  text-align: left;
  padding-left: var(--jp-code-padding);
  line-height: var(--jp-code-line-height);
  font-family: var(--jp-code-font-family);
}

.jp-RenderedText pre,
.jp-RenderedJavaScript pre,
.jp-RenderedHTMLCommon pre {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-code-font-size);
  border: none;
  margin: 0;
  padding: 0;
}

.jp-RenderedText pre a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

.jp-RenderedText pre a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}

.jp-RenderedText pre a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* console foregrounds and backgrounds */
.jp-RenderedText pre .ansi-black-fg {
  color: #3e424d;
}

.jp-RenderedText pre .ansi-red-fg {
  color: #e75c58;
}

.jp-RenderedText pre .ansi-green-fg {
  color: #00a250;
}

.jp-RenderedText pre .ansi-yellow-fg {
  color: #ddb62b;
}

.jp-RenderedText pre .ansi-blue-fg {
  color: #208ffb;
}

.jp-RenderedText pre .ansi-magenta-fg {
  color: #d160c4;
}

.jp-RenderedText pre .ansi-cyan-fg {
  color: #60c6c8;
}

.jp-RenderedText pre .ansi-white-fg {
  color: #c5c1b4;
}

.jp-RenderedText pre .ansi-black-bg {
  background-color: #3e424d;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-red-bg {
  background-color: #e75c58;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-green-bg {
  background-color: #00a250;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-yellow-bg {
  background-color: #ddb62b;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-blue-bg {
  background-color: #208ffb;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-magenta-bg {
  background-color: #d160c4;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-cyan-bg {
  background-color: #60c6c8;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-white-bg {
  background-color: #c5c1b4;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-black-intense-fg {
  color: #282c36;
}

.jp-RenderedText pre .ansi-red-intense-fg {
  color: #b22b31;
}

.jp-RenderedText pre .ansi-green-intense-fg {
  color: #007427;
}

.jp-RenderedText pre .ansi-yellow-intense-fg {
  color: #b27d12;
}

.jp-RenderedText pre .ansi-blue-intense-fg {
  color: #0065ca;
}

.jp-RenderedText pre .ansi-magenta-intense-fg {
  color: #a03196;
}

.jp-RenderedText pre .ansi-cyan-intense-fg {
  color: #258f8f;
}

.jp-RenderedText pre .ansi-white-intense-fg {
  color: #a1a6b2;
}

.jp-RenderedText pre .ansi-black-intense-bg {
  background-color: #282c36;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-red-intense-bg {
  background-color: #b22b31;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-green-intense-bg {
  background-color: #007427;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-yellow-intense-bg {
  background-color: #b27d12;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-blue-intense-bg {
  background-color: #0065ca;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-magenta-intense-bg {
  background-color: #a03196;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-cyan-intense-bg {
  background-color: #258f8f;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-white-intense-bg {
  background-color: #a1a6b2;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-default-inverse-fg {
  color: var(--jp-ui-inverse-font-color0);
}

.jp-RenderedText pre .ansi-default-inverse-bg {
  background-color: var(--jp-inverse-layout-color0);
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-bold {
  font-weight: bold;
}

.jp-RenderedText pre .ansi-underline {
  text-decoration: underline;
}

.jp-RenderedText[data-mime-type='application/vnd.jupyter.stderr'] {
  background: var(--jp-rendermime-error-background);
  padding-top: var(--jp-code-padding);
}

/*-----------------------------------------------------------------------------
| RenderedLatex
|----------------------------------------------------------------------------*/

.jp-RenderedLatex {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
}

/* Left-justify outputs.*/
.jp-OutputArea-output.jp-RenderedLatex {
  padding: var(--jp-code-padding);
  text-align: left;
}

/*-----------------------------------------------------------------------------
| RenderedHTML
|----------------------------------------------------------------------------*/

.jp-RenderedHTMLCommon {
  color: var(--jp-content-font-color1);
  font-family: var(--jp-content-font-family);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);

  /* Give a bit more R padding on Markdown text to keep line lengths reasonable */
  padding-right: 20px;
}

.jp-RenderedHTMLCommon em {
  font-style: italic;
}

.jp-RenderedHTMLCommon strong {
  font-weight: bold;
}

.jp-RenderedHTMLCommon u {
  text-decoration: underline;
}

.jp-RenderedHTMLCommon a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* Headings */

.jp-RenderedHTMLCommon h1,
.jp-RenderedHTMLCommon h2,
.jp-RenderedHTMLCommon h3,
.jp-RenderedHTMLCommon h4,
.jp-RenderedHTMLCommon h5,
.jp-RenderedHTMLCommon h6 {
  line-height: var(--jp-content-heading-line-height);
  font-weight: var(--jp-content-heading-font-weight);
  font-style: normal;
  margin: var(--jp-content-heading-margin-top) 0
    var(--jp-content-heading-margin-bottom) 0;
}

.jp-RenderedHTMLCommon h1:first-child,
.jp-RenderedHTMLCommon h2:first-child,
.jp-RenderedHTMLCommon h3:first-child,
.jp-RenderedHTMLCommon h4:first-child,
.jp-RenderedHTMLCommon h5:first-child,
.jp-RenderedHTMLCommon h6:first-child {
  margin-top: calc(0.5 * var(--jp-content-heading-margin-top));
}

.jp-RenderedHTMLCommon h1:last-child,
.jp-RenderedHTMLCommon h2:last-child,
.jp-RenderedHTMLCommon h3:last-child,
.jp-RenderedHTMLCommon h4:last-child,
.jp-RenderedHTMLCommon h5:last-child,
.jp-RenderedHTMLCommon h6:last-child {
  margin-bottom: calc(0.5 * var(--jp-content-heading-margin-bottom));
}

.jp-RenderedHTMLCommon h1 {
  font-size: var(--jp-content-font-size5);
}

.jp-RenderedHTMLCommon h2 {
  font-size: var(--jp-content-font-size4);
}

.jp-RenderedHTMLCommon h3 {
  font-size: var(--jp-content-font-size3);
}

.jp-RenderedHTMLCommon h4 {
  font-size: var(--jp-content-font-size2);
}

.jp-RenderedHTMLCommon h5 {
  font-size: var(--jp-content-font-size1);
}

.jp-RenderedHTMLCommon h6 {
  font-size: var(--jp-content-font-size0);
}

/* Lists */

/* stylelint-disable selector-max-type, selector-max-compound-selectors */

.jp-RenderedHTMLCommon ul:not(.list-inline),
.jp-RenderedHTMLCommon ol:not(.list-inline) {
  padding-left: 2em;
}

.jp-RenderedHTMLCommon ul {
  list-style: disc;
}

.jp-RenderedHTMLCommon ul ul {
  list-style: square;
}

.jp-RenderedHTMLCommon ul ul ul {
  list-style: circle;
}

.jp-RenderedHTMLCommon ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol ol {
  list-style: upper-alpha;
}

.jp-RenderedHTMLCommon ol ol ol {
  list-style: lower-alpha;
}

.jp-RenderedHTMLCommon ol ol ol ol {
  list-style: lower-roman;
}

.jp-RenderedHTMLCommon ol ol ol ol ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol,
.jp-RenderedHTMLCommon ul {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon ul ul,
.jp-RenderedHTMLCommon ul ol,
.jp-RenderedHTMLCommon ol ul,
.jp-RenderedHTMLCommon ol ol {
  margin-bottom: 0;
}

/* stylelint-enable selector-max-type, selector-max-compound-selectors */

.jp-RenderedHTMLCommon hr {
  color: var(--jp-border-color2);
  background-color: var(--jp-border-color1);
  margin-top: 1em;
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon > pre {
  margin: 1.5em 2em;
}

.jp-RenderedHTMLCommon pre,
.jp-RenderedHTMLCommon code {
  border: 0;
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  line-height: var(--jp-code-line-height);
  padding: 0;
  white-space: pre-wrap;
}

.jp-RenderedHTMLCommon :not(pre) > code {
  background-color: var(--jp-layout-color2);
  padding: 1px 5px;
}

/* Tables */

.jp-RenderedHTMLCommon table {
  border-collapse: collapse;
  border-spacing: 0;
  border: none;
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  table-layout: fixed;
  margin-left: auto;
  margin-bottom: 1em;
  margin-right: auto;
}

.jp-RenderedHTMLCommon thead {
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  vertical-align: bottom;
}

.jp-RenderedHTMLCommon td,
.jp-RenderedHTMLCommon th,
.jp-RenderedHTMLCommon tr {
  vertical-align: middle;
  padding: 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}

.jp-RenderedMarkdown.jp-RenderedHTMLCommon td,
.jp-RenderedMarkdown.jp-RenderedHTMLCommon th {
  max-width: none;
}

:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon td,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon th,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon tr {
  text-align: right;
}

.jp-RenderedHTMLCommon th {
  font-weight: bold;
}

.jp-RenderedHTMLCommon tbody tr:nth-child(odd) {
  background: var(--jp-layout-color0);
}

.jp-RenderedHTMLCommon tbody tr:nth-child(even) {
  background: var(--jp-rendermime-table-row-background);
}

.jp-RenderedHTMLCommon tbody tr:hover {
  background: var(--jp-rendermime-table-row-hover-background);
}

.jp-RenderedHTMLCommon p {
  text-align: left;
  margin: 0;
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon img {
  -moz-force-broken-image-icon: 1;
}

/* Restrict to direct children as other images could be nested in other content. */
.jp-RenderedHTMLCommon > img {
  display: block;
  margin-left: 0;
  margin-right: 0;
  margin-bottom: 1em;
}

/* Change color behind transparent images if they need it... */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-light-background {
  background-color: var(--jp-inverse-layout-color1);
}

[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-dark-background {
  background-color: var(--jp-inverse-layout-color1);
}

.jp-RenderedHTMLCommon img,
.jp-RenderedImage img,
.jp-RenderedHTMLCommon svg,
.jp-RenderedSVG svg {
  max-width: 100%;
  height: auto;
}

.jp-RenderedHTMLCommon img.jp-mod-unconfined,
.jp-RenderedImage img.jp-mod-unconfined,
.jp-RenderedHTMLCommon svg.jp-mod-unconfined,
.jp-RenderedSVG svg.jp-mod-unconfined {
  max-width: none;
}

.jp-RenderedHTMLCommon .alert {
  padding: var(--jp-notebook-padding);
  border: var(--jp-border-width) solid transparent;
  border-radius: var(--jp-border-radius);
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon .alert-info {
  color: var(--jp-info-color0);
  background-color: var(--jp-info-color3);
  border-color: var(--jp-info-color2);
}

.jp-RenderedHTMLCommon .alert-info hr {
  border-color: var(--jp-info-color3);
}

.jp-RenderedHTMLCommon .alert-info > p:last-child,
.jp-RenderedHTMLCommon .alert-info > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-warning {
  color: var(--jp-warn-color0);
  background-color: var(--jp-warn-color3);
  border-color: var(--jp-warn-color2);
}

.jp-RenderedHTMLCommon .alert-warning hr {
  border-color: var(--jp-warn-color3);
}

.jp-RenderedHTMLCommon .alert-warning > p:last-child,
.jp-RenderedHTMLCommon .alert-warning > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-success {
  color: var(--jp-success-color0);
  background-color: var(--jp-success-color3);
  border-color: var(--jp-success-color2);
}

.jp-RenderedHTMLCommon .alert-success hr {
  border-color: var(--jp-success-color3);
}

.jp-RenderedHTMLCommon .alert-success > p:last-child,
.jp-RenderedHTMLCommon .alert-success > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-danger {
  color: var(--jp-error-color0);
  background-color: var(--jp-error-color3);
  border-color: var(--jp-error-color2);
}

.jp-RenderedHTMLCommon .alert-danger hr {
  border-color: var(--jp-error-color3);
}

.jp-RenderedHTMLCommon .alert-danger > p:last-child,
.jp-RenderedHTMLCommon .alert-danger > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon blockquote {
  margin: 1em 2em;
  padding: 0 1em;
  border-left: 5px solid var(--jp-border-color2);
}

a.jp-InternalAnchorLink {
  visibility: hidden;
  margin-left: 8px;
  color: var(--md-blue-800);
}

h1:hover .jp-InternalAnchorLink,
h2:hover .jp-InternalAnchorLink,
h3:hover .jp-InternalAnchorLink,
h4:hover .jp-InternalAnchorLink,
h5:hover .jp-InternalAnchorLink,
h6:hover .jp-InternalAnchorLink {
  visibility: visible;
}

.jp-RenderedHTMLCommon kbd {
  background-color: var(--jp-rendermime-table-row-background);
  border: 1px solid var(--jp-border-color0);
  border-bottom-color: var(--jp-border-color2);
  border-radius: 3px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
  display: inline-block;
  font-size: var(--jp-ui-font-size0);
  line-height: 1em;
  padding: 0.2em 0.5em;
}

/* Most direct children of .jp-RenderedHTMLCommon have a margin-bottom of 1.0.
 * At the bottom of cells this is a bit too much as there is also spacing
 * between cells. Going all the way to 0 gets too tight between markdown and
 * code cells.
 */
.jp-RenderedHTMLCommon > *:last-child {
  margin-bottom: 0.5em;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-cursor-backdrop {
  position: fixed;
  width: 200px;
  height: 200px;
  margin-top: -100px;
  margin-left: -100px;
  will-change: transform;
  z-index: 100;
}

.lm-mod-drag-image {
  will-change: transform;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-lineFormSearch {
  padding: 4px 12px;
  background-color: var(--jp-layout-color2);
  box-shadow: var(--jp-toolbar-box-shadow);
  z-index: 2;
  font-size: var(--jp-ui-font-size1);
}

.jp-lineFormCaption {
  font-size: var(--jp-ui-font-size0);
  line-height: var(--jp-ui-font-size1);
  margin-top: 4px;
  color: var(--jp-ui-font-color0);
}

.jp-baseLineForm {
  border: none;
  border-radius: 0;
  position: absolute;
  background-size: 16px;
  background-repeat: no-repeat;
  background-position: center;
  outline: none;
}

.jp-lineFormButtonContainer {
  top: 4px;
  right: 8px;
  height: 24px;
  padding: 0 12px;
  width: 12px;
}

.jp-lineFormButtonIcon {
  top: 0;
  right: 0;
  background-color: var(--jp-brand-color1);
  height: 100%;
  width: 100%;
  box-sizing: border-box;
  padding: 4px 6px;
}

.jp-lineFormButton {
  top: 0;
  right: 0;
  background-color: transparent;
  height: 100%;
  width: 100%;
  box-sizing: border-box;
}

.jp-lineFormWrapper {
  overflow: hidden;
  padding: 0 8px;
  border: 1px solid var(--jp-border-color0);
  background-color: var(--jp-input-active-background);
  height: 22px;
}

.jp-lineFormWrapperFocusWithin {
  border: var(--jp-border-width) solid var(--md-blue-500);
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-lineFormInput {
  background: transparent;
  width: 200px;
  height: 100%;
  border: none;
  outline: none;
  color: var(--jp-ui-font-color0);
  line-height: 28px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-JSONEditor {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.jp-JSONEditor-host {
  flex: 1 1 auto;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0;
  background: var(--jp-layout-color0);
  min-height: 50px;
  padding: 1px;
}

.jp-JSONEditor.jp-mod-error .jp-JSONEditor-host {
  border-color: red;
  outline-color: red;
}

.jp-JSONEditor-header {
  display: flex;
  flex: 1 0 auto;
  padding: 0 0 0 12px;
}

.jp-JSONEditor-header label {
  flex: 0 0 auto;
}

.jp-JSONEditor-commitButton {
  height: 16px;
  width: 16px;
  background-size: 18px;
  background-repeat: no-repeat;
  background-position: center;
}

.jp-JSONEditor-host.jp-mod-focused {
  background-color: var(--jp-input-active-background);
  border: 1px solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

.jp-Editor.jp-mod-dropTarget {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/
.jp-DocumentSearch-input {
  border: none;
  outline: none;
  color: var(--jp-ui-font-color0);
  font-size: var(--jp-ui-font-size1);
  background-color: var(--jp-layout-color0);
  font-family: var(--jp-ui-font-family);
  padding: 2px 1px;
  resize: none;
}

.jp-DocumentSearch-overlay {
  position: absolute;
  background-color: var(--jp-toolbar-background);
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  border-left: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  top: 0;
  right: 0;
  z-index: 7;
  min-width: 405px;
  padding: 2px;
  font-size: var(--jp-ui-font-size1);

  --jp-private-document-search-button-height: 20px;
}

.jp-DocumentSearch-overlay button {
  background-color: var(--jp-toolbar-background);
  outline: 0;
}

.jp-DocumentSearch-overlay button:hover {
  background-color: var(--jp-layout-color2);
}

.jp-DocumentSearch-overlay button:active {
  background-color: var(--jp-layout-color3);
}

.jp-DocumentSearch-overlay-row {
  display: flex;
  align-items: center;
  margin-bottom: 2px;
}

.jp-DocumentSearch-button-content {
  display: inline-block;
  cursor: pointer;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
}

.jp-DocumentSearch-button-content svg {
  width: 100%;
  height: 100%;
}

.jp-DocumentSearch-input-wrapper {
  border: var(--jp-border-width) solid var(--jp-border-color0);
  display: flex;
  background-color: var(--jp-layout-color0);
  margin: 2px;
}

.jp-DocumentSearch-input-wrapper:focus-within {
  border-color: var(--jp-cell-editor-active-border-color);
}

.jp-DocumentSearch-toggle-wrapper,
.jp-DocumentSearch-button-wrapper {
  all: initial;
  overflow: hidden;
  display: inline-block;
  border: none;
  box-sizing: border-box;
}

.jp-DocumentSearch-toggle-wrapper {
  width: 14px;
  height: 14px;
}

.jp-DocumentSearch-button-wrapper {
  width: var(--jp-private-document-search-button-height);
  height: var(--jp-private-document-search-button-height);
}

.jp-DocumentSearch-toggle-wrapper:focus,
.jp-DocumentSearch-button-wrapper:focus {
  outline: var(--jp-border-width) solid
    var(--jp-cell-editor-active-border-color);
  outline-offset: -1px;
}

.jp-DocumentSearch-toggle-wrapper,
.jp-DocumentSearch-button-wrapper,
.jp-DocumentSearch-button-content:focus {
  outline: none;
}

.jp-DocumentSearch-toggle-placeholder {
  width: 5px;
}

.jp-DocumentSearch-input-button::before {
  display: block;
  padding-top: 100%;
}

.jp-DocumentSearch-input-button-off {
  opacity: var(--jp-search-toggle-off-opacity);
}

.jp-DocumentSearch-input-button-off:hover {
  opacity: var(--jp-search-toggle-hover-opacity);
}

.jp-DocumentSearch-input-button-on {
  opacity: var(--jp-search-toggle-on-opacity);
}

.jp-DocumentSearch-index-counter {
  padding-left: 10px;
  padding-right: 10px;
  user-select: none;
  min-width: 35px;
  display: inline-block;
}

.jp-DocumentSearch-up-down-wrapper {
  display: inline-block;
  padding-right: 2px;
  margin-left: auto;
  white-space: nowrap;
}

.jp-DocumentSearch-spacer {
  margin-left: auto;
}

.jp-DocumentSearch-up-down-wrapper button {
  outline: 0;
  border: none;
  width: var(--jp-private-document-search-button-height);
  height: var(--jp-private-document-search-button-height);
  vertical-align: middle;
  margin: 1px 5px 2px;
}

.jp-DocumentSearch-up-down-button:hover {
  background-color: var(--jp-layout-color2);
}

.jp-DocumentSearch-up-down-button:active {
  background-color: var(--jp-layout-color3);
}

.jp-DocumentSearch-filter-button {
  border-radius: var(--jp-border-radius);
}

.jp-DocumentSearch-filter-button:hover {
  background-color: var(--jp-layout-color2);
}

.jp-DocumentSearch-filter-button-enabled {
  background-color: var(--jp-layout-color2);
}

.jp-DocumentSearch-filter-button-enabled:hover {
  background-color: var(--jp-layout-color3);
}

.jp-DocumentSearch-search-options {
  padding: 0 8px;
  margin-left: 3px;
  width: 100%;
  display: grid;
  justify-content: start;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  justify-items: stretch;
}

.jp-DocumentSearch-search-filter-disabled {
  color: var(--jp-ui-font-color2);
}

.jp-DocumentSearch-search-filter {
  display: flex;
  align-items: center;
  user-select: none;
}

.jp-DocumentSearch-regex-error {
  color: var(--jp-error-color0);
}

.jp-DocumentSearch-replace-button-wrapper {
  overflow: hidden;
  display: inline-block;
  box-sizing: border-box;
  border: var(--jp-border-width) solid var(--jp-border-color0);
  margin: auto 2px;
  padding: 1px 4px;
  height: calc(var(--jp-private-document-search-button-height) + 2px);
}

.jp-DocumentSearch-replace-button-wrapper:focus {
  border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
}

.jp-DocumentSearch-replace-button {
  display: inline-block;
  text-align: center;
  cursor: pointer;
  box-sizing: border-box;
  color: var(--jp-ui-font-color1);

  /* height - 2 * (padding of wrapper) */
  line-height: calc(var(--jp-private-document-search-button-height) - 2px);
  width: 100%;
  height: 100%;
}

.jp-DocumentSearch-replace-button:focus {
  outline: none;
}

.jp-DocumentSearch-replace-wrapper-class {
  margin-left: 14px;
  display: flex;
}

.jp-DocumentSearch-replace-toggle {
  border: none;
  background-color: var(--jp-toolbar-background);
  border-radius: var(--jp-border-radius);
}

.jp-DocumentSearch-replace-toggle:hover {
  background-color: var(--jp-layout-color2);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.cm-editor {
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  border: 0;
  border-radius: 0;
  height: auto;

  /* Changed to auto to autogrow */
}

.cm-editor pre {
  padding: 0 var(--jp-code-padding);
}

.jp-CodeMirrorEditor[data-type='inline'] .cm-dialog {
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

.jp-CodeMirrorEditor {
  cursor: text;
}

/* When zoomed out 67% and 33% on a screen of 1440 width x 900 height */
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .jp-CodeMirrorEditor[data-type='inline'] .cm-cursor {
    border-left: var(--jp-code-cursor-width1) solid
      var(--jp-editor-cursor-color);
  }
}

/* When zoomed out less than 33% */
@media screen and (min-width: 4320px) {
  .jp-CodeMirrorEditor[data-type='inline'] .cm-cursor {
    border-left: var(--jp-code-cursor-width2) solid
      var(--jp-editor-cursor-color);
  }
}

.cm-editor.jp-mod-readOnly .cm-cursor {
  display: none;
}

.jp-CollaboratorCursor {
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: none;
  border-bottom: 3px solid;
  background-clip: content-box;
  margin-left: -5px;
  margin-right: -5px;
}

.cm-searching,
.cm-searching span {
  /* `.cm-searching span`: we need to override syntax highlighting */
  background-color: var(--jp-search-unselected-match-background-color);
  color: var(--jp-search-unselected-match-color);
}

.cm-searching::selection,
.cm-searching span::selection {
  background-color: var(--jp-search-unselected-match-background-color);
  color: var(--jp-search-unselected-match-color);
}

.jp-current-match > .cm-searching,
.jp-current-match > .cm-searching span,
.cm-searching > .jp-current-match,
.cm-searching > .jp-current-match span {
  background-color: var(--jp-search-selected-match-background-color);
  color: var(--jp-search-selected-match-color);
}

.jp-current-match > .cm-searching::selection,
.cm-searching > .jp-current-match::selection,
.jp-current-match > .cm-searching span::selection {
  background-color: var(--jp-search-selected-match-background-color);
  color: var(--jp-search-selected-match-color);
}

.cm-trailingspace {
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAFCAYAAAB4ka1VAAAAsElEQVQIHQGlAFr/AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA7+r3zKmT0/+pk9P/7+r3zAAAAAAAAAAABAAAAAAAAAAA6OPzM+/q9wAAAAAA6OPzMwAAAAAAAAAAAgAAAAAAAAAAGR8NiRQaCgAZIA0AGR8NiQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQyoYJ/SY80UAAAAASUVORK5CYII=);
  background-position: center left;
  background-repeat: repeat-x;
}

.jp-CollaboratorCursor-hover {
  position: absolute;
  z-index: 1;
  transform: translateX(-50%);
  color: white;
  border-radius: 3px;
  padding-left: 4px;
  padding-right: 4px;
  padding-top: 1px;
  padding-bottom: 1px;
  text-align: center;
  font-size: var(--jp-ui-font-size1);
  white-space: nowrap;
}

.jp-CodeMirror-ruler {
  border-left: 1px dashed var(--jp-border-color2);
}

/* Styles for shared cursors (remote cursor locations and selected ranges) */
.jp-CodeMirrorEditor .cm-ySelectionCaret {
  position: relative;
  border-left: 1px solid black;
  margin-left: -1px;
  margin-right: -1px;
  box-sizing: border-box;
}

.jp-CodeMirrorEditor .cm-ySelectionCaret > .cm-ySelectionInfo {
  white-space: nowrap;
  position: absolute;
  top: -1.15em;
  padding-bottom: 0.05em;
  left: -1px;
  font-size: 0.95em;
  font-family: var(--jp-ui-font-family);
  font-weight: bold;
  line-height: normal;
  user-select: none;
  color: white;
  padding-left: 2px;
  padding-right: 2px;
  z-index: 101;
  transition: opacity 0.3s ease-in-out;
}

.jp-CodeMirrorEditor .cm-ySelectionInfo {
  transition-delay: 0.7s;
  opacity: 0;
}

.jp-CodeMirrorEditor .cm-ySelectionCaret:hover > .cm-ySelectionInfo {
  opacity: 1;
  transition-delay: 0s;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MimeDocument {
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-filebrowser-button-height: 28px;
  --jp-private-filebrowser-button-width: 48px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-FileBrowser .jp-SidePanel-content {
  display: flex;
  flex-direction: column;
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  flex-wrap: wrap;
  row-gap: 12px;
  border-bottom: none;
  height: auto;
  margin: 8px 12px 0;
  box-shadow: none;
  padding: 0;
  justify-content: flex-start;
}

.jp-FileBrowser-Panel {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
}

.jp-BreadCrumbs {
  flex: 0 0 auto;
  margin: 8px 12px;
}

.jp-BreadCrumbs-item {
  margin: 0 2px;
  padding: 0 2px;
  border-radius: var(--jp-border-radius);
  cursor: pointer;
}

.jp-BreadCrumbs-item:hover {
  background-color: var(--jp-layout-color2);
}

.jp-BreadCrumbs-item:first-child {
  margin-left: 0;
}

.jp-BreadCrumbs-item.jp-mod-dropTarget {
  background-color: var(--jp-brand-color2);
  opacity: 0.7;
}

/*-----------------------------------------------------------------------------
| Buttons
|----------------------------------------------------------------------------*/

.jp-FileBrowser-toolbar > .jp-Toolbar-item {
  flex: 0 0 auto;
  padding-left: 0;
  padding-right: 2px;
  align-items: center;
  height: unset;
}

.jp-FileBrowser-toolbar > .jp-Toolbar-item .jp-ToolbarButtonComponent {
  width: 40px;
}

/*-----------------------------------------------------------------------------
| Other styles
|----------------------------------------------------------------------------*/

.jp-FileDialog.jp-mod-conflict input {
  color: var(--jp-error-color1);
}

.jp-FileDialog .jp-new-name-title {
  margin-top: 12px;
}

.jp-LastModified-hidden {
  display: none;
}

.jp-FileSize-hidden {
  display: none;
}

.jp-FileBrowser .lm-AccordionPanel > h3:first-child {
  display: none;
}

/*-----------------------------------------------------------------------------
| DirListing
|----------------------------------------------------------------------------*/

.jp-DirListing {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
  outline: 0;
}

.jp-DirListing-header {
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  align-items: center;
  overflow: hidden;
  border-top: var(--jp-border-width) solid var(--jp-border-color2);
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  box-shadow: var(--jp-toolbar-box-shadow);
  z-index: 2;
}

.jp-DirListing-headerItem {
  padding: 4px 12px 2px;
  font-weight: 500;
}

.jp-DirListing-headerItem:hover {
  background: var(--jp-layout-color2);
}

.jp-DirListing-headerItem.jp-id-name {
  flex: 1 0 84px;
}

.jp-DirListing-headerItem.jp-id-modified {
  flex: 0 0 112px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
}

.jp-DirListing-headerItem.jp-id-filesize {
  flex: 0 0 75px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
}

.jp-id-narrow {
  display: none;
  flex: 0 0 5px;
  padding: 4px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
  color: var(--jp-border-color2);
}

.jp-DirListing-narrow .jp-id-narrow {
  display: block;
}

.jp-DirListing-narrow .jp-id-modified,
.jp-DirListing-narrow .jp-DirListing-itemModified {
  display: none;
}

.jp-DirListing-headerItem.jp-mod-selected {
  font-weight: 600;
}

/* increase specificity to override bundled default */
.jp-DirListing-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

.jp-DirListing-content mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.jp-DirListing-content .jp-DirListing-item.jp-mod-selected mark {
  color: var(--jp-ui-inverse-font-color0);
}

/* Style the directory listing content when a user drops a file to upload */
.jp-DirListing.jp-mod-native-drop .jp-DirListing-content {
  outline: 5px dashed rgba(128, 128, 128, 0.5);
  outline-offset: -10px;
  cursor: copy;
}

.jp-DirListing-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 4px 12px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-DirListing-checkboxWrapper {
  /* Increases hit area of checkbox. */
  padding: 4px;
}

.jp-DirListing-header
  .jp-DirListing-checkboxWrapper
  + .jp-DirListing-headerItem {
  padding-left: 4px;
}

.jp-DirListing-content .jp-DirListing-checkboxWrapper {
  position: relative;
  left: -4px;
  margin: -4px 0 -4px -8px;
}

.jp-DirListing-checkboxWrapper.jp-mod-visible {
  visibility: visible;
}

/* For devices that support hovering, hide checkboxes until hovered, selected...
*/
@media (hover: hover) {
  .jp-DirListing-checkboxWrapper {
    visibility: hidden;
  }

  .jp-DirListing-item:hover .jp-DirListing-checkboxWrapper,
  .jp-DirListing-item.jp-mod-selected .jp-DirListing-checkboxWrapper {
    visibility: visible;
  }
}

.jp-DirListing-item[data-is-dot] {
  opacity: 75%;
}

.jp-DirListing-item.jp-mod-selected {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.jp-DirListing-item.jp-mod-dropTarget {
  background: var(--jp-brand-color3);
}

.jp-DirListing-item:hover:not(.jp-mod-selected) {
  background: var(--jp-layout-color2);
}

.jp-DirListing-itemIcon {
  flex: 0 0 20px;
  margin-right: 4px;
}

.jp-DirListing-itemText {
  flex: 1 0 64px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  user-select: none;
}

.jp-DirListing-itemText:focus {
  outline-width: 2px;
  outline-color: var(--jp-inverse-layout-color1);
  outline-style: solid;
  outline-offset: 1px;
}

.jp-DirListing-item.jp-mod-selected .jp-DirListing-itemText:focus {
  outline-color: var(--jp-layout-color1);
}

.jp-DirListing-itemModified {
  flex: 0 0 125px;
  text-align: right;
}

.jp-DirListing-itemFileSize {
  flex: 0 0 90px;
  text-align: right;
}

.jp-DirListing-editor {
  flex: 1 0 64px;
  outline: none;
  border: none;
  color: var(--jp-ui-font-color1);
  background-color: var(--jp-layout-color1);
}

.jp-DirListing-item.jp-mod-running .jp-DirListing-itemIcon::before {
  color: var(--jp-success-color1);
  content: '\25CF';
  font-size: 8px;
  position: absolute;
  left: -8px;
}

.jp-DirListing-item.jp-mod-running.jp-mod-selected
  .jp-DirListing-itemIcon::before {
  color: var(--jp-ui-inverse-font-color1);
}

.jp-DirListing-item.lm-mod-drag-image,
.jp-DirListing-item.jp-mod-selected.lm-mod-drag-image {
  font-size: var(--jp-ui-font-size1);
  padding-left: 4px;
  margin-left: 4px;
  width: 160px;
  background-color: var(--jp-ui-inverse-font-color2);
  box-shadow: var(--jp-elevation-z2);
  border-radius: 0;
  color: var(--jp-ui-font-color1);
  transform: translateX(-40%) translateY(-58%);
}

.jp-Document {
  min-width: 120px;
  min-height: 120px;
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Main OutputArea
| OutputArea has a list of Outputs
|----------------------------------------------------------------------------*/

.jp-OutputArea {
  overflow-y: auto;
}

.jp-OutputArea-child {
  display: table;
  table-layout: fixed;
  width: 100%;
  overflow: hidden;
}

.jp-OutputPrompt {
  width: var(--jp-cell-prompt-width);
  color: var(--jp-cell-outprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);

  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;

  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-OutputArea-prompt {
  display: table-cell;
  vertical-align: top;
}

.jp-OutputArea-output {
  display: table-cell;
  width: 100%;
  height: auto;
  overflow: auto;
  user-select: text;
  -moz-user-select: text;
  -webkit-user-select: text;
  -ms-user-select: text;
}

.jp-OutputArea .jp-RenderedText {
  padding-left: 1ch;
}

/**
 * Prompt overlay.
 */

.jp-OutputArea-promptOverlay {
  position: absolute;
  top: 0;
  width: var(--jp-cell-prompt-width);
  height: 100%;
  opacity: 0.5;
}

.jp-OutputArea-promptOverlay:hover {
  background: var(--jp-layout-color2);
  box-shadow: inset 0 0 1px var(--jp-inverse-layout-color0);
  cursor: zoom-out;
}

.jp-mod-outputsScrolled .jp-OutputArea-promptOverlay:hover {
  cursor: zoom-in;
}

/**
 * Isolated output.
 */
.jp-OutputArea-output.jp-mod-isolated {
  width: 100%;
  display: block;
}

/*
When drag events occur, `lm-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated {
  position: relative;
}

body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

/* pre */

.jp-OutputArea-output pre {
  border: none;
  margin: 0;
  padding: 0;
  overflow-x: auto;
  overflow-y: auto;
  word-break: break-all;
  word-wrap: break-word;
  white-space: pre-wrap;
}

/* tables */

.jp-OutputArea-output.jp-RenderedHTMLCommon table {
  margin-left: 0;
  margin-right: 0;
}

/* description lists */

.jp-OutputArea-output dl,
.jp-OutputArea-output dt,
.jp-OutputArea-output dd {
  display: block;
}

.jp-OutputArea-output dl {
  width: 100%;
  overflow: hidden;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dt {
  font-weight: bold;
  float: left;
  width: 20%;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dd {
  float: left;
  width: 80%;
  padding: 0;
  margin: 0;
}

.jp-TrimmedOutputs pre {
  background: var(--jp-layout-color3);
  font-size: calc(var(--jp-code-font-size) * 1.4);
  text-align: center;
  text-transform: uppercase;
}

/* Hide the gutter in case of
 *  - nested output areas (e.g. in the case of output widgets)
 *  - mirrored output areas
 */
.jp-OutputArea .jp-OutputArea .jp-OutputArea-prompt {
  display: none;
}

/* Hide empty lines in the output area, for instance due to cleared widgets */
.jp-OutputArea-prompt:empty {
  padding: 0;
  border: 0;
}

/*-----------------------------------------------------------------------------
| executeResult is added to any Output-result for the display of the object
| returned by a cell
|----------------------------------------------------------------------------*/

.jp-OutputArea-output.jp-OutputArea-executeResult {
  margin-left: 0;
  width: 100%;
}

/* Text output with the Out[] prompt needs a top padding to match the
 * alignment of the Out[] prompt itself.
 */
.jp-OutputArea-executeResult .jp-RenderedText.jp-OutputArea-output {
  padding-top: var(--jp-code-padding);
  border-top: var(--jp-border-width) solid transparent;
}

/*-----------------------------------------------------------------------------
| The Stdin output
|----------------------------------------------------------------------------*/

.jp-Stdin-prompt {
  color: var(--jp-content-font-color0);
  padding-right: var(--jp-code-padding);
  vertical-align: baseline;
  flex: 0 0 auto;
}

.jp-Stdin-input {
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  color: inherit;
  background-color: inherit;
  width: 42%;
  min-width: 200px;

  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;

  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0 0.25em;
  margin: 0 0.25em;
  flex: 0 0 70%;
}

.jp-Stdin-input::placeholder {
  opacity: 0;
}

.jp-Stdin-input:focus {
  box-shadow: none;
}

.jp-Stdin-input:focus::placeholder {
  opacity: 1;
}

/*-----------------------------------------------------------------------------
| Output Area View
|----------------------------------------------------------------------------*/

.jp-LinkedOutputView .jp-OutputArea {
  height: 100%;
  display: block;
}

.jp-LinkedOutputView .jp-OutputArea-output:only-child {
  height: 100%;
}

/*-----------------------------------------------------------------------------
| Printing
|----------------------------------------------------------------------------*/

@media print {
  .jp-OutputArea-child {
    break-inside: avoid-page;
  }
}

/*-----------------------------------------------------------------------------
| Mobile
|----------------------------------------------------------------------------*/
@media only screen and (max-width: 760px) {
  .jp-OutputPrompt {
    display: table-row;
    text-align: left;
  }

  .jp-OutputArea-child .jp-OutputArea-output {
    display: table-row;
    margin-left: var(--jp-notebook-padding);
  }
}

/* Trimmed outputs warning */
.jp-TrimmedOutputs > a {
  margin: 10px;
  text-decoration: none;
  cursor: pointer;
}

.jp-TrimmedOutputs > a:hover {
  text-decoration: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Table of Contents
|----------------------------------------------------------------------------*/

:root {
  --jp-private-toc-active-width: 4px;
}

.jp-TableOfContents {
  display: flex;
  flex-direction: column;
  background: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  height: 100%;
}

.jp-TableOfContents-placeholder {
  text-align: center;
}

.jp-TableOfContents-placeholderContent {
  color: var(--jp-content-font-color2);
  padding: 8px;
}

.jp-TableOfContents-placeholderContent > h3 {
  margin-bottom: var(--jp-content-heading-margin-bottom);
}

.jp-TableOfContents .jp-SidePanel-content {
  overflow-y: auto;
}

.jp-TableOfContents-tree {
  margin: 4px;
}

.jp-TableOfContents ol {
  list-style-type: none;
}

/* stylelint-disable-next-line selector-max-type */
.jp-TableOfContents li > ol {
  /* Align left border with triangle icon center */
  padding-left: 11px;
}

.jp-TableOfContents-content {
  /* left margin for the active heading indicator */
  margin: 0 0 0 var(--jp-private-toc-active-width);
  padding: 0;
  background-color: var(--jp-layout-color1);
}

.jp-tocItem {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-tocItem-heading {
  display: flex;
  cursor: pointer;
}

.jp-tocItem-heading:hover {
  background-color: var(--jp-layout-color2);
}

.jp-tocItem-content {
  display: block;
  padding: 4px 0;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow-x: hidden;
}

.jp-tocItem-collapser {
  height: 20px;
  margin: 2px 2px 0;
  padding: 0;
  background: none;
  border: none;
  cursor: pointer;
}

.jp-tocItem-collapser:hover {
  background-color: var(--jp-layout-color3);
}

/* Active heading indicator */

.jp-tocItem-heading::before {
  content: ' ';
  background: transparent;
  width: var(--jp-private-toc-active-width);
  height: 24px;
  position: absolute;
  left: 0;
  border-radius: var(--jp-border-radius);
}

.jp-tocItem-heading.jp-tocItem-active::before {
  background-color: var(--jp-brand-color1);
}

.jp-tocItem-heading:hover.jp-tocItem-active::before {
  background: var(--jp-brand-color0);
  opacity: 1;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapser {
  flex: 0 0 var(--jp-cell-collapser-width);
  padding: 0;
  margin: 0;
  border: none;
  outline: none;
  background: transparent;
  border-radius: var(--jp-border-radius);
  opacity: 1;
}

.jp-Collapser-child {
  display: block;
  width: 100%;
  box-sizing: border-box;

  /* height: 100% doesn't work because the height of its parent is computed from content */
  position: absolute;
  top: 0;
  bottom: 0;
}

/*-----------------------------------------------------------------------------
| Printing
|----------------------------------------------------------------------------*/

/*
Hiding collapsers in print mode.

Note: input and output wrappers have "display: block" propery in print mode.
*/

@media print {
  .jp-Collapser {
    display: none;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Header/Footer
|----------------------------------------------------------------------------*/

/* Hidden by zero height by default */
.jp-CellHeader,
.jp-CellFooter {
  height: 0;
  width: 100%;
  padding: 0;
  margin: 0;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Input
|----------------------------------------------------------------------------*/

/* All input areas */
.jp-InputArea {
  display: table;
  table-layout: fixed;
  width: 100%;
  overflow: hidden;
}

.jp-InputArea-editor {
  display: table-cell;
  overflow: hidden;
  vertical-align: top;

  /* This is the non-active, default styling */
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  border-radius: 0;
  background: var(--jp-cell-editor-background);
}

.jp-InputPrompt {
  display: table-cell;
  vertical-align: top;
  width: var(--jp-cell-prompt-width);
  color: var(--jp-cell-inprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  opacity: var(--jp-cell-prompt-opacity);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;

  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;

  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/*-----------------------------------------------------------------------------
| Mobile
|----------------------------------------------------------------------------*/
@media only screen and (max-width: 760px) {
  .jp-InputArea-editor {
    display: table-row;
    margin-left: var(--jp-notebook-padding);
  }

  .jp-InputPrompt {
    display: table-row;
    text-align: left;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Placeholder {
  display: table;
  table-layout: fixed;
  width: 100%;
}

.jp-Placeholder-prompt {
  display: table-cell;
  box-sizing: border-box;
}

.jp-Placeholder-content {
  display: table-cell;
  padding: 4px 6px;
  border: 1px solid transparent;
  border-radius: 0;
  background: none;
  box-sizing: border-box;
  cursor: pointer;
}

.jp-Placeholder-contentContainer {
  display: flex;
}

.jp-Placeholder-content:hover,
.jp-InputPlaceholder > .jp-Placeholder-content:hover {
  border-color: var(--jp-layout-color3);
}

.jp-Placeholder-content .jp-MoreHorizIcon {
  width: 32px;
  height: 16px;
  border: 1px solid transparent;
  border-radius: var(--jp-border-radius);
}

.jp-Placeholder-content .jp-MoreHorizIcon:hover {
  border: 1px solid var(--jp-border-color1);
  box-shadow: 0 0 2px 0 rgba(0, 0, 0, 0.25);
  background-color: var(--jp-layout-color0);
}

.jp-PlaceholderText {
  white-space: nowrap;
  overflow-x: hidden;
  color: var(--jp-inverse-layout-color3);
  font-family: var(--jp-code-font-family);
}

.jp-InputPlaceholder > .jp-Placeholder-content {
  border-color: var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-cell-scrolling-output-offset: 5px;
}

/*-----------------------------------------------------------------------------
| Cell
|----------------------------------------------------------------------------*/

.jp-Cell {
  padding: var(--jp-cell-padding);
  margin: 0;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Common input/output
|----------------------------------------------------------------------------*/

.jp-Cell-inputWrapper,
.jp-Cell-outputWrapper {
  display: flex;
  flex-direction: row;
  padding: 0;
  margin: 0;

  /* Added to reveal the box-shadow on the input and output collapsers. */
  overflow: visible;
}

/* Only input/output areas inside cells */
.jp-Cell-inputArea,
.jp-Cell-outputArea {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Collapser
|----------------------------------------------------------------------------*/

/* Make the output collapser disappear when there is not output, but do so
 * in a manner that leaves it in the layout and preserves its width.
 */
.jp-Cell.jp-mod-noOutputs .jp-Cell-outputCollapser {
  border: none !important;
  background: transparent !important;
}

.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputCollapser {
  min-height: var(--jp-cell-collapser-min-height);
}

/*-----------------------------------------------------------------------------
| Output
|----------------------------------------------------------------------------*/

/* Put a space between input and output when there IS output */
.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputWrapper {
  margin-top: 5px;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea {
  overflow-y: auto;
  max-height: 24em;
  margin-left: var(--jp-private-cell-scrolling-output-offset);
  resize: vertical;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea[style*='height'] {
  max-height: unset;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea::after {
  content: ' ';
  box-shadow: inset 0 0 6px 2px rgb(0 0 0 / 30%);
  width: 100%;
  height: 100%;
  position: sticky;
  bottom: 0;
  top: 0;
  margin-top: -50%;
  float: left;
  display: block;
  pointer-events: none;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-child {
  padding-top: 6px;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
  width: calc(
    var(--jp-cell-prompt-width) - var(--jp-private-cell-scrolling-output-offset)
  );
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-promptOverlay {
  left: calc(-1 * var(--jp-private-cell-scrolling-output-offset));
}

/*-----------------------------------------------------------------------------
| CodeCell
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| MarkdownCell
|----------------------------------------------------------------------------*/

.jp-MarkdownOutput {
  display: table-cell;
  width: 100%;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: var(--jp-code-padding);
}

.jp-MarkdownOutput.jp-RenderedHTMLCommon {
  overflow: auto;
}

/* collapseHeadingButton (show always if hiddenCellsButton is _not_ shown) */
.jp-collapseHeadingButton {
  display: flex;
  min-height: var(--jp-cell-collapser-min-height);
  font-size: var(--jp-code-font-size);
  position: absolute;
  background-color: transparent;
  background-size: 25px;
  background-repeat: no-repeat;
  background-position-x: center;
  background-position-y: top;
  background-image: var(--jp-icon-caret-down);
  right: 0;
  top: 0;
  bottom: 0;
}

.jp-collapseHeadingButton.jp-mod-collapsed {
  background-image: var(--jp-icon-caret-right);
}

/*
 set the container font size to match that of content
 so that the nested collapse buttons have the right size
*/
.jp-MarkdownCell .jp-InputPrompt {
  font-size: var(--jp-content-font-size1);
}

/*
  Align collapseHeadingButton with cell top header
  The font sizes are identical to the ones in packages/rendermime/style/base.css
*/
.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='1'] {
  font-size: var(--jp-content-font-size5);
  background-position-y: calc(0.3 * var(--jp-content-font-size5));
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='2'] {
  font-size: var(--jp-content-font-size4);
  background-position-y: calc(0.3 * var(--jp-content-font-size4));
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='3'] {
  font-size: var(--jp-content-font-size3);
  background-position-y: calc(0.3 * var(--jp-content-font-size3));
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='4'] {
  font-size: var(--jp-content-font-size2);
  background-position-y: calc(0.3 * var(--jp-content-font-size2));
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='5'] {
  font-size: var(--jp-content-font-size1);
  background-position-y: top;
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='6'] {
  font-size: var(--jp-content-font-size0);
  background-position-y: top;
}

/* collapseHeadingButton (show only on (hover,active) if hiddenCellsButton is shown) */
.jp-Notebook.jp-mod-showHiddenCellsButton .jp-collapseHeadingButton {
  display: none;
}

.jp-Notebook.jp-mod-showHiddenCellsButton
  :is(.jp-MarkdownCell:hover, .jp-mod-active)
  .jp-collapseHeadingButton {
  display: flex;
}

/* showHiddenCellsButton (only show if jp-mod-showHiddenCellsButton is set, which
is a consequence of the showHiddenCellsButton option in Notebook Settings)*/
.jp-Notebook.jp-mod-showHiddenCellsButton .jp-showHiddenCellsButton {
  margin-left: calc(var(--jp-cell-prompt-width) + 2 * var(--jp-code-padding));
  margin-top: var(--jp-code-padding);
  border: 1px solid var(--jp-border-color2);
  background-color: var(--jp-border-color3) !important;
  color: var(--jp-content-font-color0) !important;
  display: flex;
}

.jp-Notebook.jp-mod-showHiddenCellsButton .jp-showHiddenCellsButton:hover {
  background-color: var(--jp-border-color2) !important;
}

.jp-showHiddenCellsButton {
  display: none;
}

/*-----------------------------------------------------------------------------
| Printing
|----------------------------------------------------------------------------*/

/*
Using block instead of flex to allow the use of the break-inside CSS property for
cell outputs.
*/

@media print {
  .jp-Cell-inputWrapper,
  .jp-Cell-outputWrapper {
    display: block;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-notebook-toolbar-padding: 2px 5px 2px 2px;
}

/*-----------------------------------------------------------------------------

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-NotebookPanel-toolbar {
  padding: var(--jp-notebook-toolbar-padding);

  /* disable paint containment from lumino 2.0 default strict CSS containment */
  contain: style size !important;
}

.jp-Toolbar-item.jp-Notebook-toolbarCellType .jp-select-wrapper.jp-mod-focused {
  border: none;
  box-shadow: none;
}

.jp-Notebook-toolbarCellTypeDropdown select {
  height: 24px;
  font-size: var(--jp-ui-font-size1);
  line-height: 14px;
  border-radius: 0;
  display: block;
}

.jp-Notebook-toolbarCellTypeDropdown span {
  top: 5px !important;
}

.jp-Toolbar-responsive-popup {
  position: absolute;
  height: fit-content;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-end;
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  background: var(--jp-toolbar-background);
  min-height: var(--jp-toolbar-micro-height);
  padding: var(--jp-notebook-toolbar-padding);
  z-index: 1;
  right: 0;
  top: 0;
}

.jp-Toolbar > .jp-Toolbar-responsive-opener {
  margin-left: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-Notebook-ExecutionIndicator {
  position: relative;
  display: inline-block;
  height: 100%;
  z-index: 9997;
}

.jp-Notebook-ExecutionIndicator-tooltip {
  visibility: hidden;
  height: auto;
  width: max-content;
  width: -moz-max-content;
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color1);
  text-align: justify;
  border-radius: 6px;
  padding: 0 5px;
  position: fixed;
  display: table;
}

.jp-Notebook-ExecutionIndicator-tooltip.up {
  transform: translateX(-50%) translateY(-100%) translateY(-32px);
}

.jp-Notebook-ExecutionIndicator-tooltip.down {
  transform: translateX(calc(-100% + 16px)) translateY(5px);
}

.jp-Notebook-ExecutionIndicator-tooltip.hidden {
  display: none;
}

.jp-Notebook-ExecutionIndicator:hover .jp-Notebook-ExecutionIndicator-tooltip {
  visibility: visible;
}

.jp-Notebook-ExecutionIndicator span {
  font-size: var(--jp-ui-font-size1);
  font-family: var(--jp-ui-font-family);
  color: var(--jp-ui-font-color1);
  line-height: 24px;
  display: block;
}

.jp-Notebook-ExecutionIndicator-progress-bar {
  display: flex;
  justify-content: center;
  height: 100%;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*
 * Execution indicator
 */
.jp-tocItem-content::after {
  content: '';

  /* Must be identical to form a circle */
  width: 12px;
  height: 12px;
  background: none;
  border: none;
  position: absolute;
  right: 0;
}

.jp-tocItem-content[data-running='0']::after {
  border-radius: 50%;
  border: var(--jp-border-width) solid var(--jp-inverse-layout-color3);
  background: none;
}

.jp-tocItem-content[data-running='1']::after {
  border-radius: 50%;
  border: var(--jp-border-width) solid var(--jp-inverse-layout-color3);
  background-color: var(--jp-inverse-layout-color3);
}

.jp-tocItem-content[data-running='0'],
.jp-tocItem-content[data-running='1'] {
  margin-right: 12px;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-Notebook-footer {
  height: 27px;
  margin-left: calc(
    var(--jp-cell-prompt-width) + var(--jp-cell-collapser-width) +
      var(--jp-cell-padding)
  );
  width: calc(
    100% -
      (
        var(--jp-cell-prompt-width) + var(--jp-cell-collapser-width) +
          var(--jp-cell-padding) + var(--jp-cell-padding)
      )
  );
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  color: var(--jp-ui-font-color3);
  margin-top: 6px;
  background: none;
  cursor: pointer;
}

.jp-Notebook-footer:focus {
  border-color: var(--jp-cell-editor-active-border-color);
}

/* For devices that support hovering, hide footer until hover */
@media (hover: hover) {
  .jp-Notebook-footer {
    opacity: 0;
  }

  .jp-Notebook-footer:focus,
  .jp-Notebook-footer:hover {
    opacity: 1;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Imports
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-side-by-side-output-size: 1fr;
  --jp-side-by-side-resized-cell: var(--jp-side-by-side-output-size);
  --jp-private-notebook-dragImage-width: 304px;
  --jp-private-notebook-dragImage-height: 36px;
  --jp-private-notebook-selected-color: var(--md-blue-400);
  --jp-private-notebook-active-color: var(--md-green-400);
}

/*-----------------------------------------------------------------------------
| Notebook
|----------------------------------------------------------------------------*/

/* stylelint-disable selector-max-class */

.jp-NotebookPanel {
  display: block;
  height: 100%;
}

.jp-NotebookPanel.jp-Document {
  min-width: 240px;
  min-height: 120px;
}

.jp-Notebook {
  padding: var(--jp-notebook-padding);
  outline: none;
  overflow: auto;
  background: var(--jp-layout-color0);
}

.jp-Notebook.jp-mod-scrollPastEnd::after {
  display: block;
  content: '';
  min-height: var(--jp-notebook-scroll-padding);
}

.jp-MainAreaWidget-ContainStrict .jp-Notebook * {
  contain: strict;
}

.jp-Notebook .jp-Cell {
  overflow: visible;
}

.jp-Notebook .jp-Cell .jp-InputPrompt {
  cursor: move;
}

/*-----------------------------------------------------------------------------
| Notebook state related styling
|
| The notebook and cells each have states, here are the possibilities:
|
| - Notebook
|   - Command
|   - Edit
| - Cell
|   - None
|   - Active (only one can be active)
|   - Selected (the cells actions are applied to)
|   - Multiselected (when multiple selected, the cursor)
|   - No outputs
|----------------------------------------------------------------------------*/

/* Command or edit modes */

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-InputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-OutputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

/* cell is active */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser {
  background: var(--jp-brand-color1);
}

/* cell is dirty */
.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt {
  color: var(--jp-warn-color1);
}

.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt::before {
  color: var(--jp-warn-color1);
  content: '•';
}

.jp-Notebook .jp-Cell.jp-mod-active.jp-mod-dirty .jp-Collapser {
  background: var(--jp-warn-color1);
}

/* collapser is hovered */
.jp-Notebook .jp-Cell .jp-Collapser:hover {
  box-shadow: var(--jp-elevation-z2);
  background: var(--jp-brand-color1);
  opacity: var(--jp-cell-collapser-not-active-hover-opacity);
}

/* cell is active and collapser is hovered */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser:hover {
  background: var(--jp-brand-color0);
  opacity: 1;
}

/* Command mode */

.jp-Notebook.jp-mod-commandMode .jp-Cell.jp-mod-selected {
  background: var(--jp-notebook-multiselected-color);
}

.jp-Notebook.jp-mod-commandMode
  .jp-Cell.jp-mod-active.jp-mod-selected:not(.jp-mod-multiSelected) {
  background: transparent;
}

/* Edit mode */

.jp-Notebook.jp-mod-editMode .jp-Cell.jp-mod-active .jp-InputArea-editor {
  border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-cell-editor-active-background);
}

/*-----------------------------------------------------------------------------
| Notebook drag and drop
|----------------------------------------------------------------------------*/

.jp-Notebook-cell.jp-mod-dropSource {
  opacity: 0.5;
}

.jp-Notebook-cell.jp-mod-dropTarget,
.jp-Notebook.jp-mod-commandMode
  .jp-Notebook-cell.jp-mod-active.jp-mod-selected.jp-mod-dropTarget {
  border-top-color: var(--jp-private-notebook-selected-color);
  border-top-style: solid;
  border-top-width: 2px;
}

.jp-dragImage {
  display: block;
  flex-direction: row;
  width: var(--jp-private-notebook-dragImage-width);
  height: var(--jp-private-notebook-dragImage-height);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background);
  overflow: visible;
}

.jp-dragImage-singlePrompt {
  box-shadow: 2px 2px 4px 0 rgba(0, 0, 0, 0.12);
}

.jp-dragImage .jp-dragImage-content {
  flex: 1 1 auto;
  z-index: 2;
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  line-height: var(--jp-code-line-height);
  padding: var(--jp-code-padding);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background-color);
  color: var(--jp-content-font-color3);
  text-align: left;
  margin: 4px 4px 4px 0;
}

.jp-dragImage .jp-dragImage-prompt {
  flex: 0 0 auto;
  min-width: 36px;
  color: var(--jp-cell-inprompt-font-color);
  padding: var(--jp-code-padding);
  padding-left: 12px;
  font-family: var(--jp-cell-prompt-font-family);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: 1.9;
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
}

.jp-dragImage-multipleBack {
  z-index: -1;
  position: absolute;
  height: 32px;
  width: 300px;
  top: 8px;
  left: 8px;
  background: var(--jp-layout-color2);
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  box-shadow: 2px 2px 4px 0 rgba(0, 0, 0, 0.12);
}

/*-----------------------------------------------------------------------------
| Cell toolbar
|----------------------------------------------------------------------------*/

.jp-NotebookTools {
  display: block;
  min-width: var(--jp-sidebar-min-width);
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);

  /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  overflow: auto;
}

.jp-ActiveCellTool {
  padding: 12px 0;
  display: flex;
}

.jp-ActiveCellTool-Content {
  flex: 1 1 auto;
}

.jp-ActiveCellTool .jp-ActiveCellTool-CellContent {
  background: var(--jp-cell-editor-background);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  border-radius: 0;
  min-height: 29px;
}

.jp-ActiveCellTool .jp-InputPrompt {
  min-width: calc(var(--jp-cell-prompt-width) * 0.75);
}

.jp-ActiveCellTool-CellContent > pre {
  padding: 5px 4px;
  margin: 0;
  white-space: normal;
}

.jp-MetadataEditorTool {
  flex-direction: column;
  padding: 12px 0;
}

.jp-RankedPanel > :not(:first-child) {
  margin-top: 12px;
}

.jp-KeySelector select.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: var(--jp-border-width) solid var(--jp-border-color1);
}

.jp-KeySelector label,
.jp-MetadataEditorTool label,
.jp-NumberSetter label {
  line-height: 1.4;
}

.jp-NotebookTools .jp-select-wrapper {
  margin-top: 4px;
  margin-bottom: 0;
}

.jp-NumberSetter input {
  width: 100%;
  margin-top: 4px;
}

.jp-NotebookTools .jp-Collapse {
  margin-top: 16px;
}

/*-----------------------------------------------------------------------------
| Presentation Mode (.jp-mod-presentationMode)
|----------------------------------------------------------------------------*/

.jp-mod-presentationMode .jp-Notebook {
  --jp-content-font-size1: var(--jp-content-presentation-font-size1);
  --jp-code-font-size: var(--jp-code-presentation-font-size);
}

.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-InputPrompt,
.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-OutputPrompt {
  flex: 0 0 110px;
}

/*-----------------------------------------------------------------------------
| Side-by-side Mode (.jp-mod-sideBySide)
|----------------------------------------------------------------------------*/
.jp-mod-sideBySide.jp-Notebook .jp-Notebook-cell {
  margin-top: 3em;
  margin-bottom: 3em;
  margin-left: 5%;
  margin-right: 5%;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell {
  display: grid;
  grid-template-columns: minmax(0, 1fr) min-content minmax(
      0,
      var(--jp-side-by-side-output-size)
    );
  grid-template-rows: auto minmax(0, 1fr) auto;
  grid-template-areas:
    'header header header'
    'input handle output'
    'footer footer footer';
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell.jp-mod-resizedCell {
  grid-template-columns: minmax(0, 1fr) min-content minmax(
      0,
      var(--jp-side-by-side-resized-cell)
    );
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellHeader {
  grid-area: header;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-Cell-inputWrapper {
  grid-area: input;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-Cell-outputWrapper {
  /* overwrite the default margin (no vertical separation needed in side by side move */
  margin-top: 0;
  grid-area: output;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellFooter {
  grid-area: footer;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellResizeHandle {
  grid-area: handle;
  user-select: none;
  display: block;
  height: 100%;
  cursor: ew-resize;
  padding: 0 var(--jp-cell-padding);
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellResizeHandle::after {
  content: '';
  display: block;
  background: var(--jp-border-color2);
  height: 100%;
  width: 5px;
}

.jp-mod-sideBySide.jp-Notebook
  .jp-CodeCell.jp-mod-resizedCell
  .jp-CellResizeHandle::after {
  background: var(--jp-border-color0);
}

.jp-CellResizeHandle {
  display: none;
}

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Cell-Placeholder {
  padding-left: 55px;
}

.jp-Cell-Placeholder-wrapper {
  background: #fff;
  border: 1px solid;
  border-color: #e5e6e9 #dfe0e4 #d0d1d5;
  border-radius: 4px;
  -webkit-border-radius: 4px;
  margin: 10px 15px;
}

.jp-Cell-Placeholder-wrapper-inner {
  padding: 15px;
  position: relative;
}

.jp-Cell-Placeholder-wrapper-body {
  background-repeat: repeat;
  background-size: 50% auto;
}

.jp-Cell-Placeholder-wrapper-body div {
  background: #f6f7f8;
  background-image: -webkit-linear-gradient(
    left,
    #f6f7f8 0%,
    #edeef1 20%,
    #f6f7f8 40%,
    #f6f7f8 100%
  );
  background-repeat: no-repeat;
  background-size: 800px 104px;
  height: 104px;
  position: absolute;
  right: 15px;
  left: 15px;
  top: 15px;
}

div.jp-Cell-Placeholder-h1 {
  top: 20px;
  height: 20px;
  left: 15px;
  width: 150px;
}

div.jp-Cell-Placeholder-h2 {
  left: 15px;
  top: 50px;
  height: 10px;
  width: 100px;
}

div.jp-Cell-Placeholder-content-1,
div.jp-Cell-Placeholder-content-2,
div.jp-Cell-Placeholder-content-3 {
  left: 15px;
  right: 15px;
  height: 10px;
}

div.jp-Cell-Placeholder-content-1 {
  top: 100px;
}

div.jp-Cell-Placeholder-content-2 {
  top: 120px;
}

div.jp-Cell-Placeholder-content-3 {
  top: 140px;
}

</style>
<style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
The following CSS variables define the main, public API for styling JupyterLab.
These variables should be used by all plugins wherever possible. In other
words, plugins should not define custom colors, sizes, etc unless absolutely
necessary. This enables users to change the visual theme of JupyterLab
by changing these variables.

Many variables appear in an ordered sequence (0,1,2,3). These sequences
are designed to work well together, so for example, `--jp-border-color1` should
be used with `--jp-layout-color1`. The numbers have the following meanings:

* 0: super-primary, reserved for special emphasis
* 1: primary, most important under normal situations
* 2: secondary, next most important under normal situations
* 3: tertiary, next most important under normal situations

Throughout JupyterLab, we are mostly following principles from Google's
Material Design when selecting colors. We are not, however, following
all of MD as it is not optimized for dense, information rich UIs.
*/

:root {
  /* Elevation
   *
   * We style box-shadows using Material Design's idea of elevation. These particular numbers are taken from here:
   *
   * https://github.com/material-components/material-components-web
   * https://material-components-web.appspot.com/elevation.html
   */

  --jp-shadow-base-lightness: 0;
  --jp-shadow-umbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.2
  );
  --jp-shadow-penumbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.14
  );
  --jp-shadow-ambient-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.12
  );
  --jp-elevation-z0: none;
  --jp-elevation-z1: 0 2px 1px -1px var(--jp-shadow-umbra-color),
    0 1px 1px 0 var(--jp-shadow-penumbra-color),
    0 1px 3px 0 var(--jp-shadow-ambient-color);
  --jp-elevation-z2: 0 3px 1px -2px var(--jp-shadow-umbra-color),
    0 2px 2px 0 var(--jp-shadow-penumbra-color),
    0 1px 5px 0 var(--jp-shadow-ambient-color);
  --jp-elevation-z4: 0 2px 4px -1px var(--jp-shadow-umbra-color),
    0 4px 5px 0 var(--jp-shadow-penumbra-color),
    0 1px 10px 0 var(--jp-shadow-ambient-color);
  --jp-elevation-z6: 0 3px 5px -1px var(--jp-shadow-umbra-color),
    0 6px 10px 0 var(--jp-shadow-penumbra-color),
    0 1px 18px 0 var(--jp-shadow-ambient-color);
  --jp-elevation-z8: 0 5px 5px -3px var(--jp-shadow-umbra-color),
    0 8px 10px 1px var(--jp-shadow-penumbra-color),
    0 3px 14px 2px var(--jp-shadow-ambient-color);
  --jp-elevation-z12: 0 7px 8px -4px var(--jp-shadow-umbra-color),
    0 12px 17px 2px var(--jp-shadow-penumbra-color),
    0 5px 22px 4px var(--jp-shadow-ambient-color);
  --jp-elevation-z16: 0 8px 10px -5px var(--jp-shadow-umbra-color),
    0 16px 24px 2px var(--jp-shadow-penumbra-color),
    0 6px 30px 5px var(--jp-shadow-ambient-color);
  --jp-elevation-z20: 0 10px 13px -6px var(--jp-shadow-umbra-color),
    0 20px 31px 3px var(--jp-shadow-penumbra-color),
    0 8px 38px 7px var(--jp-shadow-ambient-color);
  --jp-elevation-z24: 0 11px 15px -7px var(--jp-shadow-umbra-color),
    0 24px 38px 3px var(--jp-shadow-penumbra-color),
    0 9px 46px 8px var(--jp-shadow-ambient-color);

  /* Borders
   *
   * The following variables, specify the visual styling of borders in JupyterLab.
   */

  --jp-border-width: 1px;
  --jp-border-color0: var(--md-grey-400);
  --jp-border-color1: var(--md-grey-400);
  --jp-border-color2: var(--md-grey-300);
  --jp-border-color3: var(--md-grey-200);
  --jp-inverse-border-color: var(--md-grey-600);
  --jp-border-radius: 2px;

  /* UI Fonts
   *
   * The UI font CSS variables are used for the typography all of the JupyterLab
   * user interface elements that are not directly user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-ui-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-ui-font-scale-factor: 1.2;
  --jp-ui-font-size0: 0.83333em;
  --jp-ui-font-size1: 13px; /* Base font size */
  --jp-ui-font-size2: 1.2em;
  --jp-ui-font-size3: 1.44em;
  --jp-ui-font-family: system-ui, -apple-system, blinkmacsystemfont, 'Segoe UI',
    helvetica, arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';

  /*
   * Use these font colors against the corresponding main layout colors.
   * In a light theme, these go from dark to light.
   */

  /* Defaults use Material Design specification */
  --jp-ui-font-color0: rgba(0, 0, 0, 1);
  --jp-ui-font-color1: rgba(0, 0, 0, 0.87);
  --jp-ui-font-color2: rgba(0, 0, 0, 0.54);
  --jp-ui-font-color3: rgba(0, 0, 0, 0.38);

  /*
   * Use these against the brand/accent/warn/error colors.
   * These will typically go from light to darker, in both a dark and light theme.
   */

  --jp-ui-inverse-font-color0: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color1: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color2: rgba(255, 255, 255, 0.7);
  --jp-ui-inverse-font-color3: rgba(255, 255, 255, 0.5);

  /* Content Fonts
   *
   * Content font variables are used for typography of user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-content-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-content-line-height: 1.6;
  --jp-content-font-scale-factor: 1.2;
  --jp-content-font-size0: 0.83333em;
  --jp-content-font-size1: 14px; /* Base font size */
  --jp-content-font-size2: 1.2em;
  --jp-content-font-size3: 1.44em;
  --jp-content-font-size4: 1.728em;
  --jp-content-font-size5: 2.0736em;

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-content-presentation-font-size1: 17px;
  --jp-content-heading-line-height: 1;
  --jp-content-heading-margin-top: 1.2em;
  --jp-content-heading-margin-bottom: 0.8em;
  --jp-content-heading-font-weight: 500;

  /* Defaults use Material Design specification */
  --jp-content-font-color0: rgba(0, 0, 0, 1);
  --jp-content-font-color1: rgba(0, 0, 0, 0.87);
  --jp-content-font-color2: rgba(0, 0, 0, 0.54);
  --jp-content-font-color3: rgba(0, 0, 0, 0.38);
  --jp-content-link-color: var(--md-blue-900);
  --jp-content-font-family: system-ui, -apple-system, blinkmacsystemfont,
    'Segoe UI', helvetica, arial, sans-serif, 'Apple Color Emoji',
    'Segoe UI Emoji', 'Segoe UI Symbol';

  /*
   * Code Fonts
   *
   * Code font variables are used for typography of code and other monospaces content.
   */

  --jp-code-font-size: 13px;
  --jp-code-line-height: 1.3077; /* 17px for 13px base */
  --jp-code-padding: 5px; /* 5px for 13px base, codemirror highlighting needs integer px value */
  --jp-code-font-family-default: menlo, consolas, 'DejaVu Sans Mono', monospace;
  --jp-code-font-family: var(--jp-code-font-family-default);

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-code-presentation-font-size: 16px;

  /* may need to tweak cursor width if you change font size */
  --jp-code-cursor-width0: 1.4px;
  --jp-code-cursor-width1: 2px;
  --jp-code-cursor-width2: 4px;

  /* Layout
   *
   * The following are the main layout colors use in JupyterLab. In a light
   * theme these would go from light to dark.
   */

  --jp-layout-color0: white;
  --jp-layout-color1: white;
  --jp-layout-color2: var(--md-grey-200);
  --jp-layout-color3: var(--md-grey-400);
  --jp-layout-color4: var(--md-grey-600);

  /* Inverse Layout
   *
   * The following are the inverse layout colors use in JupyterLab. In a light
   * theme these would go from dark to light.
   */

  --jp-inverse-layout-color0: #111;
  --jp-inverse-layout-color1: var(--md-grey-900);
  --jp-inverse-layout-color2: var(--md-grey-800);
  --jp-inverse-layout-color3: var(--md-grey-700);
  --jp-inverse-layout-color4: var(--md-grey-600);

  /* Brand/accent */

  --jp-brand-color0: var(--md-blue-900);
  --jp-brand-color1: var(--md-blue-700);
  --jp-brand-color2: var(--md-blue-300);
  --jp-brand-color3: var(--md-blue-100);
  --jp-brand-color4: var(--md-blue-50);
  --jp-accent-color0: var(--md-green-900);
  --jp-accent-color1: var(--md-green-700);
  --jp-accent-color2: var(--md-green-300);
  --jp-accent-color3: var(--md-green-100);

  /* State colors (warn, error, success, info) */

  --jp-warn-color0: var(--md-orange-900);
  --jp-warn-color1: var(--md-orange-700);
  --jp-warn-color2: var(--md-orange-300);
  --jp-warn-color3: var(--md-orange-100);
  --jp-error-color0: var(--md-red-900);
  --jp-error-color1: var(--md-red-700);
  --jp-error-color2: var(--md-red-300);
  --jp-error-color3: var(--md-red-100);
  --jp-success-color0: var(--md-green-900);
  --jp-success-color1: var(--md-green-700);
  --jp-success-color2: var(--md-green-300);
  --jp-success-color3: var(--md-green-100);
  --jp-info-color0: var(--md-cyan-900);
  --jp-info-color1: var(--md-cyan-700);
  --jp-info-color2: var(--md-cyan-300);
  --jp-info-color3: var(--md-cyan-100);

  /* Cell specific styles */

  --jp-cell-padding: 5px;
  --jp-cell-collapser-width: 8px;
  --jp-cell-collapser-min-height: 20px;
  --jp-cell-collapser-not-active-hover-opacity: 0.6;
  --jp-cell-editor-background: var(--md-grey-100);
  --jp-cell-editor-border-color: var(--md-grey-300);
  --jp-cell-editor-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-cell-editor-active-background: var(--jp-layout-color0);
  --jp-cell-editor-active-border-color: var(--jp-brand-color1);
  --jp-cell-prompt-width: 64px;
  --jp-cell-prompt-font-family: var(--jp-code-font-family-default);
  --jp-cell-prompt-letter-spacing: 0;
  --jp-cell-prompt-opacity: 1;
  --jp-cell-prompt-not-active-opacity: 0.5;
  --jp-cell-prompt-not-active-font-color: var(--md-grey-700);

  /* A custom blend of MD grey and blue 600
   * See https://meyerweb.com/eric/tools/color-blend/#546E7A:1E88E5:5:hex */
  --jp-cell-inprompt-font-color: #307fc1;

  /* A custom blend of MD grey and orange 600
   * https://meyerweb.com/eric/tools/color-blend/#546E7A:F4511E:5:hex */
  --jp-cell-outprompt-font-color: #bf5b3d;

  /* Notebook specific styles */

  --jp-notebook-padding: 10px;
  --jp-notebook-select-background: var(--jp-layout-color1);
  --jp-notebook-multiselected-color: var(--md-blue-50);

  /* The scroll padding is calculated to fill enough space at the bottom of the
  notebook to show one single-line cell (with appropriate padding) at the top
  when the notebook is scrolled all the way to the bottom. We also subtract one
  pixel so that no scrollbar appears if we have just one single-line cell in the
  notebook. This padding is to enable a 'scroll past end' feature in a notebook.
  */
  --jp-notebook-scroll-padding: calc(
    100% - var(--jp-code-font-size) * var(--jp-code-line-height) -
      var(--jp-code-padding) - var(--jp-cell-padding) - 1px
  );

  /* Rendermime styles */

  --jp-rendermime-error-background: #fdd;
  --jp-rendermime-table-row-background: var(--md-grey-100);
  --jp-rendermime-table-row-hover-background: var(--md-light-blue-50);

  /* Dialog specific styles */

  --jp-dialog-background: rgba(0, 0, 0, 0.25);

  /* Console specific styles */

  --jp-console-padding: 10px;

  /* Toolbar specific styles */

  --jp-toolbar-border-color: var(--jp-border-color1);
  --jp-toolbar-micro-height: 8px;
  --jp-toolbar-background: var(--jp-layout-color1);
  --jp-toolbar-box-shadow: 0 0 2px 0 rgba(0, 0, 0, 0.24);
  --jp-toolbar-header-margin: 4px 4px 0 4px;
  --jp-toolbar-active-background: var(--md-grey-300);

  /* Statusbar specific styles */

  --jp-statusbar-height: 24px;

  /* Input field styles */

  --jp-input-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-input-active-background: var(--jp-layout-color1);
  --jp-input-hover-background: var(--jp-layout-color1);
  --jp-input-background: var(--md-grey-100);
  --jp-input-border-color: var(--jp-inverse-border-color);
  --jp-input-active-border-color: var(--jp-brand-color1);
  --jp-input-active-box-shadow-color: rgba(19, 124, 189, 0.3);

  /* General editor styles */

  --jp-editor-selected-background: #d9d9d9;
  --jp-editor-selected-focused-background: #d7d4f0;
  --jp-editor-cursor-color: var(--jp-ui-font-color0);

  /* Code mirror specific styles */

  --jp-mirror-editor-keyword-color: #008000;
  --jp-mirror-editor-atom-color: #88f;
  --jp-mirror-editor-number-color: #080;
  --jp-mirror-editor-def-color: #00f;
  --jp-mirror-editor-variable-color: var(--md-grey-900);
  --jp-mirror-editor-variable-2-color: rgb(0, 54, 109);
  --jp-mirror-editor-variable-3-color: #085;
  --jp-mirror-editor-punctuation-color: #05a;
  --jp-mirror-editor-property-color: #05a;
  --jp-mirror-editor-operator-color: #a2f;
  --jp-mirror-editor-comment-color: #408080;
  --jp-mirror-editor-string-color: #ba2121;
  --jp-mirror-editor-string-2-color: #708;
  --jp-mirror-editor-meta-color: #a2f;
  --jp-mirror-editor-qualifier-color: #555;
  --jp-mirror-editor-builtin-color: #008000;
  --jp-mirror-editor-bracket-color: #997;
  --jp-mirror-editor-tag-color: #170;
  --jp-mirror-editor-attribute-color: #00c;
  --jp-mirror-editor-header-color: blue;
  --jp-mirror-editor-quote-color: #090;
  --jp-mirror-editor-link-color: #00c;
  --jp-mirror-editor-error-color: #f00;
  --jp-mirror-editor-hr-color: #999;

  /*
    RTC user specific colors.
    These colors are used for the cursor, username in the editor,
    and the icon of the user.
  */

  --jp-collaborator-color1: #ffad8e;
  --jp-collaborator-color2: #dac83d;
  --jp-collaborator-color3: #72dd76;
  --jp-collaborator-color4: #00e4d0;
  --jp-collaborator-color5: #45d4ff;
  --jp-collaborator-color6: #e2b1ff;
  --jp-collaborator-color7: #ff9de6;

  /* Vega extension styles */

  --jp-vega-background: white;

  /* Sidebar-related styles */

  --jp-sidebar-min-width: 250px;

  /* Search-related styles */

  --jp-search-toggle-off-opacity: 0.5;
  --jp-search-toggle-hover-opacity: 0.8;
  --jp-search-toggle-on-opacity: 1;
  --jp-search-selected-match-background-color: rgb(245, 200, 0);
  --jp-search-selected-match-color: black;
  --jp-search-unselected-match-background-color: var(
    --jp-inverse-layout-color0
  );
  --jp-search-unselected-match-color: var(--jp-ui-inverse-font-color0);

  /* Icon colors that work well with light or dark backgrounds */
  --jp-icon-contrast-color0: var(--md-purple-600);
  --jp-icon-contrast-color1: var(--md-green-600);
  --jp-icon-contrast-color2: var(--md-pink-600);
  --jp-icon-contrast-color3: var(--md-blue-600);

  /* Button colors */
  --jp-accept-color-normal: var(--md-blue-700);
  --jp-accept-color-hover: var(--md-blue-800);
  --jp-accept-color-active: var(--md-blue-900);
  --jp-warn-color-normal: var(--md-red-700);
  --jp-warn-color-hover: var(--md-red-800);
  --jp-warn-color-active: var(--md-red-900);
  --jp-reject-color-normal: var(--md-grey-600);
  --jp-reject-color-hover: var(--md-grey-700);
  --jp-reject-color-active: var(--md-grey-800);

  /* File or activity icons and switch semantic variables */
  --jp-jupyter-icon-color: #f37626;
  --jp-notebook-icon-color: #f37626;
  --jp-json-icon-color: var(--md-orange-700);
  --jp-console-icon-background-color: var(--md-blue-700);
  --jp-console-icon-color: white;
  --jp-terminal-icon-background-color: var(--md-grey-800);
  --jp-terminal-icon-color: var(--md-grey-200);
  --jp-text-editor-icon-color: var(--md-grey-700);
  --jp-inspector-icon-color: var(--md-grey-700);
  --jp-switch-color: var(--md-grey-400);
  --jp-switch-true-position-color: var(--md-orange-900);
}
</style>
<style type="text/css">
/* Force rendering true colors when outputing to pdf */
* {
  -webkit-print-color-adjust: exact;
}

/* Misc */
a.anchor-link {
  display: none;
}

/* Input area styling */
.jp-InputArea {
  overflow: hidden;
}

.jp-InputArea-editor {
  overflow: hidden;
}

.cm-editor.cm-s-jupyter .highlight pre {
/* weird, but --jp-code-padding defined to be 5px but 4px horizontal padding is hardcoded for pre.cm-line */
  padding: var(--jp-code-padding) 4px;
  margin: 0;

  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
  color: inherit;

}

.jp-OutputArea-output pre {
  line-height: inherit;
  font-family: inherit;
}

.jp-RenderedText pre {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-code-font-size);
}

/* Hiding the collapser by default */
.jp-Collapser {
  display: none;
}

@page {
    margin: 0.5in; /* Margin for each printed piece of paper */
}

@media print {
  .jp-Cell-inputWrapper,
  .jp-Cell-outputWrapper {
    display: block;
  }
}
</style>
<!-- Load mathjax -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-AMS_CHTML-full,Safe"> </script>
<!-- MathJax configuration -->
<script type="text/x-mathjax-config">
    init_mathjax = function() {
        if (window.MathJax) {
        // MathJax loaded
            MathJax.Hub.Config({
                TeX: {
                    equationNumbers: {
                    autoNumber: "AMS",
                    useLabelIds: true
                    }
                },
                tex2jax: {
                    inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                    displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                    processEscapes: true,
                    processEnvironments: true
                },
                displayAlign: 'center',
                CommonHTML: {
                    linebreaks: {
                    automatic: true
                    }
                }
            });

            MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
        }
    }
    init_mathjax();
    </script>
<!-- End of mathjax configuration --><script type="module">
  document.addEventListener("DOMContentLoaded", async () => {
    const diagrams = document.querySelectorAll(".jp-Mermaid > pre.mermaid");
    // do not load mermaidjs if not needed
    if (!diagrams.length) {
      return;
    }
    const mermaid = (await import("https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.7.0/mermaid.esm.min.mjs")).default;
    const parser = new DOMParser();

    mermaid.initialize({
      maxTextSize: 100000,
      maxEdges: 100000,
      startOnLoad: false,
      fontFamily: window
        .getComputedStyle(document.body)
        .getPropertyValue("--jp-ui-font-family"),
      theme: document.querySelector("body[data-jp-theme-light='true']")
        ? "default"
        : "dark",
    });

    let _nextMermaidId = 0;

    function makeMermaidImage(svg) {
      const img = document.createElement("img");
      const doc = parser.parseFromString(svg, "image/svg+xml");
      const svgEl = doc.querySelector("svg");
      const { maxWidth } = svgEl?.style || {};
      const firstTitle = doc.querySelector("title");
      const firstDesc = doc.querySelector("desc");

      img.setAttribute("src", `data:image/svg+xml,${encodeURIComponent(svg)}`);
      if (maxWidth) {
        img.width = parseInt(maxWidth);
      }
      if (firstTitle) {
        img.setAttribute("alt", firstTitle.textContent);
      }
      if (firstDesc) {
        const caption = document.createElement("figcaption");
        caption.className = "sr-only";
        caption.textContent = firstDesc.textContent;
        return [img, caption];
      }
      return [img];
    }

    async function makeMermaidError(text) {
      let errorMessage = "";
      try {
        await mermaid.parse(text);
      } catch (err) {
        errorMessage = `${err}`;
      }

      const result = document.createElement("details");
      result.className = 'jp-RenderedMermaid-Details';
      const summary = document.createElement("summary");
      summary.className = 'jp-RenderedMermaid-Summary';
      const pre = document.createElement("pre");
      const code = document.createElement("code");
      code.innerText = text;
      pre.appendChild(code);
      summary.appendChild(pre);
      result.appendChild(summary);

      const warning = document.createElement("pre");
      warning.innerText = errorMessage;
      result.appendChild(warning);
      return [result];
    }

    async function renderOneMarmaid(src) {
      const id = `jp-mermaid-${_nextMermaidId++}`;
      const parent = src.parentNode;
      let raw = src.textContent.trim();
      const el = document.createElement("div");
      el.style.visibility = "hidden";
      document.body.appendChild(el);
      let results = null;
      let output = null;
      try {
        let { svg } = await mermaid.render(id, raw, el);
        svg = cleanMermaidSvg(svg);
        results = makeMermaidImage(svg);
        output = document.createElement("figure");
        results.map(output.appendChild, output);
      } catch (err) {
        parent.classList.add("jp-mod-warning");
        results = await makeMermaidError(raw);
        output = results[0];
      } finally {
        el.remove();
      }
      parent.classList.add("jp-RenderedMermaid");
      parent.appendChild(output);
    }


    /**
     * Post-process to ensure mermaid diagrams contain only valid SVG and XHTML.
     */
    function cleanMermaidSvg(svg) {
      return svg.replace(RE_VOID_ELEMENT, replaceVoidElement);
    }


    /**
     * A regular expression for all void elements, which may include attributes and
     * a slash.
     *
     * @see https://developer.mozilla.org/en-US/docs/Glossary/Void_element
     *
     * Of these, only `<br>` is generated by Mermaid in place of `\n`,
     * but _any_ "malformed" tag will break the SVG rendering entirely.
     */
    const RE_VOID_ELEMENT =
      /<\s*(area|base|br|col|embed|hr|img|input|link|meta|param|source|track|wbr)\s*([^>]*?)\s*>/gi;

    /**
     * Ensure a void element is closed with a slash, preserving any attributes.
     */
    function replaceVoidElement(match, tag, rest) {
      rest = rest.trim();
      if (!rest.endsWith('/')) {
        rest = `${rest} /`;
      }
      return `<${tag} ${rest}>`;
    }

    void Promise.all([...diagrams].map(renderOneMarmaid));
  });
</script>
<style>
  .jp-Mermaid:not(.jp-RenderedMermaid) {
    display: none;
  }

  .jp-RenderedMermaid {
    overflow: auto;
    display: flex;
  }

  .jp-RenderedMermaid.jp-mod-warning {
    width: auto;
    padding: 0.5em;
    margin-top: 0.5em;
    border: var(--jp-border-width) solid var(--jp-warn-color2);
    border-radius: var(--jp-border-radius);
    color: var(--jp-ui-font-color1);
    font-size: var(--jp-ui-font-size1);
    white-space: pre-wrap;
    word-wrap: break-word;
  }

  .jp-RenderedMermaid figure {
    margin: 0;
    overflow: auto;
    max-width: 100%;
  }

  .jp-RenderedMermaid img {
    max-width: 100%;
  }

  .jp-RenderedMermaid-Details > pre {
    margin-top: 1em;
  }

  .jp-RenderedMermaid-Summary {
    color: var(--jp-warn-color2);
  }

  .jp-RenderedMermaid:not(.jp-mod-warning) pre {
    display: none;
  }

  .jp-RenderedMermaid-Summary > pre {
    display: inline-block;
    white-space: normal;
  }
</style>
<!-- End of mermaid configuration --></head>
<body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">
<main>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h1 id="1-Introduction"><strong>1 Introduction</strong><a class="anchor-link" href="#1-Introduction">¶</a></h1>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="1.1-Case-Study">1.1 Case Study<a class="anchor-link" href="#1.1-Case-Study">¶</a></h2><p><font size="3">On May 13, 2022, Elon Musk, the CEO of Tesla and a prominent figure in the cryptocurrency community, made a significant announcement on Twitter. In his tweet, Musk stated that Tesla would no longer accept Bitcoin as a form of payment. This unexpected decision sent shockwaves through the Bitcoin community and had a noticeable impact on the price of Bitcoin.</font></p>
<p><img alt="1-2.png" src="data:image/png;base64,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"/></p>
<p><font size="3">To analyze the causal relationship between Musk's tweet and Bitcoin's price and what would be the alternative sceinario of the Bitcoin prices if Elon Musk did not make the tweet, we will employ the "Google Causal Impact" using Python.</font></p>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="1.2-Google-Causal-Impact">1.2 Google Causal Impact<a class="anchor-link" href="#1.2-Google-Causal-Impact">¶</a></h2><p><font size="3">The "Google Causal Impact" is a statistical approach used to estimate the causal impact of a particular event on a target variable, while accounting for various other factors that may influence the outcome. It is based on Bayesian structural time series models and is particularly effective in evaluating the impact of stock/crypto price change, marketing campaigns, policy changes, or other interventions. Google Causal Impact package was initially developed for "R" by Google team, later the packege was imported to "python"</font></p>
<p><font size="3">By using this technique, we can isolate the effect of Elon Musk's tweet on Bitcoin's price, controlling for other factors such as market trends, trading volume, and external events. The analysis will provide insights into the direct influence of the tweet on Bitcoin's price movement, allowing us to understand the magnitude and significance of the impact. And help to visualize the what-if scenario for the Bitcoin price.</font></p>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h1 id="2-Model-Implementation"><strong>2 Model Implementation</strong><a class="anchor-link" href="#2-Model-Implementation">¶</a></h1>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="2.1-Libraries,-Dates,-Data">2.1 Libraries, Dates, Data<a class="anchor-link" href="#2.1-Libraries,-Dates,-Data">¶</a></h2><p><font size="3"><ul></ul></font></p>
<li>Import python libraries</li>
<li>Set the data time-frame &amp; stocks</li>
<li>Import the stock datas</li>

</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<script>
  function code_toggle() {
    if (code_shown){
      $('div.input').hide('500');
      $('#toggleButton').val('Show Code')
    } else {
      $('div.input').show('500');
      $('#toggleButton').val('Hide Code')
    }
    code_shown = !code_shown
  } 
  
  $( document ).ready(function(){
    code_shown=false; 
    $('div.input').hide()
  });
</script>
<form action="javascript:code_toggle()"><input id="toggleButton" type="submit" value="Show Code"/></form>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [1]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">import</span> <span class="nn">yfinance</span> <span class="k">as</span> <span class="nn">yf</span>
<span class="kn">from</span> <span class="nn">causalimpact</span> <span class="kn">import</span> <span class="n">CausalImpact</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [2]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">training_start</span> <span class="o">=</span> <span class="s2">"2021-04-12"</span>
<span class="n">training_end</span> <span class="o">=</span> <span class="s2">"2021-05-12"</span>
<span class="n">treatment_start</span> <span class="o">=</span> <span class="s2">"2021-05-13"</span>
<span class="n">treatment_end</span> <span class="o">=</span> <span class="s2">"2021-05-20"</span>
<span class="n">end_stock</span> <span class="o">=</span> <span class="s2">"2021-05-21"</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [3]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">y_stock</span> <span class="o">=</span> <span class="p">[</span><span class="s2">"BTC-USD"</span><span class="p">]</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">yf</span><span class="o">.</span><span class="n">download</span><span class="p">(</span><span class="n">y_stock</span><span class="p">,</span>
                <span class="n">training_start</span><span class="p">,</span>
                <span class="n">end_stock</span><span class="p">,</span>
                <span class="n">interval</span><span class="o">=</span><span class="s2">"1d"</span><span class="p">)</span>
<span class="n">y</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
<pre>[*********************100%***********************]  1 of 1 completed
</pre>
</div>
</div>
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[3]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>Open</th>
<th>High</th>
<th>Low</th>
<th>Close</th>
<th>Adj Close</th>
<th>Volume</th>
</tr>
<tr>
<th>Date</th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<th>2021-04-12</th>
<td>60175.945312</td>
<td>61253.035156</td>
<td>59589.875000</td>
<td>59893.453125</td>
<td>59893.453125</td>
<td>51828688519</td>
</tr>
<tr>
<th>2021-04-13</th>
<td>59890.019531</td>
<td>63742.285156</td>
<td>59869.957031</td>
<td>63503.457031</td>
<td>63503.457031</td>
<td>69983454362</td>
</tr>
<tr>
<th>2021-04-14</th>
<td>63523.753906</td>
<td>64863.097656</td>
<td>61554.796875</td>
<td>63109.695312</td>
<td>63109.695312</td>
<td>77451779687</td>
</tr>
<tr>
<th>2021-04-15</th>
<td>63075.195312</td>
<td>63821.671875</td>
<td>62208.964844</td>
<td>63314.011719</td>
<td>63314.011719</td>
<td>60954381579</td>
</tr>
<tr>
<th>2021-04-16</th>
<td>63258.503906</td>
<td>63594.722656</td>
<td>60222.531250</td>
<td>61572.789062</td>
<td>61572.789062</td>
<td>84293007468</td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [4]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">y</span> <span class="o">=</span> <span class="n">y</span><span class="p">[</span><span class="s2">"Adj Close"</span><span class="p">]</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="s2">"BTC"</span><span class="p">)</span>
<span class="n">y</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[4]:</div>
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>Date
2021-04-12    59893.453125
2021-04-13    63503.457031
Name: BTC, dtype: float64</pre>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [5]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">X_stocks</span> <span class="o">=</span> <span class="p">[</span><span class="s2">"MSFT"</span><span class="p">,</span> <span class="s2">"NVDA"</span><span class="p">,</span> <span class="s2">"AI"</span><span class="p">,</span> <span class="s2">"EA"</span><span class="p">,</span> <span class="s2">"SQ"</span><span class="p">,</span> <span class="s2">"CRSP"</span><span class="p">,</span> <span class="s2">"GOOG"</span><span class="p">,</span> <span class="s2">"WMT"</span><span class="p">]</span>
<span class="n">X</span> <span class="o">=</span> <span class="n">yf</span><span class="o">.</span><span class="n">download</span><span class="p">(</span><span class="n">X_stocks</span><span class="p">,</span>
                <span class="n">training_start</span><span class="p">,</span>
                <span class="n">end_stock</span><span class="p">,</span>
                <span class="n">interval</span><span class="o">=</span><span class="s2">"1d"</span><span class="p">)</span>
<span class="n">X</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
<pre>[*********************100%***********************]  8 of 8 completed
</pre>
</div>
</div>
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[5]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
<thead>
<tr>
<th></th>
<th colspan="8" halign="left">Adj Close</th>
<th colspan="2" halign="left">Close</th>
<th>...</th>
<th colspan="2" halign="left">Open</th>
<th colspan="8" halign="left">Volume</th>
</tr>
<tr>
<th></th>
<th>AI</th>
<th>CRSP</th>
<th>EA</th>
<th>GOOG</th>
<th>MSFT</th>
<th>NVDA</th>
<th>SQ</th>
<th>WMT</th>
<th>AI</th>
<th>CRSP</th>
<th>...</th>
<th>SQ</th>
<th>WMT</th>
<th>AI</th>
<th>CRSP</th>
<th>EA</th>
<th>GOOG</th>
<th>MSFT</th>
<th>NVDA</th>
<th>SQ</th>
<th>WMT</th>
</tr>
<tr>
<th>Date</th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<th>2021-04-12</th>
<td>59.889999</td>
<td>114.389999</td>
<td>139.680893</td>
<td>112.739502</td>
<td>250.827927</td>
<td>151.826202</td>
<td>265.200012</td>
<td>134.979538</td>
<td>59.889999</td>
<td>114.389999</td>
<td>...</td>
<td>258.190002</td>
<td>140.070007</td>
<td>3111900</td>
<td>1080900</td>
<td>2058100</td>
<td>31318000</td>
<td>27148700</td>
<td>86932400</td>
<td>9051300</td>
<td>6241000</td>
</tr>
<tr>
<th>2021-04-13</th>
<td>63.009998</td>
<td>120.879997</td>
<td>140.332626</td>
<td>113.363503</td>
<td>253.356720</td>
<td>156.523056</td>
<td>273.230011</td>
<td>134.564331</td>
<td>63.009998</td>
<td>120.879997</td>
<td>...</td>
<td>267.480011</td>
<td>139.800003</td>
<td>3297300</td>
<td>1352800</td>
<td>2105300</td>
<td>23310000</td>
<td>23837500</td>
<td>67621200</td>
<td>10561700</td>
<td>5799300</td>
</tr>
<tr>
<th>2021-04-14</th>
<td>68.459999</td>
<td>123.110001</td>
<td>139.838898</td>
<td>112.741997</td>
<td>250.514282</td>
<td>152.505051</td>
<td>258.399994</td>
<td>134.516068</td>
<td>68.459999</td>
<td>123.110001</td>
<td>...</td>
<td>274.130005</td>
<td>139.119995</td>
<td>11721300</td>
<td>1914000</td>
<td>1424900</td>
<td>20220000</td>
<td>23070900</td>
<td>38550000</td>
<td>12486400</td>
<td>7308200</td>
</tr>
<tr>
<th>2021-04-15</th>
<td>66.500000</td>
<td>123.849998</td>
<td>140.984390</td>
<td>114.833000</td>
<td>254.346634</td>
<td>161.092590</td>
<td>263.079987</td>
<td>135.327118</td>
<td>66.500000</td>
<td>123.849998</td>
<td>...</td>
<td>262.850006</td>
<td>139.399994</td>
<td>6223600</td>
<td>896300</td>
<td>1654300</td>
<td>27472000</td>
<td>25627500</td>
<td>59848000</td>
<td>8944400</td>
<td>7236800</td>
</tr>
<tr>
<th>2021-04-16</th>
<td>66.790001</td>
<td>118.559998</td>
<td>139.285889</td>
<td>114.888000</td>
<td>255.562057</td>
<td>158.849014</td>
<td>256.100006</td>
<td>135.761581</td>
<td>66.790001</td>
<td>118.559998</td>
<td>...</td>
<td>263.239990</td>
<td>140.889999</td>
<td>2988000</td>
<td>1359200</td>
<td>2468400</td>
<td>22596000</td>
<td>24878600</td>
<td>33520800</td>
<td>8549300</td>
<td>8829500</td>
</tr>
</tbody>
</table>
<p>5 rows × 48 columns</p>
</div>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<blockquote>
<p><font size="3">💡 Here in confounders (X) stocks we are excluding stoks related to crypto currency &amp; Elon Musk for remove selection biases</font></p>
</blockquote>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [6]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">X</span> <span class="o">=</span> <span class="n">X</span><span class="p">[</span><span class="s2">"Adj Close"</span><span class="p">]</span>
<span class="n">X</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[6]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>AI</th>
<th>CRSP</th>
<th>EA</th>
<th>GOOG</th>
<th>MSFT</th>
<th>NVDA</th>
<th>SQ</th>
<th>WMT</th>
</tr>
<tr>
<th>Date</th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<th>2021-04-12</th>
<td>59.889999</td>
<td>114.389999</td>
<td>139.680893</td>
<td>112.739502</td>
<td>250.827927</td>
<td>151.826202</td>
<td>265.200012</td>
<td>134.979538</td>
</tr>
<tr>
<th>2021-04-13</th>
<td>63.009998</td>
<td>120.879997</td>
<td>140.332626</td>
<td>113.363503</td>
<td>253.356720</td>
<td>156.523056</td>
<td>273.230011</td>
<td>134.564331</td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [7]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">X</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="n">X</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">tz_localize</span><span class="p">(</span><span class="kc">None</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [8]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">y</span><span class="p">,</span><span class="n">X</span><span class="p">],</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">dropna</span><span class="p">()</span>
<span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[8]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>BTC</th>
<th>AI</th>
<th>CRSP</th>
<th>EA</th>
<th>GOOG</th>
<th>MSFT</th>
<th>NVDA</th>
<th>SQ</th>
<th>WMT</th>
</tr>
<tr>
<th>Date</th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<th>2021-04-12</th>
<td>59893.453125</td>
<td>59.889999</td>
<td>114.389999</td>
<td>139.680893</td>
<td>112.739502</td>
<td>250.827927</td>
<td>151.826202</td>
<td>265.200012</td>
<td>134.979538</td>
</tr>
<tr>
<th>2021-04-13</th>
<td>63503.457031</td>
<td>63.009998</td>
<td>120.879997</td>
<td>140.332626</td>
<td>113.363503</td>
<td>253.356720</td>
<td>156.523056</td>
<td>273.230011</td>
<td>134.564331</td>
</tr>
<tr>
<th>2021-04-14</th>
<td>63109.695312</td>
<td>68.459999</td>
<td>123.110001</td>
<td>139.838898</td>
<td>112.741997</td>
<td>250.514282</td>
<td>152.505051</td>
<td>258.399994</td>
<td>134.516068</td>
</tr>
<tr>
<th>2021-04-15</th>
<td>63314.011719</td>
<td>66.500000</td>
<td>123.849998</td>
<td>140.984390</td>
<td>114.833000</td>
<td>254.346634</td>
<td>161.092590</td>
<td>263.079987</td>
<td>135.327118</td>
</tr>
<tr>
<th>2021-04-16</th>
<td>61572.789062</td>
<td>66.790001</td>
<td>118.559998</td>
<td>139.285889</td>
<td>114.888000</td>
<td>255.562057</td>
<td>158.849014</td>
<td>256.100006</td>
<td>135.761581</td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="2.2-Analysis">2.2 Analysis<a class="anchor-link" href="#2.2-Analysis">¶</a></h2><p><font size="3"><ul></ul></font></p>
<li>Create training dataframe</li>
<li>Apply "Differencing" technique to make the data stationery</li>
<li>Visualize to check the correlation between "Treatment" and "Confounders"</li>
<li>Dropp least correlated confounders. Here the minimum threshold is 0.4 </li>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [9]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">training_df</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="o">.</span><span class="n">index</span> <span class="o">&lt;=</span> <span class="n">training_end</span><span class="p">]</span>
<span class="n">training_df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[9]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>BTC</th>
<th>AI</th>
<th>CRSP</th>
<th>EA</th>
<th>GOOG</th>
<th>MSFT</th>
<th>NVDA</th>
<th>SQ</th>
<th>WMT</th>
</tr>
<tr>
<th>Date</th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<th>2021-04-12</th>
<td>59893.453125</td>
<td>59.889999</td>
<td>114.389999</td>
<td>139.680893</td>
<td>112.739502</td>
<td>250.827927</td>
<td>151.826202</td>
<td>265.200012</td>
<td>134.979538</td>
</tr>
<tr>
<th>2021-04-13</th>
<td>63503.457031</td>
<td>63.009998</td>
<td>120.879997</td>
<td>140.332626</td>
<td>113.363503</td>
<td>253.356720</td>
<td>156.523056</td>
<td>273.230011</td>
<td>134.564331</td>
</tr>
<tr>
<th>2021-04-14</th>
<td>63109.695312</td>
<td>68.459999</td>
<td>123.110001</td>
<td>139.838898</td>
<td>112.741997</td>
<td>250.514282</td>
<td>152.505051</td>
<td>258.399994</td>
<td>134.516068</td>
</tr>
<tr>
<th>2021-04-15</th>
<td>63314.011719</td>
<td>66.500000</td>
<td>123.849998</td>
<td>140.984390</td>
<td>114.833000</td>
<td>254.346634</td>
<td>161.092590</td>
<td>263.079987</td>
<td>135.327118</td>
</tr>
<tr>
<th>2021-04-16</th>
<td>61572.789062</td>
<td>66.790001</td>
<td>118.559998</td>
<td>139.285889</td>
<td>114.888000</td>
<td>255.562057</td>
<td>158.849014</td>
<td>256.100006</td>
<td>135.761581</td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [10]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">differencing</span> <span class="o">=</span> <span class="n">training_df</span><span class="o">.</span><span class="n">pct_change</span><span class="p">()</span><span class="o">.</span><span class="n">dropna</span><span class="p">()</span>
<span class="n">differencing</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[10]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>BTC</th>
<th>AI</th>
<th>CRSP</th>
<th>EA</th>
<th>GOOG</th>
<th>MSFT</th>
<th>NVDA</th>
<th>SQ</th>
<th>WMT</th>
</tr>
<tr>
<th>Date</th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<th>2021-04-13</th>
<td>0.060274</td>
<td>0.052095</td>
<td>0.056736</td>
<td>0.004666</td>
<td>0.005535</td>
<td>0.010082</td>
<td>0.030936</td>
<td>0.030279</td>
<td>-0.003076</td>
</tr>
<tr>
<th>2021-04-14</th>
<td>-0.006201</td>
<td>0.086494</td>
<td>0.018448</td>
<td>-0.003518</td>
<td>-0.005482</td>
<td>-0.011219</td>
<td>-0.025670</td>
<td>-0.054277</td>
<td>-0.000359</td>
</tr>
<tr>
<th>2021-04-15</th>
<td>0.003237</td>
<td>-0.028630</td>
<td>0.006011</td>
<td>0.008192</td>
<td>0.018547</td>
<td>0.015298</td>
<td>0.056310</td>
<td>0.018111</td>
<td>0.006029</td>
</tr>
<tr>
<th>2021-04-16</th>
<td>-0.027501</td>
<td>0.004361</td>
<td>-0.042713</td>
<td>-0.012047</td>
<td>0.000479</td>
<td>0.004779</td>
<td>-0.013927</td>
<td>-0.026532</td>
<td>0.003210</td>
</tr>
<tr>
<th>2021-04-19</th>
<td>-0.094986</td>
<td>-0.070220</td>
<td>-0.029690</td>
<td>-0.010067</td>
<td>0.002019</td>
<td>-0.007671</td>
<td>-0.034611</td>
<td>-0.042054</td>
<td>-0.006400</td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<blockquote>
<p><font size="3">💡 In 90% of the cases time series datas are non stationary. So we are assuming this dataframe containing non stationary data</font></p>
</blockquote>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [11]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">sns</span><span class="o">.</span><span class="n">heatmap</span><span class="p">(</span><span class="n">data</span><span class="o">=</span><span class="n">differencing</span><span class="o">.</span><span class="n">corr</span><span class="p">(),</span>
            <span class="n">annot</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
            <span class="n">fmt</span><span class="o">=</span><span class="s2">".1g"</span><span class="p">,</span>
            <span class="n">cmap</span><span class="o">=</span><span class="s2">"Blues"</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedImage jp-OutputArea-output" tabindex="0">
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,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"/>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [12]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">final_df</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s2">"EA"</span><span class="p">,</span> <span class="s2">"GOOG"</span><span class="p">,</span> <span class="s2">"WMT"</span><span class="p">])</span>
<span class="n">final_df</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[12]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>BTC</th>
<th>AI</th>
<th>CRSP</th>
<th>MSFT</th>
<th>NVDA</th>
<th>SQ</th>
</tr>
<tr>
<th>Date</th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<th>2021-04-12</th>
<td>59893.453125</td>
<td>59.889999</td>
<td>114.389999</td>
<td>250.827927</td>
<td>151.826202</td>
<td>265.200012</td>
</tr>
<tr>
<th>2021-04-13</th>
<td>63503.457031</td>
<td>63.009998</td>
<td>120.879997</td>
<td>253.356720</td>
<td>156.523056</td>
<td>273.230011</td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="2.3-Model-Creation">2.3 Model Creation<a class="anchor-link" href="#2.3-Model-Creation">¶</a></h2><p><font size="3"><ul></ul></font></p>
<li>Define Pre &amp; Post period</li>
<li>Create the impact model</li>
<li>Summarise the model</li>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [13]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">pre_period</span> <span class="o">=</span> <span class="p">[</span><span class="n">training_start</span><span class="p">,</span><span class="n">training_end</span><span class="p">]</span>
<span class="n">post_period</span> <span class="o">=</span> <span class="p">[</span><span class="n">treatment_start</span><span class="p">,</span> <span class="n">treatment_end</span><span class="p">]</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [14]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">impact</span> <span class="o">=</span> <span class="n">CausalImpact</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">final_df</span><span class="p">,</span>
             <span class="n">pre_period</span> <span class="o">=</span> <span class="n">pre_period</span><span class="p">,</span>
             <span class="n">post_period</span> <span class="o">=</span> <span class="n">post_period</span><span class="p">)</span>

<span class="n">sns</span><span class="o">.</span><span class="n">set_theme</span><span class="p">()</span>

<span class="n">impact</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">23</span><span class="p">,</span><span class="mi">14</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="application/vnd.jupyter.stderr" tabindex="0">
<pre>C:\Users\Saiyan\miniconda3\envs\myenv\Lib\site-packages\statsmodels\tsa\base\tsa_model.py:473: ValueWarning: No frequency information was provided, so inferred frequency B will be used.
  self._init_dates(dates, freq)
C:\Users\Saiyan\miniconda3\envs\myenv\Lib\site-packages\statsmodels\base\optimizer.py:18: FutureWarning: Keyword arguments have been passed to the optimizer that have no effect. The list of allowed keyword arguments for method lbfgs is: m, pgtol, factr, maxfun, epsilon, approx_grad, bounds, loglike_and_score, iprint. The list of unsupported keyword arguments passed include: standardize, nseasons. After release 0.14, this will raise.
  warnings.warn(
C:\Users\Saiyan\miniconda3\envs\myenv\Lib\site-packages\statsmodels\tsa\statespace\representation.py:374: FutureWarning: Unknown keyword arguments: dict_keys(['alpha']).Passing unknown keyword arguments will raise a TypeError beginning in version 0.15.
  warnings.warn(msg, FutureWarning)
C:\Users\Saiyan\miniconda3\envs\myenv\Lib\site-packages\statsmodels\tsa\base\tsa_model.py:473: ValueWarning: No frequency information was provided, so inferred frequency B will be used.
  self._init_dates(dates, freq)
</pre>
</div>
</div>
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedImage jp-OutputArea-output" tabindex="0">
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,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sidml+yK2SW7YnbJrpjd8uL+JbtidsmumF2yK2aX7KyW8vvSl74C7373+wAAN998I1544bkqt4jKye7ZtXfryVYcDomWFj8cDsaO7IXZJbtidsmumF2yK2a3vLh/ya6YXbIrZpfyhJDYvv1EbN9+IoSwfh6YXbKzWszvO9/5j3jZy16BTCaDD33oKoyPj1e7SVQGtZBd+7aciIiIiIiIiIiIiMrK4/Hg/vu/j/vv/z48Hk+1m0NENiOlxL/+66ewbt16DA4O4LrrPohcLlftZhHNwoIpERERERERERERERERlUUwGMSnP/15eL0+/PnPj+Cuu+6odpOIZmHBlIiIiIiIiIiIiIiIiMqmp2cLPvGJWwAA9977Dfz85z+pcouICrFgShWllKp2E4iWhdklu2J2ya6YXbIrZre8uH/JrphdsitmlwAgmUzi1a++AK9+9QVIJpPVbk5RmF2ys1rO76te9de4/PIrAQA33ngD9ux5scotolKye3aFsvsrqCBdNzA+Hq92M4iIiIiIiIiIiIgqIplMYMeO0wEADz/8JLxeX5VbRER2pus63vveK/HIIw9h7dp1uO++76GhobHazbKUTCaDr3zlizAMA1dd9cFqN8e2Wlr80LTix41yhCkRERERERERERERERGVnaZpuPXWO7Bq1WocOdKLf/mXa2EYRrWbZRnDw0O44oq34p57vozvfOc+ZLPZajepbrBgShWjaRJNTb4lVfSJrIDZJbtidsmumF2yK2a3vLh/ya6YXbIrZpfsitklO6uX/DY1NePTn/4c3G43/vSnP+DLX/58tZtkCc8++zTe8pY34Nlnn0Ew2IDbbvssnE5ntZtVlFrIbllbfvDgQZx22ml48MEHJ7+2a9cuXHbZZTj11FNxwQUX4N577y34HsMwcNddd+H888/HqaeeiiuvvBJHjhwpeE4ptkGVJwTgdGoQototIVoaZpfsitklu2J2ya6Y3fLi/iW7YnbJrphdsitml+ysnvJ73HHb8bGPfRIA8JWvfBG/+91vqtyi6vrhD3+Ad7zjrRgZGcHmzVtw333fw3nnvaTazSpaLWS3bAXTbDaLa665BolEYvJroVAIl19+OdatW4cf/OAHeO9734vbb78dP/jBDyaf88UvfhH3338/PvnJT+KBBx6AYRi44oorkMlkSrYNIiIiIiIiIiIiIiIiqp7X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bVr5PsxmM/iHf7gMzz33LLZtOw7f/vZ34PF4bX0csX//Xrz//e/BkSO98Hq9uOmmW3Dhha+uqT5ivvO1avYRLS3+We1dSElHmN5+++1IpQqrthdeeCGuuuoqvO51r8OPfvQjPPDAA9B1HZpmVoMfeeQRbNy4Ea2trQgGgwgEAnj00Ucni52RSAQ7d+7EZZddBgA466yzVryNlci/uUt9zAzi3LVppRRyubkfW2y70wM1e7vLb+9Ktjv9l2G+x+f7/uVudyX7cOH3xnr7cKHtLtam6uzD6uS7tPtwqlMt33tjvX1oj/emuO3Wex8x/d4o6+3DWugjKrFd6+3Dcr43+YPgmccM7COK225t9bP26yPy3z/X9tlHrHy7wPz71375Zh9R3Hatl++l7sPpF394HFHe7dZWvrkPi9uu9fJdi+cauZyO/fv3zWqH1fuI/M2X0z9fznYXaxP7iMW3u1ib2EdMbTf/+FzHvFbtI5az3YXa5HS6cPvtd+HNb74EL764Gx/72PW45ZbbJouDdsv3r371S9xww7VIJBLo7l6FO+/8IrZtO+5Ym2qrjzDbZa3ztaUovrRahM7OTqxfv77gAwBaW1vR2dmJSy65BLFYDNdffz327duHBx98EN/85jfxrne9C4C57uhll12G22+/Hb/5zW+we/duXH311ejq6sKFF14IACXZBhEREREREREREREREVlPZ2cXPvWpz0DTNPzsZ/+D++67t9pNWjLDMPClL30OH/zg+5BIJHDWWefg/vt/MFksJesp6QjTxbS2tuKee+7BzTffjIsvvhjt7e249tprcfHFF08+56qrrkIul8MNN9yAVCqFs846C1/72tfgdDpLtg0iIiIiIiIiIiIiIiKypjPPPBsf/OBHcNttt+Azn/kUtm07DmeddU61m1WUWCyGG264Fr///W8BAJde+jZcffWHWaOyuJKuYVrrpi8ATEsnpUAg4EEsllp0GjMiK2F2ya6YXbIrZpfsitktL+5fsitml+yK2aW8ZDKBHTtOBwA8/PCT8Hp9VW7RwphdsjPmt5BSCtdffy1++tMfo7m5Bf/5nz9AV1d3tZu1oMOHD+Lqq9+HAwf2w+Vy4frrb8Tf/u3rq92ssrNidpe6hikLpkvAgikRERERERERERHVE7sVTImotiSTSbz97ZfixRd34YQTTsLXv/5tuN3uajdrTn/60//iuus+hFgsio6OTtxxx+dw0kknV7tZdWupBdOSrmFKtJj8wsxEdsPskl0xu2RXzC7ZFbNbXty/ZFfMLtkVs0t2xeySnTG/hbxeLz796c+hsbERL7zwHG699ZOw2jhApRS+/vWv4P3vfxdisShOOeU03H//9+uuWGr37LJgShXjcEi0tQXgcDB2ZC/MLtkVs0t2xeySXTG75cX9S3bF7JJdMbs0RaC7exW6u1cBsP7FcGaX7Iz5ndvq1Wvwb/92B6SU+K//+j5+8IPvVLtJk5LJBK677kO4665PQymF17/+jfjqV/8DbW3t1W5aRdVCdu3bciIiIiIiIiIiIiIqK6/Xi5/97Lf42c9+C6/XW+3mEFGdOu+8l+B97/sAAODWW2/GM888Vd0GAejrO4r/9/8uxS9+8VM4HA5cf/2N+NjHPgmXy1XtptEysGBKRERERERERERERERElnb55Vfila+8ELlcFtdc808YHR2pWlsee+wRvOUtb8CePbvR0tKKr3zlm3jjG/++au2hlWPBlIiIiIiIiIiIiIiIiCxNCIGbbroFmzb1YGRkGB/+8AeQzWYq2galFO6//168+93vwMTEBLZvPwH33/99nH76mRVtB5UeC6ZERERERERERERENKdUKoVLL30DLr30DUilUtVuDhHVOb8/gM985nMIBAJ46qkn8OlPf6piPzudTuPjH/8XfOpTt0DXdbzmNa/D179+H7q6uivWBiofoZRS1W6EXei6gfHxeLWbYWtCAEwc2RGzS3bF7JJdMbtkV8xueXH/kl0xu2RXzC4BQDKZwI4dpwMAHn74SXi9viq3aHHMLtkZ81uc3//+t/jAB/4RAPCv//rvuOiivy3rzxsaGsKHPvR+PP/8s5BS4uqrP4zLLns7hBBl/bl2YrXstrT4oWnFjxvlCFOqKCv9shAtBbNLdsXskl0xu2RXzG55cf+SXTG7ZFfMLtkVs0t2xvwW5+UvvwDvfKdZMP3kJz+GXbteKNvPevrpJ3HppZfg+eefRUNDI774xXvw1rdezmLpDHbPLgumVDGaJtDY6IWmsRMhe2F2ya6YXbIrZpfsitktL+5fsitml+yK2SW7YnbJzpjfpXn3u9+H889/GdLpND74wfcjFAqV/Gf84AffxRVX/D+MjY2ip2cL7r//+zj33PNK/nPsrhayy4IpVYwQAi6Xg3ddkO0wu2RXzC7ZFbNLdsXslhf3L9kVs0t2xeySXTG7ZGfM79JIKXHzzbdh7dr1GBjox3XXfQi5XK4k285mM7j55pvwyU9+DLlcFq985YW4994HsGbN2pJsv9bUQnZZMCUiIiIiIiIiIiIiIiLbaWhowGc+8zl4vT48+uhD+Pzn71zxNsfGRvGud/0Dvve9/4QQAu997wdw222fhc/nX3mDybJYMCUiIiIiIiIiIiIiIiJb6unZihtvvBkA8M1v3oNf/vLny97Wzp3P49JL34Ann3wcgUAAn/3sF3Hlle+29chJKg4LpkREREREREREREQ0r+bmZjQ3N1e7GURE8/qrv3o13va2fwAAfPzj/4J9+/YseRs/+cmPcfnlb8HQ0CA2bNiIb33ru3jpS19R6qaSRQmllKp2I+xC1w2Mj8er3QzbEkLA7XYgnc6BsSM7YXbJrphdsitml+yK2S0v7l+yK2aX7IrZJbtidsnOmN+VyeVyeO97r8Sjjz6MtWvX4777voeGhoaivu+zn70d3/rWNwEA55//Mtxyy+0IBoNlbnHtsGJ2W1r80LTix42yYLoELJgSERERERERERERERFZUygUwqWXXoKBgX689KUvx513fhFSzl80C4cn8JGPfBCPPPIQAOCKK96N97zn/dA0rVJNpjJZasGUU/JSxQgBuN0OcKpvshtml+yK2SW7YnbJrpjd8uL+JbtidsmumF2yK2aX7Iz5Xbnm5mbcccddcLlc+N///T3uvvsL8z53794X8Za3vBGPPPIQPB4vbrvtTrzvfR9gsXQZaiG7LJhSxWiaREODd0kVfSIrYHbJrphdsitml+yK2S0v7l+yK2aX7IrZpbxUKoV3vOOteMc73opUKlXt5iyK2SU7Y35LY/v2E3HDDTcBAO6++wv4wx9+O+s5v/71L/C2t70ZR48ewerVa3DvvQ/gVa/660o3tWbUQnbt23IiIiIiIiIiIiIiKiulDDzxxGN44onHoJRR7eYQERXlda+7GG9606UAgOuvvxaHDx8EABiGgc9//k5cc80/IZlM4JxzduC++76HrVu3VbO5ZAEsmBIREREREREREREREVFNueaa63DqqacjFovh6qvfj6GhIXzgA/+Ie+75MgDgssv+H77wha+iqam5yi0lK3BUuwFEREREREREREREREREpeR0unD77Z/Fm9/8ehw4sA8XXfRKZLNZuFwufPSjn8BrX/t31W4iWQhHmFLFKKWQzepQSlW7KURLwuySXTG7ZFfMLtkVs1te3L9kV8wu2RWzS3bF7JKdMb+l19bWjttvvwsOhxPZbBadnV34xjfuY7G0xGohu0LZufUVpusGxsfj1W4GERERERERERERUUUkkwns2HE6AODhh5+E1+urcouIiJbuj3/8Ax566E+44op3obW1rdrNoQpoafFD04ofN8opeYmIiIiIiIiIiIiIiKhmnX/+y3D++S+rdjPIwjglL1WMwyHR3h6Ew8HYkb0wu2RXzC7ZFbNLdsXslhf3L9kVs0t2xezSdB6PFx6Pt9rNKAqzS3bG/JJd1UJ2OcKUiIiIiIiIiIiIiObk9frwyCNPVbsZREREZWXfUi8RERERERERERERERER0QqxYEpEREREREREREREREREdYsFUyIiIiIiIiIiIiKaUzqdxvve9y68733vQjqdrnZziIiIykIopVS1G2EXum5gfDxe7WbYmpQChsHIkf0wu2RXzC7ZFbNLdsXslhf3L9kVs0t2xewSACSTCezYcToA4OGHn4TX66tyixbH7JKdMb9kV1bLbkuLH5pW/LhRjjClirLSLwvRUjC7ZFfMLtkVs0t2xeyWF/cv2RWzS3bF7JJdMbtkZ8wv2ZXds8uCKVWMlALBoAdSimo3hWhJmF2yK2aX7IrZJbtidsuL+5fsitklu2J2ya6YXbIz5pfsqhayy4IpVYyUAh6P09a/MFSfmF2yK2aX7IrZJbtidsuL+5fsitklu2J2ya6YXbIz5pfsqhayy4IpEREREREREREREREREdUtFkyJiIiIiIiIiIiIiIiIqG4JpZS9V2GtIKWU7RetrTZNk9B1o9rNIFoyZpfsitklu2J2ya6Y3fLi/iW7YnbJrphdAgClDPT19QEAVq9eDSGsPwaH2SU7Y37JrqyWXSkFhCh+imAWTImIiIiIiIiIiIiIiIiobln/diAiIiIiIiIiIiIiIiIiojJhwZSIiIiIiIiIiIiIiIiI6hYLpkRERERERERERERERERUt1gwJSIiIiIiIiIiIiIiIqK6xYIpEREREREREREREREREdUtFkyJiIiIiIiIiIiIiIiIqG6xYEpEREREREREREREREREdYsFUyIiIiIiIiIiIiIiIiKqWyyYEhEREREREREREREREVHdYsGUiIiIiIiIiIiIiIiIiOoWC6ZEREREREREREREREREVLdYMCUiIiIiIiIiIiIiIiKiusWCKRERERERERERERERERHVLRZMiYiIiIiIiIiIiIiIiKhusWBKRERERERERERERERERHWLBVMiIiIiIiIiIiIiIiIiqlssmBIRERERERERERERERFR3WLBlIiIiIiIiIiIiIiIiIjqFgumRERERERERERERERERFS3WDAlIiIiIiIiIiIiIiIiorrFgikRERERERERERERERER1S0WTImIiIiIiIiIiIiIiIiobrFgSkRERERERERERERERER1iwVTIiIiIiIiIiIiIiIiIqpbLJgSERERERERERERERERUd1iwZSIiIiIiIiIiIiIiIiI6hYLpkRERERERERERERERERUt1gwJSIiIiIiIiIiIiIiIqK6xYIpEREREREREREREREREdUtFkyJiIiIiIiIiIiIiIiIqG6xYEpEREREREREREREREREdYsFUyIiIiIiIiIiIiIiIiKqWyyYEhEREREREREREREREVHdYsGUiIiIiIiIiIiIiIiIiOoWC6ZEREREREREREREREREVLdYMCUiIiIiIiIiIiIiIiKiusWCKRERERERERERERERERHVLRZMiYiIiIiIiIiIiIiIiKhusWBKRERERERERERERERERHWLBVMiIiIiIiIiIiIiIiIiqlssmBIRERERERERERERERFR3WLBlIiIiIiIiIiIiIiIiIjqFgumRERERERERERERERERFS3WDAlIiIiIiIiIiIiIiIiorrFgikRERERERERERERERER1S0WTImIiIiIiIiIiIiIiIiobrFgSkRERERERERERERERER1iwVTIiIiIiIiIiIiIiIiIqpbLJgSERERERERERERERERUd1iwZSIiIiIiIiIiIiIiIiI6hYLpkRERERERERERERERERUt1gwJSIiIiIiIiIiIiIiIqK6xYIpEREREREREREREREREdUtFkyJiIiIiIiIiIiIiIiIqG6xYEpEREREREREREREREREdYsFUyIiIiIiIiIiIiIiIiKqWyyYEhEREREREREREREREVHdYsGUiIiIiIiIiIiIiIiIiOoWC6ZEREREREREREREREREVLdYMCUiIiIiIiIiIiIiIiKiusWCKRERERERERERERERERHVLRZMiYiIiIiIiIiIiIiIiKhuOardADtRSsEwVLWbYWtCCCjFfUj2w+ySXTG7ZFfMLtkVs1te3L9kV8wu2RWzS3bF7JKdMb9kV1bLrpQCQoiin8+C6RIYhsL4eLzazbAth0OiqcmHcDiJXM6odnOIisbskl0xu2RXzC7ZFbNbXty/ZFfMLtkVs0t5yWQSr3/9awAADz74E3i93iq3aGHMLtkZ80t2ZcXstrT4oWnFF0yFslK51+J03WDBlIiIiIiIiIiIiOpGMpnAjh2nAwAefvhJeL2+KreIiIhocWbBtPiVSbmGKRERERERERERERERERHVLRZMqWI0zRySvZSKPpEVMLtkV8wu2RWzS3bF7JYX9y/ZFbNLdsXskl0xu2RnzC/ZVS1k174tJ9sRAnA6NSxhjV0iS2B2ya6YXbIrZpfsitktL+5fsitml+yK2SW7YnbJzphfsqtayC4LpkRERERERERERERERERUtxzl/gF33303/vSnP+Fb3/rW5Nd27dqFm2++Gc8//zxaWlrw9re/HW9729smHzcMA5///Ofxve99D9FoFGeddRY+9rGPYe3atSXdBhEREREREREREREREVmLYRjQ9Vy1m0FFMgyBVEpDJpOGrquy/zxNc0DK0o4JLWvB9L777sOdd96JM888c/JroVAIl19+OS644ALcdNNNePrpp3HTTTfB7/fjkksuAQB88YtfxP33349bb70VXV1duO2223DFFVfgxz/+MVwuV0m2QURERERERERERESLEdi0qWfy/0RE5aSUQiQyjmQyVu2m0BKNjkoYhlGxn+f1BtDQ0AJRonmAhVKq5KXeoaEhfPzjH8ejjz6Krq4utLW1TY4wvfvuu/Htb38bv/vd7+BwmPXaT3/60/jFL36BX/ziF8hkMjj33HNxzTXX4NJLLwUARCIRnH/++bj55ptx0UUXlWQby6HrBsbH4yvdPXXLnMPagWw2h9Knjqh8mF2yK2aX7IrZJbtidsuL+5fsitklu2J2ya6YXbIz5hcIh8eQTMYQCDTD5XKXrBhG5ScEKpJbpRQymTRisRC83gAaG1vnfF5Lix+aVvwo1LKMMH3hhRfgdDrx3//93/jCF76Avr6+yccef/xxnH322ZOFTgA499xzcffdd2N0dBT9/f2Ix+PYsWPH5OMNDQ3Yvn07HnvsMVx0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zsBJJ52Cm2/+FK6//lp89av/gU2bNi+7rV/96r3453/+EDo6OvFP//QhCCHwL//y4cnPm5qa8ZWvfBG//vUvcPXV12L9+g14+ukncfvttyIWi+H1r38jotEo3vveK7F5cw8++9kvQ0qB2267BR/96HW44467EIvFcNddd+BHP/o5Ghoa8eUvfx779+/Fbbd9FsFgED/+8Q/xsY/9Mx544L/Q3b1q2a+lWBUfYUr1y+GQaG72IxSKl2QB3pWQUiCbFejvlxgeBhIJNe9ixNGowuHDAlu2SHA90/pkpewSLQWzS3bF7JJdMbvlxf1LdsXskl0xuzRFTLtQbf2lq5hdsjPmd37v+fQf5n3s5M2t+MAbT5n8/J8+90dksnPvv21rm/CRt5w++fmHv/QQYsnsnM/d0BXEx95+1jJbDHzrW9/AAw98GwCg6zoymQw2bNiIT3ziVnR1deHQoYP44x//gH//98/gvPPMAuo73vEu7Nu3F9/61tfnLZi++tUX4a/+6m8AAG972z/g/vu/heeeewannno6gsEGAEBTUzPcbk9RbZvuDW/4e7zrXe9Fc3MzHA4H3G735JTA0z9PJpP4znfux4033jzZ9vXr12FwcAD3338vXv/6N+I3v/klEok4brzxFjQ0mO36yEc+il//+hcQQk6ug5rffn//Ufh8fqxatRrBYBBXXPHugtdUbiyYUl0RQsAwBAYHJQYHgXhcwVjk745SwPi4Qn+/xJo1ivPHExERERERERFR3fB6vfjZz35b7WYQEdnO3/3dJXjDG/4eACClREND42SREAD2798HADj55FMLvu+0007Hl7/8hXm3u379hoLPA4EAstm5i77FtG26YDBY1PcfOnQAmUwaN910PaSUk1/PF4bT6RQOHNiHtWvXTRZLAaCnZwt6erbMuc23vOX/4SMfuRoXXfRKbN9+Is4++1y86lV/XbDPyokFU6oLQgBKSYyMmIXSWExBX8IMu7kcMDAA+P0ampq4nikRERERERERERERUaV86YMvm/exafU6AMBn33/+vM8VMwbK3/ae84p+7lIFgw1Ys2btAs+Yu85gGAYcjvnLdy6Xa/aWllizWLxtC8sPLPvEJ26dLOBqmoCum193Ol0Lvoa5nHjiyXjwwZ/gsccexeOP/xk/+9n/4JvfvAd33PE5nHnm2ctua7Hk4k8hsi8hACEk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mWeepZ///Ke699679dhjj+qjH/3glCspq1ve/vjHP9K+fXt199136T3veZfK5bKKxcoWv9W+PvroIxobG5u0nZe85GX67W9/pd///t5x1yV95StfrbGxMX3wg1fr4Ycf0sMPP6T3ve//1f3336f16yeusD3a0NCg+vsPTfgzPDw0q3F40Yteora2dl199VX6/e9/pyeeeFx///fv1803/1YbNpwiSXr96/9UP/vZT/Qf//Hv2r17l37yk5v0n//5TT3jGc8+/NhT2rt3jw4c2D+rn3miWGGKBcVJCVxFduEqsgtXkV24iuzWF+MLV5FduIrswhWeZzQ25mnnTqPBQatZXvoPh5XLleu25nLSyIjk+1I0ahSLGaXTlRWoLS2VFai+X1l9apkg6oahPTGJREKf+tT/1b/927/oK1+5Ufv371U8ntCpp56mT37y8zr77HNqx77rXe/RP/zDNXrrW/9M3d09evOb/1wHDx44oZ//1re+XSMjw3rnO9+mdLpVf/Inb9Do6OSFzs2bz9Q73nGlvva1r+oLX/isenp69LznvVDLl/fqgQfukyS1t3fokkters985hPatWunnvWs505o5+yzz1F39zJ1dnZp9eo1tdtXrerTpz71eX3uc5/S2952mXzf11lnna1PfOJz6uzsnPZxvPnNb5z09vXrT9a//MvXZxyHdDqtT33q/+rTn/4nvetdlysIQm3adJr+8R8/rXXr1kuSnvGMZ+mqq96rf/3XG/XpT39cvb0rdcUVV+riiy+RJL3iFX+kD3/4/XrjG1+r73//p/L9+d/G+WjGMrPNWhCEGhjIzHwgJuX7Rul0QmNjeQUBsYM7yC5cRXbhKrILV5Hd+mJ84SqyC1eRXVTlcllt3XquJGnbtjuUTKYa3KNjedq3z9PevVI2a+V5RslkTLlcUWFIdueD51W28Y1GjVpapLY2KZWSUqlQ0ahVGFJAnS+NmntLpaL6+/equ3ulotETW2GJpcv3TVPltqurRb4/+412WWGKBWOMUSwWObzvNP+Bwh1kF64iu3AV2YWryG59Mb5wFdmFq8gump3nGWUyR1aVlsuV242RolFf+Xxj+7eYhKFUKEiFgtXYmHTwoBSJSNGop1SqUkBtaZGSyVDxeKV4SrH6+DD3wmWu55aCKQAAAAAAAADAIZVVpbt3V1aVYmGFoVQsSsWiVSYj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4tj3wswRcz92sbzXqLymVfu3MUYjY0Y7njDaezCvkWxey1LJWhFyx4G9uvWxh1U8nH8jIy9ypOi4oiWt5OFrysWMVVShWuJxpeIJpWMJtac7jhRFoxEVCpV+dCUTevrJp4zrczx+5LVcLFbmCN83ikatCoXcuIJpPJ5SxPfV6idVKhVULlVe912JuLr6Vk9o11pbWZEalMb14exVfcqXyyocLrCWrFHhcJE1YlQ79uDQQT1+YPf458M/Uti9aNNmrWrvlFS55uojB/ZqZUenVrR1KhaJKBo98rovl6efT+Z2bFye58/52CCY/nUficTk+5HjOLascnn6173vR+d8bBgGKpWmft37fkSRSOw4jg1VKk3/up/tsZ7nKxqtvG6stSoWc7X8jo3lNDJiNTBgtGKFtHKlV5tXm22OmN2xnEdIi/88Yra/h1yo8whrk5K4hqn27dsnSVq5cuW425cvX167b652796tP/iDP5j0vmc849n63Oe+UPv6oouePu5k4mjnn3+h/vmfv6IgCGWt9JKXPE+Dg4OTHrt585n6+te/Vfv6j/7opdqzZ/ekx27YcIq+850fKgisrLV6/etfo0cfnXyv/pUrV+mnP/2f2teXXfYG/f73v5v02M7OTv3qV7coDK3C0Oryy9+s22+/bdJjE4mkbrvtblW39X/HO67Qr371i0mPlaTf/e6hWrvvfe9V+tnPfjzlsbfccpdaWioT0fvf/3595zv/OeWxv/zlzero6FQYWl133TX6+te/OuWxN930c61eXbmu7T/908f1z//8xSmP/fa3f6ANG05REFjdcMPn9fnPf3rKY7/61W/oKU85W5L05S9/Rddf/7Epj/3Sl/5FF1zwVAVBqG9+8+u65poPTXnspz71eT3nOc+VJH3/+z/Q1Ve/Z8pj/+EfPq4XvvDFCoJQ//VfP9NVV71zymM/+MGP6lWv+iNJ0m9+8xu9/e1vnfLY9773fXrta9+gcjnUHXfcrje/+Y1THnvlle/WZZe9WZJ0//2/02tf++opj/2Lv7hcb3/7FSqXQz366A69+tUvm/LYN77xf+nd76489t279+hFL7poymP/5E9ep6uv/oDK5VCDg4O66KLJX8eS9LKXvUIf/Wjlucpms9q69dwpj33hCy/W9dd/ovZanu5Y5ogK5ogjFmKO+O53v6O//du/mfJY5ogK5oiK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hoelfN6q2PyXxXWO73l6ximnqzPVoqFsRn0dXY3u0oyyWaudO41OO82TMWGju4Mlqq4rTN/3vvfpPe95z4Tbt23bple96lU6++yzdfHFF+sHP/jBuPsLhYL+7u/+Tlu3btU555yjd73rXRoYGJj3NrCwyuVQBw+OqlxmwoNbyC5cRXbhKrILV5Hd+mJ84SqyC1eRXbiK7DYfayvXPfW8UO3tZa1bV1l5etppRiedZNTebhSPi9WFqhSZh4ayCoIT20bXGKMz+07S0085XebwwBbLZQ1lM/PRzboYGrLaudOT7xMEFy2GubcuBdMwDHX99dfra1/72oT7duzYobe+9a165jOfqW9961t6zWteo6uuukrbtm2rHfOBD3xAv/71r/XJT35SN954ox599FFdccUV89oGAAAAAAAAAABYWGFoZUyo1tay1q49Ujxdv96os9MokTDyuJjgvKgWS0Mb6r8fuEffvetW7Ro81OBeTS4MpYMHpYEBv9ZvYCHN+5a8O3bs0Hvf+1498cQTWrVq1YT7b7zxRm3atElXXnmlJGnDhg267777dMMNN2jr1q3av3+/vv3tb+tzn/uczj//fEnS9ddfr4svvlh33nmnzjnnnHlpAwvP943S6YTGxvIn/AkZYCGRXbiK7MJVZBeuIrv1xfjCVWQXriK7cBXZdUsYWklW6XSotjajvj6jsTGj0VGjwUEpm5WKRasgaHRPF4bnGSWTMeVyxcNjMz/KQaBSEKgUlPWT392pp568SZtXrWm6wmQ+X9mat6XFUySyRJ70RWIxzL3z/jmNm2++WRs2bND3v/99rV69esL9t99+u7Zu3Trutqc97Wnavn27rLXavn177baq9evXq7e3V7fddtu8tYGFZ4xRLBZpukkYmAnZhavILlxFduEqsltfjC9cRXbhKrKLqlgsrq985Rv6yle+oVgs3ujuzIjsuisMrcIwVCoVaMWKQJs3h9q82WrDBqOeHqNUyigy70vAmosxUjTqz/v2xLFIVC8+6zxtXL5SVtLNjz6o3+54QGHYfNunjoxUiqYey4ydshjm3nmfXl7/+tdPe/++ffu0YsWKcbctX75cuVxOg4OD2r9/vzo7OxWPxyccs2/fvnlr43hFIuNfpJVJ3E56n6Tafs2+byYEJQhCWVsJ0rH7cltra1X46dr1PCPPO7ZdK2utjJF8f/z3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SdLPP/+sq666SkcddZSOOOIIjR49WnfccYd27twZsKxly5ZJkgYPHlzvNWh//PFHvf/++zr11FP1+uuvq23btvUPWg3l5eV64okndPzxx+uII47Q0KFDdemll+qbb76p9fHGGD322GMaNWqU+vTpo9NPP13z5s0Letw333yjiy++WEceeaR69+6tY489Vvfff7+KioqCHrt48WJNnDhRAwcOVL9+/fT73/8+qE3feP/tb3/TnXfeqX79+mno0KF6++23lZubqwceeKDWdRs0aJCOP/54/235+fm69957ddxxx6lv377q27evTjjhBD3xxBOqrKyU9Ot12CTp+++/V25urh555BFJtV/fLZT9qvo6PPLII3r//fd1+umnq0+fPsrLy9PUqVOVn58f8PhQMlObK6+8Urm5udq0aVPA7VdccYVyc3M1d+7cgNt918FcvHix/7ZVq1bpsssu81/v7+STT9acOXNkjAl4rm9+eOKJJzRo0CANGjQo4Bp777zzjs466yz1799fAwYM0B//+EctWbJkv/332d/+1JA+jh49Wueff75++OEHTZo0Sf3799fQoUN12223yePxaPv27br66qs1cOBA5eXl6frrrw/aFpL09ttv66yzzlK/fv3Uv39/nXXWWXrrrbf891dUVGjo0KEaMWJEUB8k6bbbblNubm7AtR1DXQdJWrBggX7/+9+rX79+GjVqlB5//HFZlhXSWEpSaWmpZs6cqdGjR6tPnz4688wztXz58qDH1XYdQp+6rgnYkPWo7rXXXtPRRx8tSXr//feDrsf69ddf+9vt3bu3jj/+eD3xxBP+Qld9iouL9fe//10nn3yy+vfvr969e+uYY47RX//614DrRPv2zQcffFDvvPOOTjjhBPXp00fHHnusnn322aBxzs3N1fXXX68lS5b49+PRo0frwQcfVFlZWdBj69pHQp07LrjgAuXm5uqFF14IuP2NN95Qbm6uJk2aJGNMra9LN998s3r27Kk9e/Zo6tSpGjZsmPr3769JkyZp48aNKi8v13333acjjzxSAwYM0IQJE/T9998HjeWHH36oCy+8UMOGDVOvXr00bNgwXXbZZQFZmDBhQtDrZXUHMh9IVfPxpZdeqiFDhmjw4MH605/+pL179wY9rvo1TH15rv7a6rsuem2v7Q3Nf0Pm6cbuJ1Lt1zAdPXq0JkyYoHXr1umSSy7RwIED1b9/f02ePDloG1Z/7Wroa1yo+1Ftao5Zfdetr/6+J5Tl7u89a13zVX1zuY+vrc8//1wTJkxQ//79NXjwYF199dXavHnzftcbAAAAAAAAdWvyU/ImJSVp+vTpmjBhgqZNm6YhQ4YoPT29zsdblqVrrrlG8+bNU6dOnXTaaaeppKRE77//viZNmqRbb71Vf/jDH/zXQHvhhRdUVlamiy66yH8auMLCQp1zzjlas2aN8vLydMwxx2jz5s16+eWXtWjRIv3rX/9STk6OpF+vpdaiRYumXnW/a665RsnJyTr++ONVXFysN954Q1dffbWSkpL8X8JL0k033aT//ve/Ouyww3TWWWfJ4/H4v7h98sknlZeXV+cypkyZomXLlmnZsmU6/vjj1a1bt/2eFm/Pnj26+uqrdfTRRysjI0OHHnqo8vPzdf7552vPnj069thjlZOTox9++EFz5szR0qVL9b///U+JiYmaMmWK/vOf/2jLli2aPHlyvdeh69y5s/773/8GfSkdqrKyMk2cOFErV66U2+3W2WefrV27dmnBggVatGiRHnrooaDT2T3zzDMqLCzUSSedJKfTqfnz5+uqq67SHXfcobPPPluStGHDBk2cOFFOp1Njx45VZmamvvjiC/3jH//QN998E/Cl/9y5c3XrrbcqKytLxx9/vNLS0vT+++/rqquu0jXXXKNLLrkkYPkvv/yyJOnss8/W+vXr1bdvX2VmZmrevHm67rrrAh778ccfq7CwUBdeeKGkqvyeeeaZ2rp1q0aPHq0xY8YoPz9f7733nh588EHt27dPN910kzp27KgpU6bo0Ucf1UEHHaSzzjor6Dq7PqHuV9V9+OGHeuyxx/Tb3/5WQ4cO1aeffqq5c+dq7dq1+te//iVJIWemNiNHjtT8+fO1ZMkSderUSVJVodtXMFixYkXA6ScXLVqkjIwMDRo0SJK0cOFCTZkyRYmJiTrmmGOUlZWlRYsW6Y477tB3332n6dOnByxv0aJFeu+99zR+/Hjt2rVLffv2lST97W9/02OPPaaOHTtq/PjxcjgcmjdvniZOnKh77rlHJ598cq39r662/akxfdy8ebPOPvts9evXT2eddZYWLVqkf//739q7d6++/fZbHXTQQTrzzDP1xRdf6I033pDH4wm4BuO9996rZ599VtnZ2TrxxBMlSR999JGuvfZafffdd7rhhhuUmJio4447TnPmzNHKlSv94ylJlZWVevfdd9WlSxf16dOnweswd+5cTZ06VW3atNG4cePk8Xj0xBNPhDy/WpalyZMna9myZerTp49+97vf6ZtvvtEFF1xwwNdsbOi2qK5Hjx4677zz9M9//lNdu3bVCSec4J9fFyxYoKuuukpOp1NjxozRQQcdpCVLlujBBx/UokWL9NxzzykpKanOtisrKzVx4kR9/fXXOvLII3XkkUequLhYH3zwgZ555hlt3rxZDz/8cMBzFi1apCeffFK//e1vNXz4cC1cuFD33nuv1qxZo3vuuSfgsT/88IMuvPBC9e/fX3/4wx+0ZMkSPfHEE/ryyy/13HPPyel0BrRbcx9pyNwxffp0nXTSSfrb3/6msWPHqm3bttqxY4fuvPNOtWzZUjNmzJDD4ahzLIwxOu+882RZlsaPH681a9bok08+0cUXX6xDDjlEa9as0dixY7Vz507NmzdPF110kebPn+/Pxosvvqjp06erc+fOOvHEE5WYmKhvvvlG77//vpYsWaJ58+YpJydH48ePl6SA10ufA50PVq9erT/84Q8qLy/Xscceq8zMTL3//vtatGjRfp/nm8+rv7YmJyeroKBA33//fdBre/VCYX0aMk8fyH6yP1u3btVZZ52lLl266Mwzz9SGDRv04Ycf6ssvv9T8+fOVlZVV55iE8hrXmP1of2q7br0k/e9//9PGjRvVv3//Bi13f+9ZaxPKXF7dqlWrdN5552ngwIE6++yz9fXXX+udd97Rt99+q7fffnu/cxAAAAAAAADqYJrIww8/bNxut3nvvfeMMcbceuutxu12m+nTp/sfs2/fPuN2u825557rv+0///mPcbvd5oILLjDFxcX+2zdu3GiGDx9uevbsaTZu3Oi//aijjjIDBw4MWPYdd9xh3G63efHFFwNuX7BggXG73ebKK69sknV0u93mqKOOqvP+m266ybjdbjN+/HhTVFTkv/29994zbrfbXHLJJf7b3n77beN2u821115rKioq/Ldv3LjRDBkyxIwYMcKUlZXttz81x9wYYzZt2mTcbre59NJL/bede+65xu12m7vvvjvg+bNmzTJut9u88sorAbdPmzbNuN1u8+GHHwa1sW/fvv32qTYNfe6jjz5q3G63ufnmmwPG5ttvvzV9+vQxgwYNMoWFhcYYY1599VXjdrtNz549zTfffON/7KZNm8zw4cNNv379/Mu95557jNvtNosXLw5Y3kUXXWTcbrdZs2aNMcaYrVu3miOOOMIcd9xxJj8/3/84j8djfv/735vDDz/c/PDDD/7luN1uk5uba1avXh3Q7tSpU43b7TZff/11wO1XX321yc3NNZs2bTLGGPPkk08at9ttXn755YDH/fLLL+aII44ww4cPD7jd7XabcePGBdxWc4wbsl/51sHtdpu3337b/9jy8nJzwgknGLfbbdauXWuMaVhmatq+fbvJzc011157rf+2VatWGbfbbfr16xewb3k8HtO7d29zxRVXGGOMKSkpMcOGDTN5eXn+cTPGGK/Xa6644grjdrvNRx99FDBGbrfbvP/++wF9+Oqrr0xubq4599xzTUlJif/2/Px887vf/c707dvX7N69u851MKbu/amhfTzqqKOM2+02d955p/+2ffv2mb59+/rnLcuyjDHGVFZWmt/97nfG7Xb7+718+XLjdrvNKaecEtDn3bt3mxNPPNG43W6zbNkyY4wxK1euNG6320ybNi2gzwsXLjRut9s88sgjDV6Hffv2mYEDB5qRI0earVu3+h/79ddfmz59+hi3221effXV/Y7lK6+8Ytxut/nTn/5kvF6v//Z7773Xvw19lixZEjRePr6597vvvmvUtqhNbXNpYWGhGTx4sBkwYID59ttv/bdXVFSY6667zrjdbvPoo4/ut90333zTuN1uM3PmzIDbCwsLzW9+8xvTo0cP/zauvm8+/fTT/scWFxebM88807jdbrNkyRL/7b7HVt/OFRUV5vLLLw/aHnXtIw19TZ49e3bA6+zFF19s3G63efPNN/c7lr5tdsYZZwS81v3+9783brfbjB492j/PG2PMzTffHLDdysrKzIABA8wxxxwT0E9jjLn99tuN2+02//rXv/y31fZ62RTzwR/+8AfTo0cP89lnn/lv2717tzn++OON2+02N9100377UNvrY22Pa0j+Q52nm2I/8b0GP/fcc/7bfHPbtGnT/HOYMb++Js6ePXu/6x/Ka1xD9qPaxq7mmNXmrbfeMm6325x33nmmsrKywcv1jUXN96w1l92Qudw3Pm632/zjH//w32ZZlrnggguM2+02CxcurHOdAAAAAAAAULcmPyWvz/XXX6/s7Gy99NJL+uqrr+p83H/+8x9J0h133KG0tDT/7Z06ddKll16qyspKvf7663U+33f/YYcdFnTE3NFHH60BAwbovffeq/WUq+Fy3nnnBRxVO2rUKDmdzoBTpb3yyiuSpD//+c9KSPj1QN9OnTrprLPO0vbt2/XZZ581ab+OOeaYgL99p3NctWqVvF6v//ZrrrlGn3zyiX7729826fJD9Z///EepqalBY9OrVy+dc845Kigo0LvvvhvwnHHjxumII47w/33wwQfrvPPOU0lJiRYsWCDp1/WteVrfu+++W4sXL9Zhhx0mqeqIkvLycl155ZUB15BLSUnRlVdeKcuy/Ln1OeSQQ3T44YcH9UmqOs2ej8fj0UcffaT+/fvr4IMPliQdeeSRmjZtmk455ZSA57dv316dOnWq9TSs9WnMftWpUycdd9xx/r8TExP9Rzlv2bJF0oFlJicnRz169Ag41eWSJUvkdDp12mmnacuWLdq2bZskafny5SorK/O398EHHyg/P1+TJk3yj5skOZ1O/xG8r776asDyUlJSNGrUqIDbXnnlFRljdOONNwYcwdi6dWtNnjzZf5R3KGruT43poySdf/75/n9nZmb6j1adOHGi/+g8l8ulXr16SZJ++eUXSfKfIvbGG28MOForKysraHkDBgxQp06dNH/+/IDt5lvXk046qcHrsHDhQhUWFuq8885Tu3bt/I/t3bt3UJbr8tZbb8nhcOi6664LOPLx6quvPqCzADR2W9RnwYIF2rdvn8477zz/9pCkhIQE3XLLLUpJSam33Z49e+rOO+/UH//4x4DbMzIy1LNnT3m9Xu3bty/gvo4dOwY8Pi0tTVdffbWkqtPfVpeWlhZwiuiEhATdeOONtT62tn2koXPHWWedpaFDh2revHm6/fbb9eGHH+qEE07QCSecsN9x8Dn77LMDjobzHcn3+9//XhkZGf7bfUdA++Yir9er6dOn66677gropyT/kYI1T8lf04HOB9u3b9fy5cs1YsSIgDNCZGVl6fLLL9/vssMp1Hk6XPuJz+TJkwOOMPZlzbcND0Rj9qOGWL16tW655RZ17NhRDz74oFwuV9iW25C53CclJUXnnXee/2+Hw6ERI0ZIaprxBQAAAAAAiEdNfkpen8zMTN1666268sorNXXq1IDrv1X3/fffq23btv5TdFY3cOBA/2PqsmHDBpWUlMjr9fqvdVVdWVmZvF6vfvjhB3974dalS5eAvxMTE5Wenq7i4mL/batWrVJycrJeeumloOdv2LBBUtUXdk1ZtKz+hagkHXvssfr73/+ul156SW+//baOPPJIjRw5UqNGjVJ2dnaTLbchioqKtGnTJg0YMCDgy3KfgQMH6tlnnw3KxIABA4Ie27t3b0m/5mf8+PGaM2eO7r//fr344osaOXKkRo4cqeHDhwd84f7tt99KqrqG6Y8//hjQpu/6ZDWXX3NsJWnQoEHq2LGj5s2bpxtvvFEOh0MffvihSkpK/MVUqeoL2J49e6q4uFhfffWVfv75Z/3000/65ptv9PPPPwd84R2qxuxXNXMryV+08l2b8UAzM3LkSD3xxBNas2aN3G63lixZosMPP1wjRozQrFmztGzZMo0bN06LFi2Sw+Hwf8Hu2yarVq2qdT93uVxB69OuXTv/l9w+q1atkiS9++67+uijjwLu8xVra15Xri41t3lj+piYmKiOHTsG3ObLYs32k5OTJf26Lb7//ns5nc5a57XatvFJJ52kxx57TMuWLVNeXp7Ky8u1YMEC9e3bV4ccckiD18H3/+o/VPDp37+//zTO+/P999+rQ4cOatOmTcDtSUlJ6tWrV4OuI1ldY7ZFKHzPGTx4cNB9WVlZ6tq1q1avXq3CwsI6C75du3ZV165dVVZWpq+++kobNmzQxo0btWrVKv/pqWvu8/379w/48YgUPL/55ObmqmXLlgG3de7cWa1atQppH2no3OFwOHTXXXdp3Lhx/tPf33777bWue206d+4c8Heo+U9NTfVfB3rDhg1at26dNm7cqB9//NF/3eP6rqV7oPNBfftAtIQ6T4drP5Gqtlf79u0DbvO9pod6rd/9acx+FKr8/HxddtllMsbokUceCShihmO5DZ3LJalDhw5Bp92t+XoNAAAAAACAhglbwVSq+tLu6KOP1vvvv6+nn3466AhQqapAdtBBB9X6fN91R0tLS+tchu+6XuvXr9ejjz5a5+MO5EiDhvJ9sbs/hYWFqqysjGifU1JSAv5u27atXnnlFT3++ON6//339cYbb+iNN95QYmKiTj31VE2dOjXi18HyFZXrKjbUlYmaBRdJ/qN8fUXOww8/XC+//LKeeOIJLVy4UC+//LJefvllpaWl6bzzztPVV18th8OhwsJCSdpvwafmtqltmzscDp144ol68skn9eWXX6p///566623lJiYqLFjx/ofV1ZWppkzZ+rf//63PB6PpKptM3jwYLVu3Vo7d+6ssx91acx+Vdu2rnn9wQPNzKhRo/TEE09o8eLF6tatm/+6pQMHDpTL5dKKFSv8BdPevXv7t6tvm7z11lt1tl1zm9TMe/V2nnrqqZDbqUvN9puqjz717XtFRUVKTk6u9XEtWrRQamqqP09S1RHPjz32mN555x3l5eXp448/VkFBgf/o0oaug2/ure0a1a1atdpv330KCgpq3XclBRX9GqIx2yIUvjMV1PZjDqlq31q9erU8Hk+dc5hlWXryySf13HPP+fvQpk0b9e/fXx07dtS6detkjAl4Ttu2bYPaycjIUGpqqn9d9/dYSTrooIP0888/B9xWW/4aM3d06tRJPXv21IoVK3TooYc2aNvVPDrUJ5TXnuXLl+vuu+/2Fz6Tk5N1+OGHq1evXtq6dWvQONZ0oPPB/vaBA8nvgQp1ng7XfiLt//Wkvu0SisbsR6GoqKjQFVdcoV9++UX33ntvwJHk4VpuQ+dyKfzjCwAAAAAAEI/CWjCVpNtvv11Lly7V448/ruHDhwfdn56eru3bt9f6XN+XUfv78t33ReXJJ5+sv/71rwfe4QhJS0tTenp60FEtkdapUyfNmDFDXq9X3377rRYtWqTXXntN//73v9WiRQvdcMMNEe2Pb3vWlQnfF9Q1M+G7vbodO3ZICvzi+vDDD9dDDz2k8vJyffHFF/r444/12muv6YknnlDbtm11zjnn+L/AX7BgQa1HWTXEuHHj9OSTT+qdd97RYYcdpo8//lhHHnlkwKl+77nnHs2ePVvHHnus/vCHPyg3N9e/fscdd1yjCqYHul/tz4Fkpm/fvmrVqpUWL16sfv36qbi4WEOGDPGfznD58uX65ZdftH79el1xxRX+5/m2yfPPPx9w6suGSktLk8vl0ldffaXExMRGt1NX29KB9zFU6enp8ng8KigoUGZmZsB9ZWVlKi0tDchZ165d1bt3b82fP1+333673nnnHblcLv9Reg1dB98yaxbspF9/pFCfzMzMWp9fWxv7KwbULCaEa1v45iff3FJTXfNTdc8++6weeughDRkyRJMnT1aPHj38R/1deOGFWrduXdBzysrKgm4rLy8P2sZ1PdbXt5qPrU1j5o7XXntNK1as8O/br732mk499dR6l3UgtmzZogsvvFApKSmaPn26Bg4cqC5dusjlcuntt9/2n4p9fw50PmiKfSBUDcm/FNo8Hek5qyk1Zj8KxfTp07VixQpNmDCh1lOLh2O5DZ3LAQAAAAAAEB5hu4apT9u2bXXttdeqrKys1tP0HX744SosLNSaNWuC7luxYoUkqXv37nW237VrVyUlJWnVqlW1fpH4/PPP67HHHtOePXsOYC2aXm5urrZt21ZrMeyjjz7Sgw8+2OhT4YXq/fff1x133KGioiK5XC717dtXU6ZM8Z8meOXKlWFdfm0yMjJ08MEH66effqr12p3Lly+XFJwJ36kFq/vyyy8lyX+EyOuvv67p06fLGKOkpCQNHTpUN9xwg/9UhL71zc3NlRR8rVNJ+umnn3Tvvffqgw8+CGl9unfvrp49e+rDDz/UBx98oPLy8oDT8UrSm2++qTZt2uhvf/ubhg4d6i9GlJaW+q9X2dAjRg50v6rLgWbG5XJp+PDhWrFihZYtWyan06lBgwZJkoYOHar169f7r49Y/XTUvm1S23beu3ev7rrrLv33v/+tt/+5ubnyer21nmbzyy+/1P333+8fn4Zqqj6GynfN3NrGfOXKlTLGBG3jcePGae/evVqyZIk++OAD/eY3vwk4wrMh6+Dbrz7//POgx9a279TGdySgL+c+tW0jX0GrtkLUpk2bAv5uim1R8+hqSerRo4ek2se8qKhIq1ev1iGHHLLfoyPffPNNuVwuPf744xo5cqS/2GKM0fr16/3/rq628fzqq69kjFHfvn0Dbv/222+DTkW7ZcsW7dixI+ixtWno3LF9+3bdfffdys7O1iuvvKKsrCzdfffddRZdm8qCBQtUWlqqK6+8UmeeeaYOPfRQ/+mFfUWr6uNY2/Y80PmgZ8+ecjgcte4DtWXvQDQk/6HO05Ges5pSY/aj+rz00kv697//rSFDhujmm2+O2HIbM5cDAAAAAACg6YW9YCpJ55xzjvr376/vvvsu6D7fUSh33XVXwBeBmzZt0t///nclJibqhBNO8N+emJioyspK/9/Jyck6/vjjtXbtWj333HMBbS9dulR//etf9eqrr0b19Hi1GT9+vIwxmj59esD1pnbs2KHbb79dTz31VK2n+WtK69ev15w5czRnzpyA27ds2SKp6hpZPr4vaysqKsLaJ6lqbEpLSzVjxoyAbb1q1Sq9+OKLyszM1OjRowOe8/rrrwecbnLdunWaPXu2Wrdu7X/sl19+qRdffFHvvPNOwHM3b94s6df1HTdunFwulx566KGAgnZlZaWmT5+uZ599Vnv37g15fcaNG6eNGzfqmWeeUXp6elDfk5OTVVZWFnCUrNfr1V133eU/9WX1cU9MTKx3OzR0vwpVQzJTl5EjR6qwsFBz5swJuN7ikCFDJFUdwZOdnR1wKsTf/e53ysjI0NNPP+2/xq/Pfffdp3/+85/auHFjvcseP368JGnGjBn+06tKVcWuO+64Q//4xz8afd27pupjqHzbeObMmQE/LsjPz/cfbX/yyScHPOeEE05QQkKC/vrXvwZdS7eh6zBq1ChlZWVp1qxZAY9dt26dXnnllZDWwbc97rnnnoBMP/PMM9q1a1fAYw855BC5XC4tWbIk4Ii6jz76yH9K1sasR1181wyt3q8xY8aoRYsWmj17dsAyKysr/ftrzTGvKTk5WV6vN+gHIX//+9/9+1H1eU+qKo6+/fbb/r+Lior0wAMPyOl0+sfQZ+fOnXr66af9f1dUVOiee+6RJJ122mn77ZvU8Lnj9ttvV0FBgf70pz+pU6dOuummm1RQUNCg65g2hu806DVz8v333+uf//ynpMBx9G3P6q+3BzofZGdna8SIEVqyZInmz58f8Pz9nW6/MRqS/1Dn6UjPWaEK5TWuMfvR/ixdulQzZsxQx44d9dBDDwVdM7ixy635nrU2jZnLAQAAAAAA0PTCfkpeqerIjjvvvFOnnHJK0JdgJ598sj744APNnz9f48aN08iRI1VSUqL3339fRUVFmjp1qjp37ux/fE5Ojn766Sddf/31OvLII3XKKafopptu0hdffKF7771X77//vvr06aPt27fr3XffVUJCgmbMmCGns6o2XFBQoBdeeEEtWrTQ+eefH4nVr9Wpp57qX+8ffvhBI0aMUGVlpd555x3t3btX11133QGfDrY+Z555pl5++WXdf//9WrZsmXJzc7V7927NmzdPaWlpuuiii/yP9V0X75ZbbtHw4cN13nnnha1fkydP1ieffKI33nhDP/zwg4YNG6bdu3drwYIFMsbowQcfDLqGYFZWls444wydeOKJKi0t1fz581VWVqYHHnjAf52+Cy+8UO+8846uv/56zZs3T4cccoi2bNmid999V9nZ2Tr33HMlSV26dNENN9yge+65RyeeeKJGjx6tli1b6uOPP9a6det01FFHBRWa9ueEE07Qfffdp++//17jx48Pum7gSSedpGeffVannXaaxowZo8rKSn3yySfasGGDsrKylJ+fr7179/qvH5iTk6P169fr9ttv16hRo4IKsFLD96tQNSQzdRk5cqScTqe2bNmiMWPG+G8fOHCgEhISVFhYqGOPPTbgiLDMzEzdeeeduv766zV+/HiNGTNGOTk5Wr58ub7++mv17t1bF1xwQb3LHjZsmCZMmKBZs2bphBNO0KhRo5SUlKQFCxZo69atOuusszR06NAGj0tT9jFUgwcP1sSJE/Xcc89p3LhxOuqooyRJH374oXbu3KnJkydr8ODBAc9p06aNfvOb3+jjjz9WWlpawPg3dB3S09M1ffp0XXXVVTrjjDN07LHHSpLmzZunrKysWk+TXdPxxx+v+fPna968edqwYYPy8vK0du1aLVmyRB07dvQXIKSqfXzMmDGaP3++zjjjDI0aNUqbNm3SBx98oIEDBwYcndUU26J169ZKSkrS0qVLdffdd+t3v/udBg0apBkzZuiaa67RWWedpd/97ndq06aNlixZojVr1mjQoEGaPHnyftsdN26cvvzyS5199tk67rjjlJiYqKVLl2rVqlVq06aNdu/eHfSDjBYtWujaa6/VO++8o7Zt2+qjjz7Spk2bdNlll/mPTvNJS0vTgw8+qKVLl+rQQw/V4sWLtWbNGp188sn+jOxPQ+aO119/XR9++KFGjBjhL6Kecsop/ttff/31Wk9r2hSOOuooPfDAA3ryySe1fv16de7cWT///LM+/PBD//Vjq4+j7zXs8ccf1+rVqzVlypQmmQ9uu+02nXXWWbr66qs1ZswYtW3bVh9++KH/PUdTaUj+Q52nIz1nhSqU17jG7Ed1KSws1FVXXaXKykqNGDFCr776qsrLy4OOFL3iiisavNza3rPW1Ji5PFSrV6/WggUL1KNHj6D5HgAAAAAAAIEiUjCVqk7hd9FFF+nvf/97wO0Oh0MPPfSQXnrpJb3yyit65ZVXlJqaqn79+mnSpEkaNmxYwONvuOEG3XLLLZo3b552796tU045RVlZWXr55Zf15JNP6r333tOsWbOUlZWl0aNHB32hXFBQoEcffVQdO3aMasHU4XDo4Ycf1ksvvaTXXntNc+fOVUpKirp3766JEydG5Iutli1b6sUXX9Tjjz+uTz/9VEuWLFFGRoZGjhypKVOm6LDDDvM/9pJLLtG6dev06aef6qeffgprwTQ5OVnPP/+8nnnmGb3xxhuaM2eOMjMzddRRR+niiy9Wz549g55z9dVX67vvvtNrr72m4uJi9enTR1dddZX/dK+SdPDBB2vOnDl67LHH9Pnnn+uDDz5Q69atNW7cOE2ZMsX/hbokTZw4Ud26ddOzzz6rd999V5ZlqVOnTrr55pv1hz/8oc6jT2qTk5OjYcOG6dNPP9VJJ50UdP8111yj9PR0/e9//9Ps2bOVlZWlQw89VFOnTtW6des0Y8YMLVy4UGeccYakqi/o77zzTr366quqrKys9cvkhu5XoWpIZuqSlZWlI444Ql9//bX/qFKp6nTMvXr10ldffRVwOl6f4447Tu3atdOTTz6pRYsWyePxqGPHjrrssss0adKkkI/Injp1qnr37q05c+bof//7n1wul7p27aorrrgi6Gi9hmqqPobq5ptvVs+ePfXSSy/pjTfeUEJCgnr06KHbbrtNxxxzTK3PGTdunD7++GONHj3afw3Dxq7DmDFj9Pzzz+uRRx7R22+/rdTUVJ155pnq3bu3rrnmmpDWYebMmTriiCP0yiuvaM6cOerSpYseffRRvfLKKwEFU6nqSMCcnBzNmzdPs2bN0mGHHaaHH35YGzduDDqd5YFui6SkJN122216+OGHNXv2bLVo0UKDBg3SMccco9mzZ+vxxx/XokWLVF5ers6dO+vGG2/UeeedV++1MM855xwZYzRnzhzNnTtXLVq0UNeuXTVz5kwlJyfr8ssv18KFC9W/f3//c4YMGaKjjz5aTz31lD7++GMdeuih+utf/1rrUWedO3fW1VdfrQcffFDLly/XwQcfrFtuuSXkOTvUuWPnzp2aMWOGUlJSgo4mveOOOzRu3DjNmDGj1muXN4W2bdvqueee08yZM7VkyRJ98skn6tChgyZMmKCLL75YxxxzjBYtWiRjjBwOh44//ngtXLhQH330kWbPnq3x48erW7duBzwfdOrUSf/+97/14IMP6tNPP1VZWZmOPPJIXXXVVY06in9/Qs1/Q+bpSM9ZoQjlNa4x+1Fd9u3b579sw7/+9a86H3fFFVc0eLm1vWetTWPm8lCsXr1ajz76qL8gDgAAAAAAgLo5TEMvtgQAAMJu8+bNOvroo3X00Ufrscceq/fxubm5Ovzww2P2upMAAAAAAAAAEKsicg1TAAAAAAAAAAAAAIhFFEwBAAAAAAAAAAAAxC0KpgAAAAAAAAAAAADiFtcwBQAAAAAAAAAAABC3OMIUAAAAAAAAAAAAQNyiYAoAAAAAAAAAAAAgblEwBQAAAAAAAAAAABC3KJgCAAAAAAAAAAAAiFsUTAEAAAAAAAAAAADELQqmAAAAAAAAAAAAAOIWBVMAAAAAAAAAAAAAcYuCKQAAAAAAAAAAAIC4RcEUAAAAAAAAAAAAQNz6P+U33zW7NTOSAAAAAElFTkSuQmCC"/>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<blockquote>
<p><font size="3">💡 Since we are working with stock datas, we will not consider the "Cumelitive Effect" and only conside the "Relative Effect"</font></p>
</blockquote>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [15]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="n">impact</span><span class="o">.</span><span class="n">summary</span><span class="p">())</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
<pre>Posterior Inference {Causal Impact}
                          Average            Cumulative
Actual                    43971.47           263828.82
Prediction (s.d.)         49543.16 (885.73)  297258.94 (5314.37)
95% CI                    [47734.0, 51206.0] [286404.02, 307235.99]

Absolute effect (s.d.)    -5571.69 (885.73)  -33430.12 (5314.37)
95% CI                    [-7234.53, -3762.53][-43407.17, -22575.2]

Relative effect (s.d.)    -11.25% (1.79%)    -11.25% (1.79%)
95% CI                    [-14.6%, -7.59%]   [-14.6%, -7.59%]

Posterior tail-area probability p: 0.0
Posterior prob. of a causal effect: 100.0%

For more details run the command: print(impact.summary('report'))
</pre>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="2.4-Interpretation">2.4 Interpretation<a class="anchor-link" href="#2.4-Interpretation">¶</a></h2><p><font size="3">The average value of the response variable during the post-intervention period was around 43971.47. If the intervention had not taken place, we would have expected an average response of 49543.17.The 95% interval for this expected value ranges from 47823.92 to 51362.75. That means if Elon Musk did not make that tweet the Bitcoin avarage price would be 49543.17 around that period, but because of the tweet the actual average Bitcoin price fall to 43971.47</font></p>
<p><font size="3">By subtracting this expected value from the observed response, we estimate the causal effect of the intervention on the response variable to be -5571.7, with a 95% interval of -7391.28 to -3852.45. That indicates there is an negative effect on the Bitcoin price wich is around -5571.7</font></p>
<p><font size="3">In relative terms, the response variable showed a decrease of approximately 11.25%. The 95% interval for this percentage change is from -14.92% to -7.78%. This indicates that the observed negative effect during the intervention period is statistically significant.</font></p>
<p><font size="3">The probability of obtaining this effect by chance alone, as indicated by the Bayesian one-sided tail-area probability (p-value), is very small at 0.0. Therefore, the causal effect can be considered statistically significant.</font></p>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h1 id="3-Conclusion"><strong>3 Conclusion</strong><a class="anchor-link" href="#3-Conclusion">¶</a></h1><p><font size="3">By applying the Google Causal Impact we are able to prove there is a negative effect between the Elon Musk's Bitcoin tweet and the Bitcoin price fall. Understanding and analyzing causal relationships in cryptocurrency markets are crucial for investors, traders, policymakers, and researchers alike. By leveraging techniques like Google Causal Impact, we can gain a deeper understanding of the dynamics within these markets and make more informed decisions. This analysis serves as a reminder of the interconnectedness of social media, public figures, and the cryptocurrency landscape, and the potential implications of their interactions on market behavior.</font></p>
<p><font size="3">Overall, the case study showcases the power of data analysis techniques like Google Causal Impact in studying and quantifying the impact of specific events or interventions on cryptocurrency prices. This knowledge can provide valuable insights for market participants and contribute to a more comprehensive understanding of the complex and dynamic nature of the cryptocurrency market.</font></p>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<script>
  $(document).ready(function(){
    $('div.prompt').hide();
    $('div.back-to-top').hide();
    $('nav#menubar').hide();
    $('.breadcrumb').hide();
    $('.hidden-print').hide();
  });
</script>
<footer id="attribution" style="float:right; color:#999; background:#fff;">
Created with Jupyter written by Sakiful Ahmed Saiyan.
</footer>
</div>
</div>
</div>
</div>
</main>
</body>
</html>
