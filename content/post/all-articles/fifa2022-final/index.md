+++
title = 'How to Analyze Football Data Using Python and StatsBomb: FIFA World Cup 2022 Final Example'
description = "A comprehensive guide on performing football data analysis"
slug = "fifa2022-final"
date = "2024-11-24"
image = "cover.jpg"
draft = false
categories = ["My Articles"]
tags= ["data analytics"]
+++

<!DOCTYPE html>

<html lang="en">
<head><meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<title>Fifa Worldcup-2022 (Final) Analysis</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
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
<h2 id="1.-Introduction">1. Introduction<a class="anchor-link" href="#1.-Introduction">¶</a></h2><p>The FIFA World Cup 2022 Final between Argentina and France will be remembered as one of the most thrilling matches in football history. With Argentina clinching victory in a penalty shootout after a 3-3 draw, this match provided a wealth of tactical, individual, and team insights. This analysis working with only Argentina's player passing data to find out key patterns, tactics and insight that shaped this epic encounter.</p>
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
<h2 id="2.-Libreries-and-Data-Import">2. Libreries and Data Import<a class="anchor-link" href="#2.-Libreries-and-Data-Import">¶</a></h2><p>To conduct this analysis, we utilized the StatsBomb API for detailed event data. Key Python libraries included:</p>
<ul>
<li>pandas for data manipulation,</li>
<li>mplsoccer for visualization,</li>
<li>matplotlib for plotting, and</li>
<li>scipy for data smoothing.</li>
<li>The dataset included detailed events such as passes, shots, fouls, and defensive actions from the final matc</li>
</ul>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Import Libreries &amp; Packeges</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">from</span> <span class="nn">mplsoccer</span> <span class="kn">import</span> <span class="n">Pitch</span><span class="p">,</span> <span class="n">VerticalPitch</span><span class="p">,</span> <span class="n">FontManager</span>
<span class="kn">from</span> <span class="nn">matplotlib</span> <span class="kn">import</span> <span class="n">rcParams</span>
<span class="kn">from</span> <span class="nn">statsbombpy</span> <span class="kn">import</span> <span class="n">sb</span>
<span class="kn">from</span> <span class="nn">scipy.ndimage</span> <span class="kn">import</span> <span class="n">gaussian_filter</span>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [2]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Call Statsbomb API to import data</span>
<span class="n">matches</span> <span class="o">=</span> <span class="n">sb</span><span class="o">.</span><span class="n">matches</span><span class="p">(</span><span class="n">competition_id</span><span class="o">=</span><span class="mi">43</span><span class="p">,</span> <span class="n">season_id</span><span class="o">=</span><span class="mi">106</span><span class="p">)</span>
<span class="n">matches</span><span class="p">[</span><span class="n">matches</span><span class="p">[</span><span class="s1">'competition_stage'</span><span class="p">]</span><span class="o">==</span><span class="s1">'Final'</span><span class="p">]</span>
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
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[2]:</div>
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
<th>match_id</th>
<th>match_date</th>
<th>kick_off</th>
<th>competition</th>
<th>season</th>
<th>home_team</th>
<th>away_team</th>
<th>home_score</th>
<th>away_score</th>
<th>match_status</th>
<th>...</th>
<th>last_updated_360</th>
<th>match_week</th>
<th>competition_stage</th>
<th>stadium</th>
<th>referee</th>
<th>home_managers</th>
<th>away_managers</th>
<th>data_version</th>
<th>shot_fidelity_version</th>
<th>xy_fidelity_version</th>
</tr>
</thead>
<tbody>
<tr>
<th>9</th>
<td>3869685</td>
<td>2022-12-18</td>
<td>17:00:00.000</td>
<td>International - FIFA World Cup</td>
<td>2022</td>
<td>Argentina</td>
<td>France</td>
<td>3</td>
<td>3</td>
<td>available</td>
<td>...</td>
<td>2023-08-17T15:55:15.164685</td>
<td>7</td>
<td>Final</td>
<td>Lusail Stadium</td>
<td>Szymon Marciniak</td>
<td>Lionel Sebastián Scaloni</td>
<td>Didier Deschamps</td>
<td>1.1.0</td>
<td>2</td>
<td>2</td>
</tr>
</tbody>
</table>
<p>1 rows × 22 columns</p>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [3]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Select Fifa Worldcup 2022 "Argentina vs France" final match</span>
<span class="n">events</span> <span class="o">=</span> <span class="n">sb</span><span class="o">.</span><span class="n">events</span><span class="p">(</span><span class="n">match_id</span><span class="o">=</span><span class="mi">3869685</span><span class="p">)</span>
</pre></div>
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
<h2 id="3.-Data-Preprocessing">3. Data Preprocessing<a class="anchor-link" href="#3.-Data-Preprocessing">¶</a></h2><p>Before diving into analysis, preprocessing steps involved filtering and structuring the data:</p>
<ul>
<li>Extracting key events (passes, shot,, goals, player positions),</li>
<li>Filtering player-specific data (Messi, Argentina),</li>
<li>Data Normalization</li>
</ul>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="n">events</span><span class="o">.</span><span class="n">tail</span><span class="p">()</span>
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
<th>50_50</th>
<th>bad_behaviour_card</th>
<th>ball_receipt_outcome</th>
<th>ball_recovery_offensive</th>
<th>ball_recovery_recovery_failure</th>
<th>block_deflection</th>
<th>block_offensive</th>
<th>carry_end_location</th>
<th>clearance_aerial_won</th>
<th>clearance_body_part</th>
<th>...</th>
<th>substitution_outcome</th>
<th>substitution_outcome_id</th>
<th>substitution_replacement</th>
<th>substitution_replacement_id</th>
<th>tactics</th>
<th>team</th>
<th>team_id</th>
<th>timestamp</th>
<th>type</th>
<th>under_pressure</th>
</tr>
</thead>
<tbody>
<tr>
<th>4402</th>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>...</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>Argentina</td>
<td>779</td>
<td>00:19:07.472</td>
<td>Half End</td>
<td>NaN</td>
</tr>
<tr>
<th>4403</th>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>...</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>France</td>
<td>771</td>
<td>00:05:58.866</td>
<td>Half End</td>
<td>NaN</td>
</tr>
<tr>
<th>4404</th>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>...</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>Argentina</td>
<td>779</td>
<td>00:05:58.866</td>
<td>Half End</td>
<td>NaN</td>
</tr>
<tr>
<th>4405</th>
<td>NaN</td>
<td>Yellow Card</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>...</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>France</td>
<td>771</td>
<td>00:49:35.193</td>
<td>Bad Behaviour</td>
<td>NaN</td>
</tr>
<tr>
<th>4406</th>
<td>NaN</td>
<td>Yellow Card</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>...</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>NaN</td>
<td>Argentina</td>
<td>779</td>
<td>00:04:57.514</td>
<td>Bad Behaviour</td>
<td>NaN</td>
</tr>
</tbody>
</table>
<p>5 rows × 94 columns</p>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [5]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Check the available colomns</span>
<span class="n">events</span><span class="o">.</span><span class="n">columns</span>
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
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[5]:</div>
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>Index(['50_50', 'bad_behaviour_card', 'ball_receipt_outcome',
       'ball_recovery_offensive', 'ball_recovery_recovery_failure',
       'block_deflection', 'block_offensive', 'carry_end_location',
       'clearance_aerial_won', 'clearance_body_part', 'clearance_head',
       'clearance_left_foot', 'clearance_other', 'clearance_right_foot',
       'counterpress', 'dribble_nutmeg', 'dribble_outcome', 'dribble_overrun',
       'duel_outcome', 'duel_type', 'duration', 'foul_committed_advantage',
       'foul_committed_card', 'foul_committed_offensive',
       'foul_committed_penalty', 'foul_committed_type', 'foul_won_advantage',
       'foul_won_defensive', 'foul_won_penalty', 'goalkeeper_body_part',
       'goalkeeper_end_location', 'goalkeeper_outcome', 'goalkeeper_position',
       'goalkeeper_technique', 'goalkeeper_type', 'id', 'index',
       'interception_outcome', 'location', 'match_id', 'minute', 'off_camera',
       'out', 'pass_aerial_won', 'pass_angle', 'pass_assisted_shot_id',
       'pass_body_part', 'pass_cross', 'pass_deflected', 'pass_end_location',
       'pass_goal_assist', 'pass_height', 'pass_inswinging', 'pass_length',
       'pass_outcome', 'pass_outswinging', 'pass_recipient',
       'pass_recipient_id', 'pass_shot_assist', 'pass_switch',
       'pass_technique', 'pass_through_ball', 'pass_type', 'period',
       'play_pattern', 'player', 'player_id', 'position', 'possession',
       'possession_team', 'possession_team_id', 'related_events', 'second',
       'shot_aerial_won', 'shot_body_part', 'shot_end_location',
       'shot_first_time', 'shot_freeze_frame', 'shot_key_pass_id',
       'shot_one_on_one', 'shot_outcome', 'shot_statsbomb_xg',
       'shot_technique', 'shot_type', 'substitution_outcome',
       'substitution_outcome_id', 'substitution_replacement',
       'substitution_replacement_id', 'tactics', 'team', 'team_id',
       'timestamp', 'type', 'under_pressure'],
      dtype='object')</pre>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [6]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Create x and y lables from "location" data</span>
<span class="n">events</span><span class="p">[[</span><span class="s1">'x'</span><span class="p">,</span><span class="s1">'y'</span><span class="p">]]</span><span class="o">=</span> <span class="n">events</span><span class="p">[</span><span class="s1">'location'</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">)</span>

<span class="c1"># Create end_x and end_y Lables from "pass_end_location" Data</span>
<span class="n">events</span><span class="p">[[</span><span class="s1">'end_x'</span><span class="p">,</span><span class="s1">'end_y'</span><span class="p">]]</span><span class="o">=</span> <span class="n">events</span><span class="p">[</span><span class="s1">'pass_end_location'</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">)</span>
</pre></div>
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
<h2 id="4.-Ploting-&amp;-Visualization">4. Ploting &amp; Visualization<a class="anchor-link" href="#4.-Ploting-&amp;-Visualization">¶</a></h2>
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
<h3 id="4.1-Aregntina's-Pass-Analysis">4.1 Aregntina's Pass Analysis<a class="anchor-link" href="#4.1-Aregntina's-Pass-Analysis">¶</a></h3><p>Analysing Argentina's passes and player data will give us key insights into the team's build-up play. Here we will try to understand:</p>
<ul>
<li>Completed vs Missed/Other passes</li>
<li>Player individual passes</li>
<li>Messi's passes pattern</li>
<li>Passes leads to goal</li>
</ul>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Create new data frame for all the passe's by Aregentine players</span>
<span class="n">ag_pass_df</span> <span class="o">=</span> <span class="n">events</span><span class="p">[(</span><span class="n">events</span><span class="p">[</span><span class="s1">'type'</span><span class="p">]</span><span class="o">==</span><span class="s1">'Pass'</span><span class="p">)</span> <span class="o">&amp;</span> <span class="p">(</span><span class="n">events</span><span class="p">[</span><span class="s1">'team'</span><span class="p">]</span><span class="o">==</span><span class="s1">'Argentina'</span><span class="p">)]</span>

<span class="c1"># Filter sucessfull passes</span>
<span class="n">mask_pass</span> <span class="o">=</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="s1">'pass_outcome'</span><span class="p">]</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Set up the pitch</span>
<span class="n">pitch</span> <span class="o">=</span> <span class="n">Pitch</span><span class="p">(</span><span class="n">pitch_type</span><span class="o">=</span><span class="s1">'statsbomb'</span><span class="p">,</span> <span class="n">pitch_color</span><span class="o">=</span><span class="s1">'#22312b'</span><span class="p">,</span> <span class="n">line_color</span><span class="o">=</span><span class="s1">'#c7d5cc'</span><span class="p">)</span>
<span class="n">fig</span><span class="p">,</span> <span class="n">axs</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">draw</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">13</span><span class="p">),</span> <span class="n">constrained_layout</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">tight_layout</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_facecolor</span><span class="p">(</span><span class="s1">'#22312b'</span><span class="p">)</span>

<span class="c1"># Plot the completed passes</span>
<span class="n">pitch</span><span class="o">.</span><span class="n">lines</span><span class="p">(</span><span class="n">ag_pass_df</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">y</span><span class="p">,</span>
            <span class="n">ag_pass_df</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">end_x</span><span class="p">,</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">end_y</span><span class="p">,</span>
            <span class="n">lw</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span> <span class="n">transparent</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">comet</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'#3cada2'</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">'completed passes'</span><span class="p">)</span>
<span class="n">pitch</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">ag_pass_df</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">y</span><span class="p">,</span> <span class="n">alpha</span> <span class="o">=</span> <span class="mf">0.2</span><span class="p">,</span> <span class="n">color</span> <span class="o">=</span> <span class="s2">"#3cada2"</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">)</span>

<span class="c1"># Plot the other passes</span>
<span class="n">pitch</span><span class="o">.</span><span class="n">lines</span><span class="p">(</span><span class="n">ag_pass_df</span><span class="p">[</span><span class="o">~</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="o">~</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">y</span><span class="p">,</span>
            <span class="n">ag_pass_df</span><span class="p">[</span><span class="o">~</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">end_x</span><span class="p">,</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="o">~</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">end_y</span><span class="p">,</span>
            <span class="n">lw</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span> <span class="n">transparent</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">comet</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'#ba4f45'</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">'other passes'</span><span class="p">)</span>
<span class="n">pitch</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">ag_pass_df</span><span class="p">[</span><span class="o">~</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="o">~</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">y</span><span class="p">,</span> <span class="n">alpha</span> <span class="o">=</span> <span class="mf">0.2</span><span class="p">,</span> <span class="n">color</span> <span class="o">=</span> <span class="s2">"#ba4f45"</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">)</span>

<span class="c1"># Set up the legend</span>
<span class="n">axs</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">facecolor</span><span class="o">=</span><span class="s1">'#22312b'</span><span class="p">,</span> <span class="n">handlelength</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span> <span class="n">edgecolor</span><span class="o">=</span><span class="s1">'None'</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">15</span><span class="p">,</span> <span class="n">loc</span><span class="o">=</span><span class="s1">'upper left'</span><span class="p">,</span> <span class="n">labelcolor</span><span class="o">=</span><span class="s1">'white'</span><span class="p">)</span>

<span class="c1"># Set the title</span>
<span class="n">ax_title</span> <span class="o">=</span> <span class="n">axs</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">'Argentina Passes Against France'</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">20</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'white'</span><span class="p">)</span>
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
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [9]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Create player name list</span>
<span class="n">players</span> <span class="o">=</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="s1">'player'</span><span class="p">]</span><span class="o">.</span><span class="n">unique</span><span class="p">()</span>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [10]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Set up the pitch</span>
<span class="n">pitch</span> <span class="o">=</span> <span class="n">Pitch</span><span class="p">(</span><span class="n">pitch_type</span><span class="o">=</span><span class="s1">'statsbomb'</span><span class="p">,</span> <span class="n">pitch_color</span><span class="o">=</span><span class="s1">'#22312b'</span><span class="p">,</span> <span class="n">line_color</span><span class="o">=</span><span class="s1">'#c7d5cc'</span><span class="p">)</span>
<span class="n">fig</span><span class="p">,</span> <span class="n">axs</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">draw</span><span class="p">(</span><span class="n">nrows</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span> <span class="n">ncols</span><span class="o">=</span><span class="mi">4</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span><span class="mi">15</span><span class="p">),</span><span class="n">constrained_layout</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">tight_layout</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_facecolor</span><span class="p">(</span><span class="s1">'#22312b'</span><span class="p">)</span>

<span class="c1"># Convert the axs into one dimension</span>
<span class="n">axs</span> <span class="o">=</span> <span class="n">axs</span><span class="o">.</span><span class="n">flatten</span><span class="p">()</span>

<span class="c1"># Plot each player's passes</span>
<span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">player</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">players</span><span class="p">):</span>
    <span class="n">player_passes</span> <span class="o">=</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="n">ag_pass_df</span><span class="p">[</span><span class="s1">'player'</span><span class="p">]</span> <span class="o">==</span> <span class="n">player</span><span class="p">]</span>
    
    <span class="n">pitch</span><span class="o">.</span><span class="n">lines</span><span class="p">(</span><span class="n">player_passes</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">player_passes</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">y</span><span class="p">,</span>
             <span class="n">player_passes</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">end_x</span><span class="p">,</span> <span class="n">player_passes</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">end_y</span><span class="p">,</span>
             <span class="n">lw</span><span class="o">=</span><span class="mi">2</span><span class="p">,</span> <span class="n">transparent</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">comet</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'#3cada2'</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">[</span><span class="n">i</span><span class="p">],</span> <span class="n">label</span><span class="o">=</span><span class="s1">'completed passes'</span><span class="p">)</span>
    <span class="n">pitch</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">player_passes</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">player_passes</span><span class="p">[</span><span class="n">mask_pass</span><span class="p">]</span><span class="o">.</span><span class="n">y</span><span class="p">,</span> <span class="n">alpha</span> <span class="o">=</span> <span class="mf">0.2</span><span class="p">,</span> <span class="n">color</span> <span class="o">=</span> <span class="s2">"#3cada2"</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">[</span><span class="n">i</span><span class="p">])</span>
    <span class="n">axs</span><span class="p">[</span><span class="n">i</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Passes by </span><span class="si">{</span><span class="n">player</span><span class="si">}</span><span class="s2">"</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'white'</span><span class="p">)</span>

<span class="c1"># Remove extra pitches</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">17</span><span class="p">,</span><span class="mi">20</span><span class="p">):</span>
    <span class="n">axs</span><span class="p">[</span><span class="n">i</span><span class="p">]</span><span class="o">.</span><span class="n">remove</span><span class="p">()</span>

<span class="c1"># Set the title</span>
<span class="n">fig</span><span class="o">.</span><span class="n">suptitle</span><span class="p">(</span><span class="s2">"Argentine Player's Individual Passes"</span><span class="p">,</span> <span class="n">fontsize</span> <span class="o">=</span> <span class="mi">25</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'white'</span><span class="p">)</span>
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
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [11]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Filter all the passes from Messi</span>
<span class="n">messi_pass</span> <span class="o">=</span> <span class="n">ag_pass_df</span><span class="p">[</span><span class="n">ag_pass_df</span><span class="p">[</span><span class="s1">'player'</span><span class="p">]</span><span class="o">==</span><span class="s1">'Lionel Andrés Messi Cuccittini'</span><span class="p">]</span>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [12]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Set up the pitch</span>
<span class="n">pitch</span> <span class="o">=</span> <span class="n">Pitch</span><span class="p">(</span><span class="n">pitch_type</span><span class="o">=</span><span class="s1">'statsbomb'</span><span class="p">,</span> <span class="n">pitch_color</span><span class="o">=</span><span class="s1">'#22312b'</span><span class="p">,</span> <span class="n">line_color</span><span class="o">=</span><span class="s1">'#c7d5cc'</span><span class="p">)</span>
<span class="n">fig</span><span class="p">,</span> <span class="n">axs</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">draw</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">8</span><span class="p">),</span> <span class="n">constrained_layout</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">tight_layout</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_facecolor</span><span class="p">(</span><span class="s1">'#22312b'</span><span class="p">)</span>

<span class="c1"># Plot the pass convex hull</span>
<span class="n">hull</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">convexhull</span><span class="p">(</span><span class="n">messi_pass</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">messi_pass</span><span class="o">.</span><span class="n">y</span><span class="p">)</span>
<span class="n">poly</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">polygon</span><span class="p">(</span><span class="n">hull</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">,</span> <span class="n">edgecolor</span><span class="o">=</span><span class="s1">'cornflowerblue'</span><span class="p">,</span> <span class="n">facecolor</span><span class="o">=</span><span class="s1">'cornflowerblue'</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=</span><span class="mf">0.3</span><span class="p">)</span>
<span class="n">scatter</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">messi_pass</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">messi_pass</span><span class="o">.</span><span class="n">y</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">,</span> <span class="n">edgecolor</span><span class="o">=</span><span class="s1">'black'</span><span class="p">,</span> <span class="n">facecolor</span><span class="o">=</span><span class="s1">'cornflowerblue'</span><span class="p">)</span>

<span class="c1"># Set the title</span>
<span class="n">axs_title</span> <span class="o">=</span> <span class="n">axs</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s2">"Messi's Pass Convex Hull"</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">20</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'white'</span><span class="p">)</span>
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
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [13]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">shot_pass_df</span> <span class="o">=</span> <span class="n">events</span><span class="o">.</span><span class="n">loc</span><span class="p">[(</span><span class="n">events</span><span class="p">[</span><span class="s1">'pass_assisted_shot_id'</span><span class="p">]</span><span class="o">.</span><span class="n">notnull</span><span class="p">())</span> <span class="o">&amp;</span> <span class="p">(</span><span class="n">events</span><span class="p">[</span><span class="s1">'team'</span><span class="p">]</span><span class="o">==</span><span class="s1">'Argentina'</span><span class="p">),</span> <span class="p">[</span><span class="s1">'x'</span><span class="p">,</span> <span class="s1">'y'</span><span class="p">,</span> <span class="s1">'end_x'</span><span class="p">,</span> <span class="s1">'end_y'</span><span class="p">,</span> <span class="s1">'pass_assisted_shot_id'</span><span class="p">]]</span>
<span class="n">shot_df</span> <span class="o">=</span> <span class="n">events</span><span class="o">.</span><span class="n">loc</span><span class="p">[(</span><span class="n">events</span><span class="p">[</span><span class="s1">'type'</span><span class="p">]</span><span class="o">==</span><span class="s1">'Shot'</span><span class="p">)</span> <span class="o">&amp;</span> <span class="p">(</span><span class="n">events</span><span class="p">[</span><span class="s1">'team'</span><span class="p">]</span><span class="o">==</span><span class="s1">'Argentina'</span><span class="p">),</span> <span class="p">[</span><span class="s1">'id'</span><span class="p">,</span> <span class="s1">'shot_outcome'</span><span class="p">,</span> <span class="s1">'shot_statsbomb_xg'</span><span class="p">,</span> <span class="s1">'minute'</span><span class="p">]]</span><span class="o">.</span><span class="n">rename</span><span class="p">({</span><span class="s1">'id'</span><span class="p">:</span><span class="s1">'pass_assisted_shot_id'</span><span class="p">},</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="n">shot_pass_df</span> <span class="o">=</span> <span class="n">shot_pass_df</span><span class="o">.</span><span class="n">merge</span><span class="p">(</span><span class="n">shot_df</span><span class="p">,</span> <span class="n">how</span><span class="o">=</span><span class="s1">'left'</span><span class="p">)</span>
<span class="n">mask_goal</span> <span class="o">=</span> <span class="n">shot_pass_df</span><span class="p">[</span><span class="s1">'shot_outcome'</span><span class="p">]</span> <span class="o">==</span> <span class="s1">'Goal'</span>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Setup the pitch</span>
<span class="n">pitch</span> <span class="o">=</span> <span class="n">VerticalPitch</span><span class="p">(</span><span class="n">pitch_type</span><span class="o">=</span><span class="s1">'statsbomb'</span><span class="p">,</span> <span class="n">pitch_color</span><span class="o">=</span><span class="s1">'#22312b'</span><span class="p">,</span> <span class="n">line_color</span><span class="o">=</span><span class="s1">'#c7d5cc'</span><span class="p">,</span>
                      <span class="n">half</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">pad_top</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>
<span class="n">fig</span><span class="p">,</span> <span class="n">axs</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">grid</span><span class="p">(</span><span class="n">endnote_height</span><span class="o">=</span><span class="mf">0.03</span><span class="p">,</span> <span class="n">endnote_space</span><span class="o">=</span><span class="mi">0</span><span class="p">,</span> <span class="n">figheight</span><span class="o">=</span><span class="mi">7</span><span class="p">,</span>
                      <span class="n">title_height</span><span class="o">=</span><span class="mf">0.08</span><span class="p">,</span> <span class="n">title_space</span><span class="o">=</span><span class="mi">0</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span>
                      <span class="n">grid_height</span><span class="o">=</span><span class="mf">0.82</span><span class="p">)</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_facecolor</span><span class="p">(</span><span class="s1">'#22312b'</span><span class="p">)</span>

<span class="c1"># Plot the completed passes</span>
<span class="n">pitch</span><span class="o">.</span><span class="n">lines</span><span class="p">(</span><span class="n">shot_pass_df</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">shot_pass_df</span><span class="o">.</span><span class="n">y</span><span class="p">,</span> <span class="n">shot_pass_df</span><span class="o">.</span><span class="n">end_x</span><span class="p">,</span> <span class="n">shot_pass_df</span><span class="o">.</span><span class="n">end_y</span><span class="p">,</span>
            <span class="n">lw</span><span class="o">=</span><span class="mi">6</span><span class="p">,</span> <span class="n">transparent</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">comet</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="s1">'jet'</span><span class="p">,</span>
            <span class="n">label</span><span class="o">=</span><span class="s1">'pass leading to shot'</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">[</span><span class="s1">'pitch'</span><span class="p">])</span>

<span class="c1"># Plot the goals</span>
<span class="n">pitch</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">shot_pass_df</span><span class="p">[</span><span class="n">mask_goal</span><span class="p">]</span><span class="o">.</span><span class="n">end_x</span><span class="p">,</span> <span class="n">shot_pass_df</span><span class="p">[</span><span class="n">mask_goal</span><span class="p">]</span><span class="o">.</span><span class="n">end_y</span><span class="p">,</span> <span class="n">s</span><span class="o">=</span><span class="mi">300</span><span class="p">,</span>
              <span class="n">marker</span><span class="o">=</span><span class="s1">'football'</span><span class="p">,</span> <span class="n">edgecolors</span><span class="o">=</span><span class="s1">'black'</span><span class="p">,</span> <span class="n">c</span><span class="o">=</span><span class="s1">'white'</span><span class="p">,</span> <span class="n">zorder</span><span class="o">=</span><span class="mi">2</span><span class="p">,</span>
              <span class="n">label</span><span class="o">=</span><span class="s1">'goal'</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">[</span><span class="s1">'pitch'</span><span class="p">])</span>
<span class="n">pitch</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">shot_pass_df</span><span class="p">[</span><span class="o">~</span><span class="n">mask_goal</span><span class="p">]</span><span class="o">.</span><span class="n">end_x</span><span class="p">,</span> <span class="n">shot_pass_df</span><span class="p">[</span><span class="o">~</span><span class="n">mask_goal</span><span class="p">]</span><span class="o">.</span><span class="n">end_y</span><span class="p">,</span>
              <span class="n">edgecolors</span><span class="o">=</span><span class="s1">'white'</span><span class="p">,</span> <span class="n">c</span><span class="o">=</span><span class="s1">'#22312b'</span><span class="p">,</span> <span class="n">s</span><span class="o">=</span><span class="mi">300</span><span class="p">,</span> <span class="n">zorder</span><span class="o">=</span><span class="mi">2</span><span class="p">,</span>
              <span class="n">label</span><span class="o">=</span><span class="s1">'shot'</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">[</span><span class="s1">'pitch'</span><span class="p">])</span>

<span class="c1"># Set the title</span>
<span class="n">axs</span><span class="p">[</span><span class="s1">'title'</span><span class="p">]</span><span class="o">.</span><span class="n">text</span><span class="p">(</span><span class="mf">0.5</span><span class="p">,</span> <span class="mf">0.5</span><span class="p">,</span> <span class="sa">f</span><span class="s1">'Argentina Passes Leading to Shots'</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'white'</span><span class="p">,</span>
                  <span class="n">va</span><span class="o">=</span><span class="s1">'center'</span><span class="p">,</span> <span class="n">ha</span><span class="o">=</span><span class="s1">'center'</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">20</span><span class="p">)</span>

<span class="c1"># Set legend</span>
<span class="n">legend</span> <span class="o">=</span> <span class="n">axs</span><span class="p">[</span><span class="s1">'pitch'</span><span class="p">]</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">facecolor</span><span class="o">=</span><span class="s1">'#22312b'</span><span class="p">,</span> <span class="n">edgecolor</span><span class="o">=</span><span class="s1">'None'</span><span class="p">,</span>
                             <span class="n">loc</span><span class="o">=</span><span class="s1">'lower center'</span><span class="p">,</span> <span class="n">handlelength</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>
<span class="k">for</span> <span class="n">text</span> <span class="ow">in</span> <span class="n">legend</span><span class="o">.</span><span class="n">get_texts</span><span class="p">():</span>
    <span class="n">text</span><span class="o">.</span><span class="n">set_fontsize</span><span class="p">(</span><span class="mi">15</span><span class="p">)</span>
    <span class="n">text</span><span class="o">.</span><span class="n">set_color</span><span class="p">(</span><span class="s1">'white'</span><span class="p">)</span>
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
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAxEAAAKeCAYAAADa9pbfAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjkuMiwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8hTgPZAAAACXBIWXMAAA9hAAAPYQGoP6dpAAEAAElEQVR4nOzdd5hU1f3H8fc5t8zMdnbpvSpVig2wYEXsGlEjmmiaxlhi7z8TE9REjZpEk2g0xiQWFHvDLiI2FAvY6L0ubN9p957z+2N2l0VYYGGXpXxfz8PD7pQ7587O3r2fe875HtVz6ACLEEIIIYQQQmwh3dINEEIIIYQQQuxcJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIIYQQQgghGkVChBBCCCGEEKJRJEQIsQvbf+99mTt9JnOnz2T/vfdt6eYIsVPr1KFj3e/TKcefuMH9F5/3q7r7xY5Lfk5CNA23pRsgdm/7DduHxx74d933p55zFtO//LzF2iN2bJNffJXOHTttcHs6naaispJ5C+Yz9eMPefypJ1lVvLoFWrh7qj0Z+/CTaZx57k9auDVid7D/3vty8nEnMGTQXrRv245YNEo8kWDV6lXMX7SQL2fOYOrHH/LFzBlYa1u6uULskqQnQrSoH3zvat7Jx53QQi3ZeWzuaujuyPM8Clu1Yp+hw/j1eb/itaeeZ/Shh7d0s4TYqd322/HMnT6TyS++2tJNqZMVi/H3O/7Mo/98iFNPPJk+PXuRm5OD67rk5uTQq0dPjhh1KJddcDFPPfwoB40Y2dJN3qTJL77K3Okzue2341u6KUI0mvREiBYTiUQYc/iRAFRWVZGTnc0xRx7F72+/lVQ63cKt2zV89Ok0eg0b2NLNaHIrVq3kJxecV/e967p07tiJU044iSNGHUpubi5333o7Y88ex9fffduCLRW7k7/c9zf+ct/fWroZu7R7b7+Lg0ceCMCCRQuZ8MxEvvxqJmXl5WTFsujetSt7Dx7K4aMOpXVRUQu3Vohdm4QI0WJGH3o4uTk5APzu9lu57bfjKcjP57CDD2HSm6+3cOvEjiwIAmbNnbPebV9/9y2vvf0m1156BT//0TlEfJ8Lfn4eF1x5aQu1UgjRlA458OC6APHu++9x3qUXbXDB6dMvPuOpF55D3/I7jjzkMJavWNESTRVityDDmUSL+UHN0KVvZn3HU88/y9z58wAZ0iS2zZ//cS/xeByAA4ePRCnVwi0SQjSFIw85tO7rW+68fZM91sYYXn3rDWbPm7s9mibEbkl6IkSLaNO6NSP3Gw7Acy+/WPf/ZRdczMEjD6SwoBVrS0safP7F5/2KX5/3KwB6DRtITk4O5/zwTEYfdgRdOnUiLzePq35zPU+98Fzdcwry8znvnJ9xxKhD6di+A5VVVXw7exaPPPk4r739JqccfyK33XQzAAcfO5qly5dt9LV93+f0k09h9KGH06dnb/Lz86moKOfb2bN4YdIrPP3ic4RhuNHn1k4Mfur5Z7nqtzfQo1t3fvGjczhg+AjatG5DRUUF07/4nPsefpDPZ3y5wfO/X03ktpturmtzrT/XG1Kx/9778ug/HwJg3C9+wkefTlv/+b8dzyknnMSSZUsZddxR5Obk8rOzfsxRhx9J544dCYKAb2fP4rGnnuT5V15q8OcRi8Y47OBRHLD/CAb1H0CXjp2IRqOUV1YwZ95c3np3Mo9OnEB1zcl9c6qOx5kzfx6D+g8gJzubgvx8SkpLARgyaC8OO2gUew8ZRq/uPcjPzyeZTLJi1Uo+/vQT/vP4I8ypCbMN6d61G2f/cBzD99mPjh064vs+JaUlrFm7lq++/YYpH0zl9bff3OAER2vNyccez3FjjqFfnz0zr51IsKZkLctWLOf9jz/i9bff3OTrH3nIYZxw9LEMGbgXRYWFJFNJFi5ezJvvvsPDjz1CeUV5k7d7e+nWpQtnnXYGB+w3nI7tO+B5HquKVzNt+qf8d8JjzPjmqwaf26Z1a0Yfejgj9t2ffnvsSds2bXAcl5LSEmZ8/RUvTHqZl19/dbMTbLXWnHHKqfzguBPp1aMnWMvCJYt5YdLL/OfxRza7D98/Ln3ftv7+1+c4Dmed+kNOPOY4enbvgbWGhYsX89wrL/K/CY/Rtk1b3n3pNYANjoWN2Q+Azh07bbSS0cb2sVOHjpwz7iwOHD6Sju074GjNytWr+GDaR/xnwmPMmjN7i9vxfR3bd6j7euHiRVu9ne/zfZ+zf3gmxx11NN27dgNg7vx5PPPS8zw68YkGj+e1tmafH7n/IYbvs65i3iknnMQpJ5y03mO+X6igKY4hQjQlCRGiRZx49HG4rksYhnUnp8+98hKXnH8hvudx/JhjeHgL/mgDdO/SlX//7X66dOrc4GP26N2H//ztn7Rp3brutmg0yoFFIzhw+Agee+oJPvvyi82+Vt8+e3LfXX/ZoEJQUWERB+w/ggP2H8EZp5zKLy65kDVr12xyW6MPPZw/jb+VrFhW3W2RoiJGH3Y4hx08istuuIaXXpu02TY1lR7duvPQPf/Y4H3cb9g+7DdsH4buNZib/njLRp/7wF/+tt4fxFpFrQop2ruQ/ffelzNPPZ2fXfwr5i2Y3yztry8drDsR1toBWC8k1ud7Hrk5OfTp2YvTTz6F391+K488OWGj2z36iNH8afwfiPj+ere3a9OWdm3a0n/Pvpx64skcfepJ6w23yorFePCvf2e/Yfts+Nq5uXTv2o2R+w1nQN9+XHjVZRu8bl5uHvfefmdd8K4ViUQY1H8Ag/oP4KxTf8h5l1200ZPPrW339vLzH53D5Rf+Gt/z1ru9a+cudO3chZOPO4F7H7iPu/9x7wbP1Voz9ZU3cRxng/vat21H+7btOPKQwzj1xB/wqyt+3WCQbehnNLBffwb268/xY47m2t/9Zhv2cn3b8vufk53NQ/fex7C9hqx3e+1n4bjRR3PDzTc1WVu31MnHnsDNN/yGSCSy3u3du3aje9dunHriD7jr7/fwj4ce2Krt1w+4vXr05JtZ321TeyFz7H7onn8woG+/9W4fPHAQgwcO4sDhI/nlZRc3GECbe59rbesxRIjmICFCtIiTjj0eyEz8Xbl6FQBLli1l+hefs8/QYZx83AlbHCLuuf0u2rVtx8OPPcIbk9+mvKKc7l26sXRFpichNyeXh+75R12AeObF53l+0kusLSmhW5eunHPGWZxxymn03WPPTb5Oty5deOyBh8jLzaOiooL/Pvk4X86cwfKVKyjIL+DwUYdwxg9OZfDAQdx311/44c/OJgiCjW5rzz59OHb0GFYVr+bB/93JjK+/QinFQSMO4Jfn/IxoNMrN1/+GDz7+aL0emaNPPYm2bdry8N/uB+BP9/6FN955a71tr1m7dovet/pi0Sj/vPseCvILuOef/2DqRx9SHa+m/579uPjc8+nQvj0/Pn0cb737DlM+eH+D57uOw7ezZ/Hm5LeZ8fVXrFy9CqUUnTp0ZPShh3PMkUfRtXMX/vGnP3PcGWNJpVKNbuOWchyHXt17AJBMpSgtK6253aW0rIw3Jr/Fx9M/ZcGihcTjcdq2acvAvv348RlnUtSqkN9efT3zFszng2kfr7fdosIi/vjb8UR8n+I1a/jvhEf5bMaXlJSWEI1E6dalK/vtvQ9HHnLYBm369XkX1P3xf/Pdd3j+5ZdYtmI5yVSSosJC+u/Zj8MOGrXRExXf8/jvP/7JwH4DCIKAFya9zDvvTWHxsiW4rst+w/bhp2f+mNZFRTz4l79z/LixLFu+vEnavT384sc/4ZpLLgcyQxsfeXICCxcvpLyigh7duvPj08cxbPAQLjr3fEpKSzc4LtQOV3v/4w+ZPPU9vpszi7UlJWRnZdOlc2d+ePJYhg0ewkEjRnLTNTdw5W+u32g77hz/h7qf0eczvuShR/7LgsULaV1YxA+OP5FjR49h/PVNEyK29ve/1p9vvb0uQHzy2XT+M+FRFi5eRGGrVpx4zPGcdMxx/P76G7e6fY888TiT3niNy351EUceevgGhQw25pADD+a2m8ajtaayqooH//cwUz/6gDAMGbbXEH75059T1KqQKy+6hPKKCh6duPGgvilfffsNR4zKDGn67dXXc/7lv95kj/WW+Psdd9O7Zy/+/ej/ePPddygrL6Nnt+5c8Itf0qdnL44YdSg//MFYHnvqySbd56t/ewNZsRgP3Xsf7du24/W33+TOv/11ve3XD7zbcgwRorlIiBDbXb899qRfzQn7szVDmWo9+/KL7DN0GIP6D6B3j55b1C27R6/e/PSi83nvw3UntzO/+bru64vPO5/2bdsB8Pvb/8C/H/vfeo975Y3X+Nvtd3HkZkqC3n7TLeTl5jHzm68554Jz64bI1Hrvw/d5e8pkHvjz3xg6aDCnHH8iE555aqPbGthvADO+/oqzzvsplVVVdbd/PuNLFi5exF03/5Hc3FxOPPY4Hnrkv3X3z5o7h6rq6rrvV65a2SRXjosKi/A8j1PPOXO9McQzv/majz79mJcnPEM0GuXMU3+40RBx9W9vYMFGhhd8MXMGL7/+Kk88+zT/vvc+evXoyYlHH8eTzz29zW1uyBmnnEp+Xj4An34+vW4owuSpU3h+0kskEon1Hv/1d9/yznvv8u/HH+HxBx6m3x578utfXrBBiDj0oIPJzspcNf7RL3+2wfs+/cvPeeal5/ntHzfs7TjmyKMAePn1V7no6ss3uP/d96fyj4ceID8vb4P7Ljr3fAb2G0BZeRk/Pv8X6322M/v4Gc+98iIT//0I7dq05YoLfs1lN1zTJO1ubr179OSyCy4G1h+GV2vmN1/z4quvcPvvbuHkY4/nsgsu5pmXXlhv2FYYhhz5g+NYuHjxBtv/ePonPPX8s/z6lxdw8bnnc9Kxx3PvA/dt8Fk95MCD637/357yLudddtF6Q1jemTqFWXPncOn5FzbJfm/t7z/AEaMO5ZADDwZg0puvc+FVl6134vju+1P5+ttvuO6yK7e6fWtK1rKmZC3lFRXAxgsZ1Oe6Ljff8Ju6k+kf/uzH6/USfD7jSya99XrdZ/TaSy/nlTde3eAYujlPPvs0v/jxOWTFsthn6DDefek13n7vXT6e/gmfz5jBt7O+Jd3AhZuGDBowkHN+de56Qz2/+vYb3v1gKq9OfJ42rVtz5qk/3CBEbOs+L1m2FKDuQlN5RcUm3+NtOYYI0VxkYrXY7monTsfjcV79XhWml1+fRLLmKvWWTrB+6oXn1gsQ9fmeV7eWwhczZ6wXIGoZY7j+5t9tcHJZ3z5Dh7H3kKEAXPmb6xv84/fu+1PrKkudcvxJm2z31Tf933onELWef+UlVqxaCcC+Q/fe5Daa0l1/u2ejkxAXLl7M6zW9HfsMGbbR524sQNT3/scf8ubkdwA48tCmv+LtOA7dunTh8gsu5v+uWHcC/c//PFT39crVqzb5M66srOTuv98DZN73gvz89e5vU5TpySotK9vkH/tkMkkymVzvttY1vWCffDZ9k/tRVr7+nIasWIyzTvshAHf9/Z4NAkStZcuXc88/7wPg6COPIhaNNUm7m9vPfnQOvufx5VczGyyNaq3lpj/eQjKZJCc7m6OPOHKDx2wsQNT31/v/zpqStWitOXzUoRvcf9apmfc4mUxy3e9/s9Ex8Pc+cB/fzZ61Jbu1Rbb293/c2NOAzPHz/27+3UavPD/4v4eZuYk5JE1t9KGH112oufeB+zY6zGjZ8uX84e4/AZAVy2LsCSc3+nWWr1zBxddcWfe+xWIxjjnyKH579fU8+7/H+WLKRzz2wL/5yZk/2uKT6f88/sgGc8Ug87s48flnAdizdx9yaioJ1tpe+1xra48hQjQnCRFiu3IchxPGHAvAW1Mmb/BHtKy8nMnvTQEy8ya2pLLO86+82OB9g/oPrLsq/dzLDT9uzdo1TPlgaoP313ahz50/b7MTAz+e/knmtQcM3Og4bYBvZ8/a5AlJ7doGm5rn0ZSMMTw/qeGJ07Unr60KCsjNyd3s9goLWtG9S1f26NW77t/a0swwq359Nj1sbEvUTvSs/Tdr2he89dwr/Opn5+K6LsYY/nTvX3j3/YZ/prFojE4dOtKnZ6+6NtYfftbve8PbalfALsjPr/s8bKnVNc89dvQYotHoFj9vv733JS83czL0yhuvbfKx02o+d77nMbB//yZpd3M7/OBRAJst6VxRWcF3Nb93Q783D+D7lFK0bd2GHt261/1ce/foyYqVmRPz7/9ctdbsv09mmMiUD99vcKVzay1Pv/j8ZvdpS2zt77/jOHVDWt79YOomh/I889ILTdDSLXPA/pm5OsYYJj73TIOPe+X1V+t6kUbuP7zBx23K21Mmc9QpJ/DvR//HmpL1h25GIhH2G7YPN1x+NW8//wonH7v5C1GbKhhRG8S01nT53jy47bnPsPXHECGakwxnEtvVQSMOqJub8OzLG/8j9+zLLzD6sMPp0L49I/bdj/c//miT2/x2E3+M9+jdu+7rhq7i1prx9VcNDmka1G8AkJnMt7EqJRvjex4Fefkb/KED6srZNqSsrAyA7KzsLXqtbVVSWkJpzWtuTGn5uvtysrOpqKzY4DF7Dx7K2Wecycj9htOqoKDBbW3qvm1VUVHBB9M+5sFHHt7oFbtWBQX89KyzGXPYEXTv2g2tG76O0qqg1Xrfvzn5bcrKy8jPy+fvf/ozH306jTfffYdp0z/l6+++xRjT4LaefuE5Ljr3fPYeMpTJL7zKy2+8ygcff8Qnn03f5IngoP4D6r7+6PXJm9r19dT2Pmxru5tTxw4dKCrMLAZ21cWXctXFW7aeR5sGFhA78ZjjOO3EHzB44CBisdhGHwMbfv66du5SN7l5xleb/t3+4qsZW9TGzdna3/+unbvU7duWHM+2lz169QFg8dKlm/w8p4OAr7/9luH77scevXo3+LjNWbFqJb+/4w+M/9Mf6b9nX4YM2ouB/Qaw79Bh9OjWHYD8vHzu+P0taEfzVE2PwsbM3UShh7J6x73s7PV/Ftt7n7f2GCJEc5IQIbar2rUh1paUNHiV+O0pk+tOek4+9oTNhohNdd/WXsUFNnoyX9+mDsSFhYWbfG5DGrpitKlhNUDdiZ3jbJ/Owvhm2mPrnWhu7MT7+yUhN2VTJ3hb6vsTPYMwpKKygtXFxQ0+Z2C//jx0z30UtmrV4GPqi36v2kppWRnnXnoRd99yGx3atWfEvvszYt/9gUx4eX/aRzz53DO8PWXDk/17HriPdm3bMfaEk2hdVMSPTx/Hj08fB8CsObOZ9NYb/O+Jxzeo6FW0lZ+7WL3P3ba0uzkVtdq61YSj0fU/P77v8/c77q6bJ7DZ50fW/52sP2xtc8eI4jWbrri2pbb297/+EJ21mzuelWy/E8vadq0p2fz7s3pN5ne0IC9/M4/cPGstX337DV99+03dbQP79eeGK66uGwp23aVXMumN19abS1bfpn4WxqwbKubo9XuVt/c+b+0xRIjmJCFCbDc5OTkcfvAhABS2asV3H3++2eeMPuwIbrx1PPFEw+sLbI8rqU7NifPX333L5fUmrW5ObeWpXdnI/favCxALFy/mgf/+m08+n86yFcuJx+N148sv+eUFXHTu+U3ympub6Pl9nuvylz/8icJWrUil0/zn8Uwlr/kLF1BeXl5XOrJLp86880KmrObGhtJ98tl0DjvxGMYcfiSHHHAQ+w3bhw7t25Obm8tRhx3BUYcdwbvvv8f5V1yy3slJEARc+7sbefC//+b4MccwYt/9Gdh/ABHfZ4/efdijdx9+euaPufyGa3hj8tt1z6t/4nL8GWMbrPb1fctrhu5sa7ubU/0T5L/c/3deef3VLXre90u0XvCzc+sCxIefTON/TzzGV99+w+riYhLJRN2cgcce+HdmKNAmhkhKZZtttAO8fTO/+ZqfXPBLXnx8It27dqMgP58D9h/Ba2+/2TwvuJ32eWuPIUI0JwkRYrs59sijGj2WMyc7m6MOP4Jnt3J8b/0qLkWtClmwaGGDjy0saPgKdWnd8IKsFqmjvyM7/eSxQOY9Gnv2uAZ7dPLzt/3K49Yasd/+dOvSBYDf3DqeJ57deNWsLblSmEqleP6Vl+rGUnfu2IlDDzqYH58+jp7de3DwyAO5/IKLuflPt23w3Dnz53HX3+/hrr/fg+/77DNkGCccfSwnH3s8OdnZ3H3LbRx64tF1PSq15Wkhc2W5dsLt1tiWdjeH0nrFCYJ0eqt/r0476RQgMxfprPN+2mAQaOhnW78ns3XhpntHWjcwlGp7qd/Wwlab7qXa0h63plDbrqLNvH9Qb6J/ecPDJ7dVPBHnhUkv11206Nala5O/Rkvtc2OPIUI0J5lYLbab2mpLK1ev4tfXXLnZf8tXrMg8bwsmxzWk/onJwH79N/HI9ceff99X32W6y7t06tziJxJ2R7jcV0+fnr0A+PCTj7d4fP/21qfnurHIL732SoOPG7gVbVyybCn/nfAYJ//oh3Wf2dpyjJuSSqV4/+MPueam/+MPf85UcInFYhx20Ki6x9QfplFbHaypbG27m8qipUvqQv7W7ltBfj5t27QB4JXXX2swQGTFYnVj5Tdox5LFxGt6NwYN2HAF5vr26r/p+5vboiWL63qKtuV4tqW29Fgza25m0nuXTp02eTHGdV369+1b85zmvRizcvW6CfLN0cPUVPu8LW3bkmOIEM1JQoTYLjp37MTegzMnCq+++TovvvbKZv9NeitTsWXEvvvRrk3brXrdGV9/VXeicuIxxzX4uKLCIg4acUCD99eWJ9Vac84ZP9qqtjSVZHLdQm3+91YgbgmOm+nQzNrEXIf+e/Zl6KDB26tJG6hfJauhORlKKX74g1O2+jUqq6r48uvMxNzvT8renPrzfuo/t3bRP4Czf3jmVrdtU7al3dvCGMM7NZXYDhw+kl49ejZ6G46zrjN9U3NtTjv5FLzvrYZdKwzDuhKfBw0fud6q9vUppfhBTbnolhKGIR9/9ikAB484YJMnryfXLOi5LWqPNb636ePM1I8+BDLHx7EnntTg444+/Mi6eWrv1zynudQPUYuWLmny7TfVPteWNN/WY3lDxxAhmpOECLFdnHzcCXUTcl95Y9PlHGvVlrR0HGeTAWBTUqkUz7yYGQo1eOAgzjnjrA0eo5Ti5utv3ORQq/c+fJ/PZ3wJwC9+fM5mr9ju0bsPhx3cPFeDSstK6/7wdO3cpVleozFqh4jtPWRY3ZCh+goLWvGn39+6vZu1nvrrWDS0fseVF13CwH4NX709aETDJ5iQmfOzV82V7CX1Tlry8/I2+1k4aPjIuq+XLF1a93VFZQX/nfAYkLlaf8MVV2+y7HFRYVHd8J5tbff28PeHHiAIAhzH4Z7b7qyru78xWmtOOPrY9R6ztmRtXQWd48ccg7+RoDCo/0AuPf+iTbbjkZqVhCORCOOv/81Giwec/9Nf0LfPHlu0X82pdtGzWCzG76+/caOfh5+ddfYmP8tbqrbcbVFhYd2ChRvz+ttv1g21+9VPz2WP3n02eEyHdu255tIrAKiOVzPx+YbLojbk99fdyPk//cVm14A4YP8RdUU8qqqref+jDxr9WpvTVPtcW7p1U8fybTmGCNGcZE6E2C5qr4oVr1nDtJoraZsz/YvPWbl6Fe3atOXkY4/n/of/tVWv/ef77uXoI0bTtk0b/u/KaxjYrz/PvfIia0tK6NalK+eccRZ7DxnK5zO+ZMigvYCNd+Nfev3VPP2fx2hVUMBf//gnTjzmOF56bRILFi3EGENRq0L69+3HYQePYtheQ3jgP//mrXebvuJNGIbM+Gom+wwdxtgTTubrb7/h61nfEQSZycGlZWXbdcGhZ158niNGHUp2VhaP/vPf3PfQg3XlJ4cNHsJPz/oxbYpaM/2Lzxk2eMh2a1d9U96fSvGaNbQuKuKyX11E546deO3tNygpLaVbl66cfvIpHLD/CD75bDr7DN34gnrHH3UM9999L1M//ID3PnyfWXNnU1pWRnZ2Nnv06s2PTh9Hh3btAXj0qSfqnpeTncM/776XxUuX8Opbb/DFzBksXb6MMAxp07oNhx88qu7Ef/nKFbw15Z31Xvfuv9/Dfnvvw9BBg/nJuB+x/977MuGZiXzz3XdUx6vJz8ujT6/eHLDfcA4+4CBmzZm93pyPrW331mhTVFS3uOOmzJ43ly+/msmsObO59e47+L8rrmGPXr155clnePzpiXww7SOK16whEonQuUNHhu41hDFHHEm7Nm05+tST6k7erLU898pL/Pj0cfTbY08m/Ou//Ot/D7Ng0SJyc3MYdcBBnHXqD6mKV7Nq9Sp6du+x0fa89e5k3pj8NkeMOpQjRh3KEw/9l4ce+S8LFi2kqLCQU44/ieOOOpovv5pZF7haymtvvcG7H0zl4BEHMObwI3n8gYd5+PFHWLh4EYWtWnHiMcdz8rHHr38828ohM9O/+BzIXMj5/XU38p8Jj1JSb8hi7SJ/6SDg+vE38c+77yE3N5cn/vVfHvjPQ7z/8UeEJmTY4CH88pyf1w0FvfWuPzV6tWrIlOcdN/Y0Ljr3fCa/N4WPpk9j1pw5lJaV4jgu3bt04fBRh3LMkUfV9T7e+be/bHRRv23VVPs8/YvPGbHv/gweOIjzzvkZk6e+RzyR6X1MJJKsXL1qm48hQjQXCRGi2e09eGjdxLbX3n5zi/+gWWt57e03+dFpZ7BH7z4M7Nd/s7XRN6asvJyfXPhL/vP3+ykqLOLk407YYDXsic8/w7TPptf90a0/ZKjWoiWLGXvOmfzt9rvYs88edSccDamoqmx0W7fU3x96gH8OvofCVq24+9bb17vvz/f9rcHVf5vDpDdf58nnnuHUE0+mfdt2/Obq69a7PwgCbv7TbeTl5bVYiIgn4lxx47X8409/IRqNMm7saXUr/9b6cNrH/PaPNzNp4nMNbsf3PA496GAOPajhcqKPPDmBhx97ZIPbu3TqzM9/dE6Dz1u5ehW/vOziDaoPpdJpzj7/F9x2082MOfxI+u/Zl5uuuaHB7VRu5HO3Le1ujF49enLbTTdv9nEPPfpfvqxZk+Hfj/6PeDzODVdcTV5uHuee/VPOPfunG31eMpUimVp/Ve0/3fsX9h48lAF9+7HXgIEb/D6UlJZywZWXcskvL2wwRABcdv3V/Ouv/2CfocMYOmgwQ/+w/vC7md98zQ0338Tzjz652f1rbhdffQX/vvc+hgzai32GDtsg+M785mt+84fxPPdIJhTW9lw21gfTPmL6l58zbK8hnHjMcRv0CPcati5QvfPeu1z92xsYf/1vyM3J4dJfXcSlv1q/BygIAu76+z08WtPz01grV2Wq3UV8n9GHHc7owza+rg9kSrfe/Y97+fej/9uq19oSTbHPjzw5gXFjT6dVQcEG66V8+Mk0zjz3J3Xfb+0xRIjmIiFCNLuTj1s3NndzK9N+36tvvs6PTjsjs51jT9iqEAHw7ezvOGrsifzynJ9z+KhD6Ni+A5XVVcyaM5sJT0/khVdf4Zxx64Y6bWwxNcgM3TnujLEce+RRHHX4kew1YCCFBa3QjkNpWSnzFyzgk8+n89rbb643KbapvfPeu/zolz/jnDPOYtCAgRS2KtzoUI7t5Zqb/o8Ppn3ED38wln579MX3PFavKWba9E/5z4RH+fKrmVy8hetINJcpH7zPSWedznk/+Tkj9t2PwlaFVFSUM3vePJ5/5UWeePZpOrbv0ODzx//pNt776ANG7Ls/ffvsQZvWrSlsVYgJQ5avXMFnX37BhGef4tPPP1vveUuXL+Oks37IIQcexLDBQ+jUvgOti4rIimVRXlnBnHlzeevdyTz+9JMNXjGtqq7mgisvZe8hQznluBPZZ+gw2rZpSzQSobKqikVLFvPFVzN4Z8q7TPnw/SZp9/Y04ZmneGPyO5xxyqkcNHwkPbp3Jy8nl1Q6zcpVK/luzmymfvQBk958fYOruZWVlZz20x/xszN/zDGjx9C9S1eCmn175713+fej/9uiqlZV1dWMO/cnjBt7GicfewK9evTEWsuiJYt56bVJPPTof9dbxK8lVVRWcPrPfsxZp/2Qk445nh7dum/Q1l71AlNDx7PNsdZyzq/O5dyzf8phBx9SszBfrMFFGp9+8Xk++vQTfnLmjzhw+Eg6tu+AVopVxav5YNpHPPz4o8yqWXl8a/z+jj/wwP/+zaiRB7LP0L3Zo1dvOnXoSHZWFkEQUFZRzpx58/jwk4959qUXWL5yxVa/1pba1n1euXoVP/jxGfzyJz9n/733oX3bdhsMrW2KY4gQzUH1HDpgxyr1IkQLueX/buL0k09h+YoVHHjMES3dHCGE2GonHnMcd47/AwCHnnA0i5YsbuEWCSF2NTKxWggyEyqPOCQzNOmzGV+0cGuEEGLbHH/UMQCsWbtGAoQQollIiBC7hU1VvtBa8/tr/4+imsWbnn7x+e3VLCGEaLR2bdoSiUQavP+0k06pm/9SW51OCCGamsyJELuFC39+HnsNHMSLr77CFzO/ZM3atUQjUfbsswc//MEpdeUQ3/vwA96e0vQVlYQQoqkcOHwEV//6Ml58dRIffjqNZcuXoZSmW+cuHDt6TN2E49XFxfz9oX+2cGuFELsqCRFit9GnZy8uPf/CBu//5LPp/PraK7Zji4QQYusUFRZx9hlncvYZG1+EcOXqVfz84l9RWla2nVsmhNhdyMRqsVvo0a07Yw4/kgP2H06nDh0pbFWI57qUlJUy4+uveOm1Sbz46itbXU9dCCG2l1YFBYw5fDQHjziA3j17UtgqsxhceWUFc+fP4613J/PoxAlUVVe3dFOFELswCRFCCCGEEEKIRpGJ1UIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBQJEUIIIYQQQohGkRAhhBBCCCGEaBS3pRsghBACfv6zn9C5c+eWbsYOb8mSJTzw4EMt3QwhhNjtSYgQQogdQOfOnenTp3dLN0MIIYTYIqrn0AG2pRvRGPvtty9jT/kBsVi0pZsidgN5eXlorTHGUF5e3tLNERuxq/yM8vLycF25rrM5QRDs1D/nWrvK53ZXJT8f0RLi8QQTJz7Fx9M+aemmbJGdLkTc9sdb6dSpY0s3QwghhBBCiCa1dOkyrrr62pZuxhbZ6S571fZAGGMoLS1t2caIXV5BQUHd1Sj5vO2YdpWfkfREbJldpSdiV/nc7qrk5yO2t9rP3M400man/YtVWlrKRRdf2tLNELu4v/7lLgoLC+XztgPbVX5GMrF6y+wqE6t3lc/trkp+PmJ7q/3M7Ux22hAhhBC7kl3hxFgIIcTuQ9aJEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEEIIIYQQQjSKhAghhBBCCCFEo0iIEGIHZG1Lt0AIIYQQomESIoTYQVkrYUIIIYQQOyYJEULsgJTK/G8tGKMwpmXbI4QQQghRn4QIIXZQSq0LE6AIQ40xalNPEUIIIYTYLiRECLEDUwq0toBFobDWwYQOYdjSLRNCCCHE7kxChBA7Aa1BOyFKhTVzJSKEgSc9E0IIIYRoEW5LN0AIseW0tqBDjAFrHEzoYw0onarpsRBCCCGEaH7SEyHETkjrEKVTKEzNEKcYQRDBGPmVFkIIIUTzk54IIXZSWgM6jTEB1niYMIIxPkYHKJXAcaRnQgghhBDNQ0KEEDu5zBCnFEqHmDCKDT0MUaxJop24DHMSQgghRJOTECHELkLrEK2rCEMXE+ZgTZQg9NFOGu1U7/JhoqCggL/+5a6WboYQW6SgoKClmyCEENtEQoQQuxjHCdC6FBNGCINcTOhjwiy0W4XW1ZlhULuQeDwBgNaawsLCFm6NEI1T+/kVQoidjYQIIXZBSoHjJlE6hQmzMWEWYTofo/LQbgWOU1VvIbud28SJTzF27CnEYtGWbooQjRKPJ5g48amWboYQQmwVCRFC7MK0tmhdSairMWEBNowRpgoIVQGOV4brVrZ0E7fZx9M+4eNpn7R0M4QQQojdyi42sEEIsTGOY/D8tbj+apQOwHqEqdYk4x0JgpyWbp4QQgghdjLSEyHEbkQ7KXxnJWGQRRgUYkyMIJWNSSfRXjGuW93STRRCCCHETkBChBC7IcetRjvVhOlWBEEhxkYwie4YncDxV+BImBBCCCHEJshwJiF2U0qB65fgR+ehnTJAYUwWqXgPktU9MWGspZsohBBCiB2U9EQIsZvT2uJHVmG8UoJUO0xQgDH5JOP5aKcUz1+OdnbNMpTWWtLJFInKapLV63pfIllZRHOy8CI+alcpYyWEEEI0IQkRQggAtE7hRxcTBmtJpzphTTZh2IqwujWutxrXX4rW6ZZuZpMwYUj1mjKKV6yq+76+ijWlaMcBoHX7tmQV5dd9L4QQQggZziSE+B7HrSKaNQvXn4ciExqCdBsS8SGkkt0xxmvhFm6bVFWcaKC484+3M3jw4AYfp4Ahgwdz1213EElnnieEEEKIDAkRQoiN8vwyIlkz8CILUSoNOARBexKJoSRT3TFm57oyb60lrEwwcui+fDrtE84880ymf/opb7/1Fr1798Z1XVAK13Xp3bs3b731Fp9++injxo1j+iefMnLovoSVCay1Lb0rQgghRIuTECGEaJDW4PmriGTNwHWXAxZrNUHYmURqX1LpThizcxxGylcUc86ZP2LC44+TlZVVd/vBBx/M7NmzqaioAGupqKhg9uzZHHzwwXWPycrKYsLjj3P2uLOoWFHcEs0XQgghdig7x19/IUSL0jrEjywkGvscxy0FwFqXdNiDRLA/qbATxrRsGzelYm0Ja1auYp+9927wMdFodL3/N6Zf374Ur1xNxdrSpm6iEEIIsVORECGE2GJaJ4lGviUa+RytyrBKY/FJh71JmOGkTUd2tNE+xhhKlq0GCy+88MI2bWvChAlgLSXLVmF25NQkhBBCNDOpziSEaDRHVxKLziAI25AKe2CJYcgiafqSVl3x1Hw8vbKlmwlAyfLVBOnMBPEpU6Y0+LggCOr+d92NHxo///zzzGPSaUqWr6aoU7umbewuICsWo1uXrvi+TyqVYuHiRVTHZVK6EELsaiRECLETszazaFxLcZ3VaLWawHYhTQ+sdQnJItSDSVOOZ2fjqTUt1j5rLVWlZXXfl5SUbPRxDz74IBdceAEoyM3J4d6//Y2f/vSnGzyuqqpq3del5RIiavTu0ZNxY0/ngOEj6NmtO1qv6+Q2xjBv4QKmfvgBj06cwJz581qwpUIIIZqKhAghdlLW1v5TWKsAQ0ssZaA1+CzGNctI05O07ooFQvIwehhpXYkffovLxk/gm1M6kcSE64YdrVixgoULF9KtWzcgc4J7wIEH8vFHH9UNT0okk5z385/z0D//yeSpU+tOiD/99FNWr15dty0ThqTiCfxYw3ModnWdO3bid9fewKgDDqJ4zRomvfk69z/8L+bMm0s8kSAWjdK7Zy/26j+QY0eP4ewzzmTy1CnceOt4lixb2tLNF0IIsQ0kRAixk1KKuvkHCoUxHoFRaG2xhDjO9h2zr3VIhNl4dgkp9iBNO6x2CVUBcXc4Dmvww+9wbdnmN9ZEElXVdQvJaa3p06cP3bt3B2DIkCEsW7aM1cWrsWb9iRyBtXz44Yd0bN+eSCzGokWL6p7z5ZdfYozBhCGJqurdNkScdtIp3HDF1ZSUlnDJdVcx6Y3XSNcMCavvi5kzeOr5Zxl/xx8Yc8RorrzoEl5+4hnG3/FHnnj2qRZouRBCiKYgE6uF2IlpDVpbtBOinczJchh62DCbdCqXIB3b7us5aBUnyhfE7Ec4lNbdHrjtiEcOptrbm5CshjfQhFKJJABKKYYOHcq3336LtZZPP/2UAQMGsGrVqg0CRF17gZWrV3PcccexfPlyrLV89tlnDB48GFUzhiyVSG2X/djR/Opn53LrjTfx4qSXOea0k3lh0ssbDRD1pYOAFya9zNGnnsSLk17m1htv4lc/O3c7tVgIIURTk54IIXYRWhu0ThGGAdb62DCKNT5hkItSoHUc7Vajdbhd2uOqMtzwA9KqHSm3L4Y8AAK3I0GkC16wiEjiazSJZmtDkE6jlKJHz558+OGHdbcPGzaM//3vfzw5cSKpZLLB52dHo9x7773r3fbxxx/Td889mTd/PmHNhO3dyWknncLlF1zMnff+hXsfvL/Rz6+qrua68b9l2YrlXH7BxawuLubJ555uhpYKIcSOrXZYslJgGrigtSOTngghdjGOY3DdBK5XinaqUcpgjUuYLiSV6Eoy3oUgVUQYbp8eCs+uJJaeTCT9Fdh0pvsESLtdqcw5kkRsKIZI87y243HggQcyd86cjVZc6tix4yafv/ewYRvc5rouc+bO5eCRI4no3esQ2rljJ2644momPD1xqwJEffc8cB8Tnp7I/115DZ07dmqiFgohxI7NGDBGE4a18xkzPdstWSRla+1efwGF2I1oDa4Xx48W4/pr0G4VWI0Ns0inOpCsHkSiug/pVJtmH/KkAT+cR1bydfxgHgqLBazjkYz2oqrgaBJZAzB4Tfq62fm5XH755Q3e/9vf/Ga9SkL1eVpz2513NvjcS664grMqqzlz0VLUbrJmxO+uvYGS0hJuvvO2JtneLXfdTmlZKb+79oYm2Z4QQuyIjFGY0CEMfIxxsVaTCQ8WrS1KUTdMdmciIUKI3YDjJvEixfixBTjeWpQKUIAJ80mlehCP700i2Z900AZjmu9A5hASTc4gu+o1vHBpXa9EqFyS2QOobHMciax+hDRNG3TE4/EJExq8/+yzz8ZpoKSV67rsv//+DT73pUceYUAqxag1pdw34ztGr2q5UrbbQ+8ePRl1wEHccc+fqaqubpJtVlZVcftf72bUAQfRq0fPJtmmEELsCIxxCdLRzNzEsHZ+okWpEK0DHMews3dm7+TNF0I0htYhXmQ10exv8WLzcNwyFAqFJgwLSYb9iJsDiIcDCWwbwmYaoqltnKz4NLLL38YNijMHUqWwyieZM4iqDieRyNkTs41hwo9G+OTTTxpcXXr69Omk02l69+5Np44dad2qFV06dGCPnj2Jp1J89tlnG32eMYavp02jKxABosZwztIV/OOrWQysqNymNu+oxo09PVPG9Y3XmnS7r775OsVr1nDm2NObdLtCCLE9GQNh4BOks0kn8zFBDKwHFrROo50UjpvGcexOOXRpY2RitRC7Kdctx3XLMcYnCNoTmPZYFcPiE9COQHVEOQaHVbhmGa4tbqL+gXptCNfgVrxDKtKFZM5eGCcHHDBOjETB3iRz9iRa9Q1exeytvuKRsiHPP/88J5100nq3x+Nx9t57b1544QWOO+64DZ734osvMmzYMKqrq4nFYuvf99xz9CstJQJ170kEaJtK8/u5i5ibHeO2rp1YFfG3stU7ngOGj2DSm69vtgpTY6XSaSa9+TrHD92b6vmLqfA8VkVcVkZ85kWjrHJdzM5+uU4IsUsyRmFMFoQ+xnqAQSkDyoBKoZ00Wu+6w10lRAixm9M6he8vwrOLCExrQroQ6NagwCgP43QlrbuhdIBrVuCmF+MFxU3aBj+5GDe5mFRsD5Kt9qq73UZziWeNIJXfj0jJZ3hVixsdZHTM54xx4wDIyc6mX79+XHjhhfzmN7/hwAMP3GiAADjuuOMYOXIk++yzD3fffTf/fuAB3psyhZLSUpww5MFUitqI4FEvTFjLgMpqHvp2Du8WFnBnp/akd/KT4OysLHp26879D/+rWbY/45uvOHPsaRyYDomUluMoRRYW1wdXg5erKXM1iahmpetS6WqW+B7FymOB9lliPebZCHFqxxkLIUTzMMYjDKJYk401XqZ4CQal0mgngXbi260KYkuTECGEADKVITynGI9ijI2Rsl0J6IxVWaA1xomQ9HuSyt0DZavwUkvxqhfgpptmJWoNROOz8BPzSeUNJJnbB6szC7kFXh5Bp8Nwk2uJrv4Ur3rZlm/XcchtW8iaJcspjseZMmUKU6dOxRhTt4hcQx577DG6devGcUcdRdpmJoPnAOcCRfUeVxsmHNadwuYZy/FrShhVVc5/27fhsfzCnbP8BtC1cxe01syZN7dZtj977hyU1vi9e8MXX6DIjKOrGeVG1BgcY/GCgA4qjYcldAFHoX1IOeBFoNLRGAfWeC4VSlPiuKwMXYqNy+K0x4qkx7xqnzUpFyOjeYUQW8iEEcIwHxNEsUTABihlgQDtVNWUUG+4XPiuSkKEEGIDmQXjvsMEswhMJ9LRnhjdGo3CAPi5JKP9SBQOwLFVuFUL8Evn4KYrtv21bZpo2Wd4lbNJFA0jnd0tc+6tFGG0iMouR+Kki4mtmIZXvWqLtplbWEAqnqC8uARrTN0ciQMOOGCTQeLAAw8EIFWzNHgWMAY4jHUHzyjrgkNtbSlP1dymoK0NuWLFCk6vLOGWNu35OJKzxe/FjsL3MzEpnmieNT0SNWt16EgEy7r3Uyk26Fiof9+6GgCZKie+snjKku0nCbXGjSVIKEUkYkm6Gt8zhD6klSYdVRSnHZJaszLpUhk6LE+4rKp2WV7psbTcY2mpTzwtvRvbKisWo1uXrvi+TyqVYuHiRVTH4y3dLCE2KUxnEYatMGE+1uqao0AadIh2Epk5hbp6p58cvS0kRAghGqSx+GYJfvUSgmQeqVgf0m6XTO+EkzlTDv08wpyhJDsMQafL8MsX4K/+Fie1bRV8nLCS7FXvEvhFxNvvT+i1rWmUIszuQGWvE/DKFxFdPR23evPDqwo7tsMaQ2VJOSbMdDUvXbqU+++/n3PP3XDl5Pvuu4+lS5euey8ch2h+Lvul0/gVVUDm1LL2IOpSf0hT5hvtrjsR3tMk+e+qhUzNyeb6vI4sd3ae+RKpVGZl7lg02izbj0Yy64TYVE2YqHn/FGBVJiDYuvSwrpeidsCAVbUVANbdVzdzo+b5SlksCq0sKMh2DI5niUQt3XQK17UQsyStgx+zxFFEYpaKQJO2ihLrsKbSpTztsLLUpSTusKzYY3Wpy6IVPmUVDsbsxmcT39O7R0/GjT2dA4aPoGe37uuVUjbGMG/hAqZ++AGPTpzAnPnzWrClQmRYC2GYTxgWYtP5GOuhCGqORQHaqUQ5JThuGVrvfAvDNQcJEUKILeKG5biVn2IqPyeV3YN0/p4E2UWZMz2lwVGEfhHVrdoR7z0Ct2oF3uo5RJbPQqe2/qqjm1pD7qKXSeV0JdFmGGF267r70q26kG7dHa9kHtElH+OmyhvcjlKK1l06EsvNoXjJcsJ0gDGGa665ZqMh4tprr63rsXA8l9adO5BdkMc/gMJkivMXLWWvynVBqbYXIkLmvNUq8GvOmxw/c/JqFYw0VbxRNoeJ0XxujnYgtRNcxlq4eBHGGHr37MUXM2c0+fb79OqNNYb07Dl4rCsbWL8nonYkmAKMWvd+1t0IaAUG0Kp2QBR1oUNpi0Gtf1/tQ+ruy5xI1BfxDTEHCrJDOhSl8bMhHiqiWZaUBuUobBQqUg5x7bCyNEI87bKi2KeiwmFVsc+aYk3JWk3xCkXpGkWq+RZpb3GdO3bid9fewKgDDspU83rzde5/+F/MmTeXeCJBLBqld89e7NV/IMeOHsPZZ5zJ5KlTuPHW8SxZtnTzLyBEE8pMjC7MzAcMC1C13Zs2cxlC6TiOtxbHLUHrdAu2dMckIUII0SiakGjVHKJVcwiirUkU9iPdqjvoGDgKhcVoTbqoE+k2HakafChexTIii77BX/gdOkht1ev6lYtwKxeTaj2QRJu9MF4E5WQOYalWPUm16Ym/Zg6xhR/ipBvuBckuyCOWm03Z6rVUrCmhtLSUe++9l5EjR6K1xhjD+++/T2lpKa7vkVvUivw2heh660msjfjc3KcHneIJLl24lD3jmbNCpdbNj3C9mhNfDVEnc2aa9hQ+FgfLqaaUYxMV/DnSmv/qoh16vkR1PM68hQvYq/9Annr+2Sbf/qB+A6j67jtsVaaHR0NdQFDfCwpKsUEIWK+3oeYJVq33tPWfV3tjTVrRKtOrkfnWrvcYR0OIQpPpyci8Ts3zHAjtuhydk2OwkRA3aunQXRGYkNCBeMJB+S5VCQ/lO5RWesSrFBVVLmVrobpKU1JsiZdb1q4yxEsDKlYFJCrCjezsjuu0k07hhiuupqS0hEuuu4pJb7y20WpeX8ycwVPPP8v4O/7AmCNGc+VFl/DyE88w/o4/8sSzT7VAy8XuxBiHkHYEpghjCrBW1S0YagnQKon2V+O5xWhnF078TUBChBBiq7mJYnKWTcGs/JhkUR9SHQcR5hZkZk5oLzPTWEOqXTfSXbrDyMPxVy8ksuBb3Fnf4TRypWeNJVo8A3/tt8TbDyPVfiAoJ1NOz/FJte1LqnVv/DXfkbXgY3R64z0g2nFo1b4NBe1aE6+s5uY7biMaidScImbG6Lfv1Y1oTtYmVxFdGotyRd9e7FlVzRULl9E7mQQFVmfmRQC4/rrx+15tmHBUZuy+DblGreRsVcJvaM9Uchv1fmxPUz/8gGNHj2H8HX9o0jKvvudxzGFHEH/0UdbLC9+fC1FvGFNQe7Gw9mS+3jCmtFI42A16MBwsKRROvW2vyxKWoGZjdUGhNmBoS/C9BRiVtjW13y3poGabdXfWPq/mYqbDunkeNfdFsxXa1WS1dshrp1G+RzzlgOuQsB5BSmEcn+pqSAcO5SWGdMJSWWpJlKZJlAUkSpIkS1MkihOkSxPYdMuWkfzVz87l8gsuZsLTE7n5ztu2aEHCdBDwwqSXeevdd7j+squ49cabaF1UxN8evH87tFjsTgxR0rYtoWqHsdmZgzQGRe1q0UlcZy1ar8B1qlq6uTsNCRFCiG2mwySxVTOJrZpJqqATya57kerQEyJRcEwmVCgPfI+ge3dMv554xxyGN28uzlffoecsQH1/HMmmXs+kyV72EdHVX1HdeT/S7fZYd6ejSXbei1SHvkSXfEF00WfoYONVM5RSZOVmr38bEMtq3HyF77Kz+EX/3uxfXsFVS5fTyaYzJ68ORGpORkM/ExyMUrj1eyaUpRNp7vMX8bnK4rpUBxbZ5pl7sC0enTiBs884kzFHjOaFSS832XaPOvxIClu35vaJT1DdrjVFQUA+lixraKNDPMfSRofgQo4yeDoTELJUvZPm2l6GeoFvvQnYqJqeiNqYWHOfthgLSiuMXf+JWtXcx0aGRqnaHgiFsZnQUtfzoRVhqEBl7gOwtf8rsCazgdqPu0Wtm/vxvfuUo/FjDjmRCFZpspVPkLSEXoRkwoLnkQgcLJpEQpEuT5GqNqRKk4TVaVKlccLKJMHaOKaiGrO2EqqTG47Z2kannXQKl19wMXfe+xfu3YoAUFVdzXXjf8uyFcu5/IKLWV1czJPPPd2kbRS7n5As0k5nQlpjVD4qDLEWlDYQZpYy1WoVnl6Fdtfs1hOkt5aECCFEk/JLl+KXLsV8EyXeYy+SewzBRPOAABwH5YKyATbmYwf0wQzsgU4nUXMWwGffYudteflWJ11J7vy3SK+eSbz7AaTz2qO8zGHNOj6JHnuT6DWU6LxPiM6fjjbNW7v7o7xcTsnLZUx5KZevXkl7J8iccGqVOfkFAjfTS2GUykzmJVOi1NeKYcR5Jm8erwb5jK9qT/X617hb1Jz585g8dQpXXPhr3nr3nS260rw5OdnZXHnRJUyeOoV/VJZCx3aNer4TGArCkIJUSFsnTW61pcANyI+HZLmGVn5IxDfkeYZYyuA4lvwwxPqQr0KUsvhKEal/Ul03h4J1AaE2fKh1vRS199U+fl2IyAQMVCY81O+BUFphDOv1TtRlFwVh7X3fP8fXqiZ81Luv3jgvay066uMqB93aR7e3WNfHDTTWQFp5hCmLcT2CeEiYNqTLktiqOKYiiS2vgso4trQSXVkFZeU48Sr0FvQ4de7YiRuuuJoJT0/cqgBR3z0P3EfH9h34vyuv4YNpH8kcCdFoaV1I6LYncDtiTCwz1DAMwGaCurIGzRpcvRSX1TJBehtJiBBCNAudTpA962OyZ31MslMvEv2HEHTvhvIctA5RYYCKarQBFXFxhu6BN7QHqqwcM2cxwadzCBZt2aJ2XuUqvJnPkCrqQXWfAwljBShrsV6mPFJ8jwNI9hxCdN6nROZ9hm7iK7HfNymvgEk5eYyrLuGS8tVkeyEoCOqHCQ/89cKEIuUoYo7lJKeMg7Mreai6iAcrC2EHWdPgxlvH8/ITz3D9ZVdx3fjfbvP2rrv0SgryC7jx1vFb9fxQadagWWM85pooNHreY01gALK9gFZZhvxoSFFOQDRiKMgx5GQZotGQ/FyDF7UU5Bq8WEgkCrFcg3Ug1xiSriYralEumLQCvS4o1A6Jq+ulYOP32ZD17lsXPjQ2XD+s1MUPrbBp6oJJzY21T8QakxlWWNvz4WjwIxDNhcBgtUeYCAkdj7DaYpRLUO1kAkTcoCoq0Ik4qrwcJxFHV1agk1Xo6gp0ooqbrruRktISbr7ztsa++Rt1y123c+CIkfzu2hv46UXnN8k2xa7LAoHXlnSkM6HTHqNjqLTJ3GMDsAqrNI4pxjHL8exStAqlanMTkRAhhGh2kaVziSydS5iVTXLoUOzQfmgvAmGYCRW2JlT4CrdVFs4+vXFH9kGVlJL8ciHV0+aTXrn5NSj8NfNx1y4g1XEQ8d77YVXtmgwhJjuP6kGHEu85hNjcT4jO+7J5/45ozaM5RTwWK+CXqTX8IrEGz7U4CkKl6s2PAL+mYpDrZy43pxS0ckIuy13Fya1K+OOa9kypbvn5EkuWLWX8HX/k1htvYunyZdt05fnCn5/H6T8YyzU33diCV5zXndBXpj0qy2BxGbByK7emLK5rySsIyc6BrGzIzgMvqsnOU2jf4scMXlaA8jSRHEXoQCTLYHwNWqGzDGGocb1MlLA1o7bW5d71eyDW755Y9xBbNz7re/8rXS9tbCRMG4PCyQzB8iLYbIXJboXKbktggZSFIIBA0bcwh0NGHsAl113VJD1TAJVVVdz+17u5+5bb6NWjJ3Ol/Kv4HoNDEOtIEOtM4LfHmszwU5sOM78d2oIBbavw0kvwwiVoaubHSXhoUhIihBDbjVNdRdbU97BT3yPs1xv2HgC9OqA8BydIo0JQnkIbgwoMXuscsg7tQ9GoHpi1FSRmLGXN+wtJr224Yoa2lujSL/FXfEu8z/4kuu4FEa/ufpudR9V+R5Houy+xLyYTXTqnWffZOg5/j7XlAb+Iy8OVnBGUobx6YaK2F8JdFyacmhPIlFb0iKT5e8fFfBRmcdPSDixKRZq1vZvzxLNP0bqoiMsvuJhOHTpu8STaWjnZ2Vx36ZWc/oOx3HHPn3epse/WKtJpxZrVmjWrN/qImn+br1CmPXAiDpFcFzer9p+Piri42T7Gd3GiHjYSBdeBrCihctA5MQJciPhYX9Wbj7Huf1sTOtbNy6j5X2nqpprUvzMzaYPaRKNsZojXTw4YyOq1a5n0xmuNfKc27dU3X6d4zRrOHHs6v7v91ibdttg5GeWSzu1OOtaJMNoxM8SwdnRqMkDVlH1WYRwvuQAvtQjHVrZom3cHEiKEENudAtxv5sA3c7Ct8rAjBqKG9kQ5mZMY7TroMIDAov3M2HO/dYy8Mb3pNLoLicWllM1YyaoPV5Aq3fgYFh2myP52CpH504kPPoxUhz6ZoSB+5rAX5hVSefCJJCrXkvXJW/jLFzbrPqcdhz84HbnXbcPVahUnqjJMTXAIAa9ecPBrKwpFauZMKMX+udU8v+c8nq3I54+L2hE3LTdf4m8P3k/xmjXccMXVHDhiJLf/9e4Gy3nW8j2Pow4/kisvuoSC/AKuuenGXSpANDWTBpMOSVeGwMYLA2yxmA9RH5UVxfoeZMVQfgTt+RCN4DoRTFYMrIt1I0AMrINxYxAqrB/LTEitSxuZLw7dsxOvbubnvjVS6TST3nydEfsdQiL5Ctg4WgVAHK3SoFIoUignANIyIXYXFbpZpPO6kc7vQegXAi42DFFGYW3mQlNmIbgEfnwpbnw+XrC2pZu9W5EQIYRoUaqkHPPy+8Rf+QBvWC/Uvr3werbG8TROmMKGoD2NE6ZRQYjjK/K7ZVPYrRt7ntSFqgUlrPi4mMUfrCGMb1jm0k1WkfvxC6QL2lK916GkO3bN3GEtNuIRFLajfPQZeMULiH0yBX9l8w6tqdAeN9CJP9s2XK9WcASVBF4mOBjAczNDmpKOIqJtpmfCz5y0GQ2ntC1lTFE5f1/ZmoeXtNx8iSeefYr3P/6Q3117A3ffchvFl1/NpDdfZ8Y3XzF77hwSySTRSIQ+vXozqN8Axhx+JK2LimRhsZYQT0E8hS1Zd2W2dh2/Lf30WMA4Hrg+1o2QldOK3u1+wQNfz2yGBsOMb75i3NjTiESLiFdWY7BgahYAUyGZ1TsMkAYdonU11oY4ThJLiNIBigClbeaEUxkJGzuBIJJHuk0f0tmdCHPaQzoN1oEwQIWAdrBhgDYhbmIRfuV8nOSyHWTW2O5HQoQQYsdgLelP55D+dA7V7fLIHdWXvCHt0Qow4HgaHaSxocHxdWb4kwkp6pNLu14+Q05pTfmiKpZ8VMrs98prFxyt45WuIv/dCSQ796F6r4MJC1rVGx4bku7cjXTnbviL5hKbNhmveKPjUZrMauVzSbor3YIE17srOIDq9eZHeJGaMKEVkZr5E6qmmpPrwuW9VjGucwnj57RjSnFes7a1IUuWLeWnF51P7x49GTf2dEbuP5xxY09D1ztbM8Ywd8F8XnptEo9MnCBj3HdSCnDCNIRpSFbRq1MbtNbMmTe3WV5v9tw5aK3p3d3lq2/XgnEyw66szoyusioz90NliuSa0EcpgwldIMxMKCesWV8kAAxGG8DUhBBTsxZIZhJuZq2AZtkVsRnpnNak2/Qm1bonoZuPUgqVStcMpaup36wdSCfxqlfglc7Gq1qCpnmr7YnNkxAhhNjhhCvLKX3iY0qfVuSP6E7h/p2JdMvB9RQ6CLHG4voKnTYQhDh+5mDWvneEbgNbc+C4XFZ8E2fOB1XMmZakfmXXyJLZeEtmk+i/D/G9RmAj2eCum2AadO1CVd8f482aTXTKZJzysmbd14U2yrmV3envVHNtwQqGkSDlKSK1PRM1vRAJtS5MaC/zf1Ek4J5hS/iyPMYNMzqwsKpl1peYM39e3dj1rFiMbl264vs+qVSKhYsXUR3f+KJ/O5Nddb+2lu9nJrPGE82zom8imRnClZO9jGjku40+xlowRqFUTVlnqzLrethMP4vNrBAC2Mx9qnZOSu0GqFcGy2aGbEmQaHYWSBd1ItW+D0HrHoSxPEjUDE1KpgGF1QoVZqqJueXL8cvn4ZXMwTGNLsEmmpGECCHEjiuwlE2ZT9mU+WR1zaP94V1pN6QVOjCgM0FCpUNsaPA8UIHBpi2xLE3PIR57DMlBnxth8YwEX0xOM2v6upWNs77+hOisL6keMoLkkH1qprxadCRzApLeYw/C3t3w587Gf+c9dGXzTtL7OsziR2t6sn+kgivarqI/SVL1hjS5Xm2Y0EScmmFbLqAU/fKTPHXEfF5fnsf46e2oClru0F4dj/PNrI2f9O1santYDhg+gp7dum/QwzJv4QKmfvgBj06cwJzdrIcllcpMDo9Fmye4RiOR9V5nY5QCx7FsRW1fsZ0ZpQg69CDZuS/pNl2wXk5mSGkyzPQ8aIO1OhMeDDjJMvyV3+GvmY2TlhWkd1QSIoQQO4XqReXMe2gmCyKazod0oNPwIvwuETwfdBBgHYPvg0qFmNAQ9UClDa5rGTjCZfC+IcnygAVfh3z8luK7mRodpMj5ZDLRb6YTH34IQe+e4NRWcjLomEOwVz/Cfn3wvvgS972P0dXNe/X5o2Qupy7O5cicMn7dcTXdSWWGNNWGCT8TIJKomjniFuuDp+GIThUc2K2C/31bxP0zirAyUnirdO7Yid9dewOjDjiI4jVrmPTm69z/8L+YM28u8USCWDRK75692Kv/QI4dPYazzzhzt5vrsXDxIowx9O7Ziy9mzmjy7ffp1RtjDAsXL2rybYvtwzguqV57kurYk3TH3pnjkakpMZwwmfCgMissWkfhVJThrZpLZNlXuInSFm692BISIoQQOxWTNCx6dSmLXl1K0R459DmqNV0HRiAdgmPxIxaVDjGOIeZbSBtM2hD1IZofss+IkIMPTVFZHPLlpw7vvB5h/twKct98gfRX7UkcdAhh5844KsiMw4XMgl7DBxMM64/+6HP01GnoVNNWpPm+1yvzeX1WHqcUlnBel2I6ENQLEwpdk3WSaPya4VjGhRzf8vNBazi+Xyl3ftyOtxa0zHyJndVpJ53CDVdcTUlpCZdcd1WDVae+mDmDp55/lvF3/IExR4zmyosu4eUnnmH8HX/kiWefaoGWb1/V8TjzFi5gr/4Deer5Z5t8+4P6DWDugvm79ZCxnZHJipHq1Yegz56kCjtgnBikAjBeZvxZMlPmS2mTmd8SJPGXzSGy9Fu80mUt3XzRSBIihBA7rTWzKlkzq5Lp2Zp+o/PZY0QWsY4qUy41CMExRHwLNUOear82aWjTJuSIIxIcdVgZVSUhn0yN8fxrKZY++TipHj1Jjx6FjRYA4GiDUg5EfMzIoej9B2Df/xymTkeFG1aEajqKp9YW8tTaAn7SYQ0/6raWCCHJ+vMjasrAJlH4NfMnQg0dcwL+cOgyZpSt4dbJHZizpmXmS+xMfvWzc7n8gouZ8PTELV7/Ih0EvDDpZd569x2uv+wqbr3xJloXFfG3bViIb2cx9cMPOHb0GMbf8YcmLfPqex5jDj+Sl16b1GTbFM3H5GYT7tWPoEdPTOeOBAmLVR4qGWTWcvAcbCozAV6pNAQGb9kcovNn4q5aIP2lOzEJEUKInV6qyvDFMyV88UwJXQZH2OfoGL36gU0ZiFoifmYCtnUsUd9AKiQMDdm+gXhIm7yA044u5ZRRpSxe4vPBZ6t49slvWdpjX9Ij90UVZte9lqMt+FHs4cPR+/RDffgF9oMZG64a3KQ0Dy1vw3+WF/GrnqsZ262UCHa9ydaqJkCkjMKPZio7BRqGdEjwn1MX8vrCHP70VjvKk3LY35jTTjqFyy+4mDvv/ctWrcRdVV3NdeN/y7IVy7n8gotZXVy8y6+D8ejECZx9xpmMOWI0L0x6ucm2e1RNOeBHJk5osm2KpmXbFGIH9YE9exC0bgNaYxMGqxVaG0IL+A42YVBodJjEXbYUf+5XRBZ9hzZSWWlXIH9NhBC7lMVfJFn8RZKcVjD8GJ/BIyDWzuJ7IaZmQnbUD7Fpi9UQ80JslSWwEHUtXduk6HZYkrMPK2H2vGW8NfMdnvaOZO2Q/VAalF+7yJvFKchCHTMSO3wg9u1PMJ/NatZ9C9H8dV47/rmgDZf3XcmYHmVEgASKSG2FqZrJ1imriNSECeNYju1XwcG9qvjfF63413tFWCvX/2p17tiJG664mglPT9yqAFHfPQ/cR8f2Hfi/K6/hg2kf7dJzJObMn8fkqVO44sJf89a77zRq5fKG5GRnc+VFlzB56hQpB7yDUV3b4gzsie3bEwpySVsXUJnhStqvqX4Fytd1cx4iyxfhzZ5FZO436GTzVPISLUf+igghdkmVJfDGIynuvCjFI3caFs5SuCpTvUlrS8QPMakQrCXLMZi0Igwg6lgIFWEa+nZK8IsDVvHi4Ed4tPgafrTqKWImc6LkhCmUztSDVK1yiJ56MNHLTsXp373Z9y1hNDd/3YFjX+vNS0vyMG7t7TVDuQBbGyaMIloz5Mn1LecdvIZnL5zHIf3Km72dO4vfXXsDJaUl3HznbU2yvVvuup3SslJ+d+0NTbK9HdmNt46nVUErrr/sqibZ3nWXXklBfgE33jq+SbYntoFSOH06Ejv1QLKvOpXY+SfgHzAAVZiH0godZoawaVVbelqjDOjitUTff4+8f95H3nMTiH39mQSIXZT0RAghdmnWwpcfwJcfuLRupzn6xDjDh0O71hZHh5gEKG2JaAjiCkcbIg6kkorAWnxtSaHoUxBnYDiZ81dPZabqypu5+zHJ3ZuU9jKLcLkOuk0+0TMORRWvIf7yNMLZy5t138rTLtdP60SbmWmu328F+3XNlEJMWJWZ/wFYNxN00hYisUzPREFOyB9/uIyZS9dyywvtmbt84/MllFLYZh2m1fJ69+jJqAMO4pLrrmqSK+kAlVVV3P7Xu7n7ltvo1aPnLn1FfcmypTx48++4+OY/sHT5sm3qybnw5+dx+g/Gcs1NN+7SPTg7NFcTG9gZb0AX/D07YxyH0PXBWNIW0AqVCrCOi6pZc0O7Dqa4BOe7+bifzsRZW9Ky+yC2GwkRQojdRvFKzX/vz+aRB2KMOizOiWNK2aNdQDqtyNIGlCaV0ES1wVeQTmgcDBFtSSYVgYEclWZY9Tz2rlrIlfo5PnN68Er+UN7y9sJqB61CdMdCcn5+FOGcpSRe/5xgQTOvfh33uGRyF7rmJ7l+5Ar26pKpaJM0Gr+mFyJ0wFGKwKwb5tSrU5L/XLKQt2fkcNvT7SivzvxJaF1UxEUXX0DPHj2orKzkgQcf4tNPpzfrPrSUcWNPz5RxfeO1Jt3uq2++TvGaNZw59vS6hfh2VX3+/BeKcbjs5pvp1KHjFk9Kr5WTnc11l17J6T8Yyx33/HmXn0uyo9FZHlkDO5IzrCu6c2tUVpQwaQhdH21r5jfozCrS1vVwMASASiXhq1moz7/FX7yipXdDtAAJEUKI3Y4xmrffyObtN7Lp0TXJaUeVcOCgCgprTq5TSUVMG0CTTiq0MkQUpFIKbS0+llQqxAmrGWm+Yd/iuVxhX+DrSCee67QfH7TtC0oR7dWW2B5jSH27lMqXPiVc0byrXy8qi3DeK93o1zbONaNW0qdDZghBsv5kawURFIFVRLIy45YPGFTFM0PmMeGdVvzzpSKuuOIyOnbsgNaanJwcfn3xhVx//Y0sXrKkWdvfEg4YPoJJb77epNWFAFLpNJPefJ2R+w9v0u3uaAZXVTKkOk78lltYuWolp9x1N6OGj+AP9/y5wfK4tXzP46jDj+TKiy6hIL+Aa266UQLEduLkRWi1Xydi/TqS1auQdKDBdUknDQZwPEVoQSmNCkKs42TWAE+mMN8tJfxkFnb2YhkTv5uTECGE2K3NXxThj/9sz11eW044qJSTh5fRKS9NKtBElMVaRSqliWLwFKSTGm0NESyptCIMDX4iASZk/8o5HLj0O9aqHKa36sHzvfdlZvvu+H070K7vGBJfLaXs+c8I1279CqxZsRjdunTF931SqRQLFy/aoJb+N6tinP1kd/bpWsmVh66ic9t03fyISL3KTRGlCI3Cj2XCxOmHl3DsqCq8Tt9RYjoDoLXGWsuefffY5UJEdlYWPbt15/6H/9Us25/xzVeMG3saWbHYLrvewQ2rV+D7YEOFefBBVr7xJnl//xt333IbJZddxUtvvcGMb75i9tw5JJJJopEIfXr1ZlC/AYypqcK0uy3U11IibaK03q8j+YPa4HYqyhwTUgqrNZp14cFApuchmel50EGa5JwVpD6fR/qL+dCsZa3FzkRChBBCAKm0ZuJbhUx8q5B+XeKcOXItI7pXkesa0glFKtBECcFq0mmVCRUWgpRCG4OfStf0VGiK0pUcWvY1h82aSZWN8mHH3jy97wjm79WFWN/2pGYsZO2LMwjLtmyyYe8ePRk39nQOGD6Cnt26o/W663/GGOYtXMDUDz/g0YkTmFNv/P0ni3I4/eEcDt2znF8fsZqiVgGgSBtFJKem1wVFRGXOC/yYobVOkh+9hzbOiyyuPo942BelFFVVTTNfYEfStXMXtNbMmTe3WbY/e+4ctNZ069KVb2Z91yyv0ZL2T1TSTyVJeoosbUk7kF68gMpjjqGibz9iv/wlx44ezbixp23wmZ27YD4vvTaJRyZO2KXnjLS03G7ZtNm3La32akO0dYw0PgCJVAiumxmuBGg3Ex60VpBKg3YJFq2m+ovFJD6bD/F0i+6H2DFJiBA7ldo5nkq1bDvEru2bxTFumNCJLD/k9H1LOLFfGW28gFSY6Z1IG0Uy0EStgRDSgSJiLX4I6VSINhYvZUmHLrnJOEd/9QVHfD6T4qxcpnfrzrOjhrPkhqMpf38upa9+g6ne+B/ozh078btrb2DUAQdlxu2/+Tr3P/wv5sybSzyRIBaN0rtnL/bqP5BjR4/h7DPO3OhV3be/y+Pt73I4Ye9yzjusmNy8EFCkQ0UkuyZMWEVUgzFQnS4lx/+OXnk3UGb25v0vRjNt2ifb583fjkbazPseTzRP5ZhEMgmA7/vNsv2WdlV8JcpT5GhLKgTS4KrMJP7gu2+ovOTXnNK/D/H8/M32nokmoqBoj1w6jmhNQe88Iu1yMKElrSIA2FSAcly0DTG4OF5mPThVEx6Sq6qpmL6Eyo8XYMrlZyQ2TUKE2CkZA1oGY4pmVp1yeGhqax6a2pp9O1dyxoAS9mtTRba2pAJFKsxcxbcGUoEiag2e0QRJhQ4C3IQhwEVbhZcKaZOo4OjlX3DcW5+xpLCIjwb14rlLRjLvy1UUv/odpNcNEzjtpFO44YqrKSkt4ZLrrmpwfPkXM2fw1PPPMv6OPzDmiNFcedElvPzEM4y/44888exT9R6pef7TAl6Ynsu4UaX8+NC1RLIMDpkJ47WVm5JWQSJOGIaoWAqP1+jd/mXOOL2AxyYUEAQ7/y/e6LCMC+Or6VniARCLNs9q3tFI5sQtlUo1y/Zb0vCgkj1J4kYsgQEnpcjWlqQHKgWegscLClnj+xCP75I9MTsK5UCXYbm0G1JAu73ywXOxnp8JD4B2atZycF0cmxm25HmQJBMe0ivKqZy5itIP5pNaufVDLcXuR0KE2KkolQkQoGqCxK5dflLsOKYtyWHakhzy/DQ/7r+WEzqUk29CwrBmonWoMj0VWKxRpNKaSGhwU2kC4+Bbi5sKCY3GWuiyrJiOi0o44ZlPWJqfx+T9e/NoUREL31vMr875BZdfcDETnp64xZVu0kHAC5Ne5q133+H6y67i1htvonVREX/7XslNax0eeaeIJ6YUcM6YNZx+SBnat0QUBCH4WZkwUR4P8FUaYyGS7/LDsaUceFCc/z1eyJR3osDO1h1oOTFSyvm2mC6JFApQi2djjaF3z158MXNGk79in169McawcPGiJt92S7vSrMT1LWkDKlA4NT10fjpTLnk5Lne3a9fSzdxluVHotncuvUbkkN89Gz/HI5FUWN/BBOvCg00FKNdF2RCLi+OCAcJ4wNpPl7P2o6VUzy9t4b0ROysJEWKnozUYY7HWqQkSYUs3SexGylMe93zejns+b8shbcs5o1Mpe2dXE7GZIBEE4FlLOszMPfCtxSZDUmlFJDQ4SQgz1/9xUiHJQFO0pITj5kzjYN8hvPRC+l1wMXfe+5etqrlfVV3NdeN/y7IVy7n8gotZXVy80Yo36dDhny+15dE3Cjn35GKOP7Ac40IECI3CremZqAodnFhmKGGrdvDry0oYfXSEfz2Qx/zZ3ra/oc3OcmpeCT+LFdMxHUAcQkehXCBRDXNnsVf/gTz1/LNN/sqD+g1g7oL5u9zQnYMop7+bIK0VOg2OsqQchRNYtIZ0qPhHThsC6S5uUtEcRd8DY3TbO4f2fXyS1kO5mmQiczHNcw0pQLvUhQdtDBZwXYjH05R8U8KyKcsp/3pti+6L2DVIiBA7pUyQMFjrEIYOjiNBQmxvindW5fPOqnzaeCnO7VTMUdkVZAcmMyfCZIJEYMhMwA4t6QC8dIgOLaF1cE2ATRrSVmMI8Tp0ocd1v2fC0xO3adEugHseuI+O7Tvwf1dewwfTPmqw8k1V0uWux9vz8CuFnHdaMaNHVJICfJUp8aizah6XdnFiCmuha2/D724r54OpUf73QIzy0h3vZFFhOKNDCWe1Wku7MEDFM+FIexYVgKr5X7/3GseeMI7xd/yhScu8+p7HmMOP5KXXJjXZNncUV/srSRuFDjK9walQ4aYzx+VUqFjk+UzILmzpZu4S8lvDwFEReg3xKeyRhdYQT7koV6ETIdbVeC4EgOMobDpEuU5deNDKsnJGCSumrWbFx6szEyCEaCISIsROS2tLGBqs9TChQjtNW+ddiC21Ou1z84KO3Izl+NwyTssuYTBxfJuZOxEag2cyE7ADC15gCJOWpNVYYzCBJek4FN17L8Vlpdx8521N0q5b7rqdA0eM5HfX3sBPLzp/k49dW+Zz6z878vBzSc47q5gD96mi2jg4WhEaUL4DQHXSwfEzoWHwfiED9onz+oseLzzuEQYtP8TJwfCjPmv5YfsS2to0Og4qWRMYUoBT889VWAeCx+6j1U8uZswRo3lh0stN1o6jasqXPjJxQpNtc0cwyiunczTI9EA4NQEiAOVkPutOANdGOrZ0M3dqHbrB4IMceu/t0aqNzqwYDVSnQtAOmBDQeJ4lhUW7CpsKUU4mPBjjUL64ioUfLmPph2sIqiU5iOYhIULs1BzHYMKA0HhYq3HcXW8Co9iZKF6oKOCFigI6qRQXZq3i8LASFWYWqfPCTO9EaC1OaIknIG0UKjTo/gPIO/pobrzuqkat9rsplVVV3P7Xu7n7ltvo1aPnFpXSXLYqwm/u7ETv7nHOPruEoYMTxAMPJ1YzD8mtCRMJBx3R+FgOPd6yzyEBzz/i8PHbLdMr4SrDOYOLOa1nKUUmgCqwKUXoAoFCOYBLXS+EDkB5wPyvSb/9CtdccDFvvftOk7z3OdnZXHnRJUyeOmWXK196Ue5qHCzasSQDhZdeFyA8DVO8LL5UWS3dzJ2MoWdf2P9QS7e+ilYdPYI0BG7mdymdCjO/d6EB18FzLQG2pufBolyFCkNKlwcsnFbB7LdLSJbLRTXR/CREiJ2edsKa+REuNq1xveYp1yhEYyy1PtdWdc4Mq6GEsaaUvjaBZyxBoMBYqBniFBjI+8W5rC0uZtIbrzVpO15983WK16zhzLGn87vbb93i581ZEOP/booxoH81486pYs++aeJJFyeiMBbwMmEikXDQvia/FfzgF5rhR2ue/5dlwbfbp+hB1DOcs38xJ+5RRr4NIZlZEFB5oEKLdjIXb7Vr0T6owKLCTEUbHEBDeOMFtJ70JddfdhXXjf/tNrfpukuvpCC/gBtvHb/N29qRHBIrZ89oEm0syVDhKcDNLLroK0i4cENCeiG2hFKGYfsFDBkeMGCoxYk4aN8hHSjSgOtBKm3Qrq4LD75nCMjMb0inLcpRVK9OsuDzJLMmV1C6VC6iie1LQoTYJThuCpPWYDNXcHa2IGHt+l8rJWth7Cosmkcp4lG3iN7RBBezmoMSlRCCsZkT2hTgjx7NM2+90aTj8gFS6TST3nydkfsP36rnf/V1FtdflcU++1dz8hlJunU3xJMOOpKZH2EcBw3EExrlO3TqAT++3mPWF/DKv5OUFTfp7tTJigT85LC1HNu/jDxt0AmLk7JoA8pkAoRKk5lA7SqsqwgdwFEobcFVxD3Fh9Fs/lGmGPyn27n1xptYunzZNs1HufDn53H6D8ZyzU037nIrMF/WdhXKtSRTGl9ZcCypIPO18SyPVheyWu2aa2I0hYgfst/IFAePitO5pyU3H6riLjrqkE6HhGR6GVIpg3I1hCG4Gs+1hGTCQyoZkkgoZn1cyVeT46ycI8FBtBwJEWKX4boJgrQGEyNIO7jezlrvOnNyZi1gM93ZmWChQFmstZmvMYBt1HoZtduVoiktY44b5eKcLrhZhrPL1jBmTSntEylsTg5Ze+zBl4//r1led8Y3XzFu7GlkxWJbXSnok4+y+OSjGAcekmTMqSHtOloSSQftZ9KucVwUkEwpnIhDv/2gU98cPn8n5J0JccImWvA2Jyvg5ycUc/TQCnIIUXEgCcpVmACMBlSm/r1yyQQJp6ZHwgU8mJ/weSYo4NGgkMDJ/DJ89+xTtC4q4vILLqZTh45bXFq3rl3Z2Vx36ZWc/oOx3HHPnzdaEWtndmR+GT3yknUBwnqWdCqz+KKxllUpj7uSUtL1+7KzQkaPKmffkQn67ZEg5fk4rqIq7gIOnlsTHjxLOm0zazrUzHnw3ZqeBw8qSkMWfWuY/mYVC76Q1aPFjkFChNhlKAWOW40JXEwYIW0cvEh5Szdri9TvdbD1uyUUYDNfGOtkvrYKS024MBqjah+kM5dgrQGlUMoAYeaqKwalwrqNhqFG61B6O1pIoDUPtmrDg63a0Leyml+3aUcfrZkzb26zvN7suXPQWtOtS9dtXPRL8d47Ud57x3D4cSGHHG8paA3VCY2qmWwdKhcNpJKKSI7L/se59Nw3yvvPJvjq7a0vdZqfH3L22GJG71NBzBpIQCqlUYDGonQmHGsXtAfaWHSYGb6kDVQlNVOrsrl/RWvmpGIbfY2/PXg/xWvWcMMVV3PgiJHc/te7G1zkr5bveRx1+JFcedElFOQXcM1NN+5yAQLgwq6rSTqaSMRiDZkAoS2hgTCpuSfRhhC5OgFQlJ/i2EMqGDG4it57JHEdS4WTWR06lQzBdfFcg8HB9yxVNcOWbGDAcfBdQ5rM4X/OZwFfvh8yc2pIKNMcxA5GQoTYpWgNuOXYdCHWRkmnFK5XtlOdLK/fS1C/qkaAMWCtQikNVmFwyfRcaLAOWBdrFZnB3tT0ZGS+ttZFKUNoQrAeSgUoJ4mjAZ1CEaB0iFLJner92tl9m5PFP3p1ZzQQTzTPMLxEMgmA7zfVUBPNmy9q3nnFMvoUwz6jXXJ8SCQ12tdgIURnwkRKkdvG46hf+PQ/NIf3Hi1n+bfJLX6l/FYBp4+r5qDh5eTpJF7KQhocPxMeHCzK1gQJQ6aDLlAYrQg1zK2O8uyCfJ5amo+p/b3YhCeefYr3P/6Q3117A3ffchvFl1/NpDdfZ8Y3XzF77hwSySTRSIQ+vXozqN8AxtRUYZo8dQo33jp+lxvCBHBEmzI6ZqfxTU1oSCsi0ZqvU4oFgc8z1a1aupktqlv7JEcPL+PAoVV0aJ3Gz8lcDErazMHUpix4Ck9nVoz2PUNV2uA4GkILLvhuSNo4LFsAU98Kmf4uJONSWUnsuCREiF2O1oBXSpAqxITZBDi43tpd4sQ4EzAsteFi/bK2VRiTCRTKuhg01nhg/bqQYa2DUm6mmlWYg0o7hNqgNVgUtYeETH3xAFQSpS1KJUEHaJUClUKRQqkUWpvt+wbsolKpzLjmWDTaLNuPRiLrvU5TCUPFK084vPGsZfQPDYNGecR8SCQVuqYkbICDRpFKQ5ueEU6+oS3ffZTgw0dKqFrb8KXV/NaWE8eF7D88QU4kRURrVFgTFrAQKkKlMKjM2tk20z+nFFQFmqmLsvnPl4UsqGj8e7pk2VJ+etH59O7Rk3FjT2fk/sMZN/Y0dL2Eb4xh7oL5vPTaJB6ZOGGXq8JU3y97FuNHMvN7g5Qmqg3pEEyg8CKW6xd1aOkmtgBL/y5xTty/nEG9q+neKU0qVHhZmfCQDsFxMiHLcS0+mZ6HiGeoDCyOqyCw4IDnhCxa5PH5Ry5vvuRQUSY9OmLnICFC7JK0Nrh+CUGqDTaIkTZt8CKrd4kgsSla1waM2oEF6w8fMSYTJFzrE6ayCMJcrPUxpNHEqBtIZRyMckFFwNYeJhRW1/Rq6JreEMKacJFGkQQdookDKbROoWw1kMJB+uE3ZeHiRRhj6N2zF1/MnNHk2+/TqzfGGBYuXtTk2wZIp+Cl/1jefCrB6LN8+gyPEKEmTNRUcQpsJkwEAXTdL5fOQ3KZ8Xo5XzxVvN58iVYdNIef5rHXPgHZXohFkwoclHKw1gMDvjG4KjPPQbmg/cwE9dkrfJ79tIAXZuZj7LafiM2ZP6+uolVWLEa3Ll3xfZ9UKsXCxYt2uZWoN+aojmX0LkgRhpYwrYlEDWkDJqWIOJZX1+byTWJ3KelqOKhPFYcPrGB4n2qi2SHRrEylKgDfsQQBOC6kkwony+KqzFE16lgq0uB4QCozpKmsBD76OMbbr0VYtmTzvWRC7GgkRIhdltYhjreaINURTDbppML1V+3Wk4q1zgQMSOG6leh0FTaIoZwAxy0FHKzxsSYLi4c1PoZsMD6GCHXDpKjposcFfEILVtmawvvUTFCpeaO1ykzXsAlwQrRJom0cdBodVKFsAmWTaFONtrtnpZHqeJx5CxewV/+BPPX8s02+/UH9BrBk1QLiieY96U1UwfP3pch5Ms3hZ8boOiwLD0gmqQsTKeOgHIVV0G9Ma3oc0IrpE4spmVPJ8FOy2XOIIuakCbGkQhfXCTOBVgcorVEaXG1wnUyvRFmlw3uf5fHo261YvCbSbPtWHY9v43ySndOFg1YTRDLzHqKOJR0oTKCIRA2lKYebF7Rv6SY2rzDF6L7lHNu/jH5d4xRkGxImM5wrZTLHwYjOlGp2XEW6pufBrbki4zuWRKBwXSBlKYu7fPRpFi+9ksuc2T61x1IhdkYSIsQuzXFCVGQFqURHrMknSLl4kWW7fI/ElnKcKgITIQyysMbH9VfhuHG+34NRyxgXSxRjYlgVxdgIqBwMUQyRdT0Z9d9flZn6alQ2aKemeo7FujWBQ9vMpTsA16BsGhXGUTrIhIwwjrIpdLoSHcRRYTU6qN7l/vRO/fADjh09hvF3/KFJy7z6nsfRo49kiZnMT+9uzftPVvLNe81bArlyreW5v1ZT0D7BIT/Oo12/bBwglQJVEybSoUZrRaSVxxHXdCPLSxGurUClEmRmRDugM4UDQjRp66BDF2VCbAjzZnu88lY+r32YmxmuJ5rcsT1KaV+QzsyBcCypIDPsMeIakmnFhJWtKAm8lm5mk4s6IZ1LX6Zz6adkVX7FfmNKcbQiXnPU0bUBQVuCmmFL6ZTGcW3dZRbftXVDmqoqNF/OzeKVd/L44NMskAnoYhchIULs8rRO40dWkkp2xgR5pK2PG1mwW/dI1NIaXK+UwLbHhNmkEp3wo0sbfG+0DoBKHF250fuN9TFEsSYba7MwKkKockFnYVWkbmKrXS/F1ftauRjtgZsFXu38DIOq/doBHBdlQ1BpVJhAp6pQKkAnK1CpKnSYQCfKUalKdKoaXb/a1Q7s0YkTOPuMMxlzxGhemPRyk233qMOPpKigiFfnvUB+G4ejfpHNwad4vP1oglnTmrdUZOkKw7O3ldK6exUH/qgVBT2zUUCQApWThdMqGy9q8HUKhUusfQ66WhOsCSEdorSD0i5KG7Ryqa6yfP5RhBefzWblKlmPoHlZfjakmFArIrHMgnKQOTlOpjWrEy73zmvdwm1sOgV+mlP2KOOgzpX0a5cgb+USVLaDtSYTEKKZKl9QM2zJZDpbg9phSzXHmdohTQbFJ99k8ea0XF7/IJcglD84YtcjIULsFrSTwPOXkU50x4Q5pBM98KLzJUiQmT/ieKswYTcw+aSTHt5WhiytUmhSQHlNOVoy1XJqGHyMimGcXIyTDTqLwMvF2mxMTdAA1lt9b2O9RlY5WN9DkUWYVQC1VYdUiK392rXgOqhUHG2Tmf/jFSiTRMcr0NWV6GQVuqoUVV2JY1p2kvic+fOYPHUKV1z4a956951GrVHQkJzsbK7+9SUsKP+IktQiLBZPh2R1cBh7eTbLZqWYMjHB3C+bd9+LF6R59veraN83yj6/7EZkz454MRdj0xgVEFiDMgatHZxYhKzOClVVBRWG0ATMm+3w0RtRpr2XgzHyS7s9HLtnKR0KAnxVEyAc8F1DMq3RWP4yt01dqemdVZdYkpO6l3JY50raZ6eJZmeOO0HNMccYD6WS6/U8hGFmBfR0Sm0QLBIpxbyVEV6ZlseL7+cTT8o8B7FrkxAhdhuOW42NLiFIdMOYAoJEb9zoHAkSgOMEEFlBOtETExSQtn3worOb/L3RpDLzHoIy6uZa1xs5ZZSPcXMI3Rysn49xszB+DiaSh3VjWK+20o6t679QVlEvcqzbmFKAwvgxTCQ3s+SGDSC2LnDUhQ83jTIBuroKhyp0VRW6sgI3XY0qr0CVV6ArK6CsAh00X8nFG28dz8tPPMP1l13FdeN/u83bu+6yKyksKmDCwisBMKmQ2rfQWkPXPvDjG6Is/Mbw+n+TLJ7TfL02sb7tiBzVi0U2h/yVhjYdNXguGkuIg+M4GAyhVZk5ENEsVpQV8O7jlcx6fjnsHB1KuwjLT/ddi59lSaYUyq4LEI4H31ZEeHVJfks3cqvsmV3NDzuXMrSwmh55aZIo/CyLVRAai6MVQU2viwoMeBDRpqbnITPnIRKzOPWCxZzlPlO+zuXJqQWsqdj1hncJ0RAJEWK34rrl4C8jnepKEOZjEnviR2fVVDXavTluFcZfTjrZjdC2wqb64vvfbteQpW0KnV6Lm1670WkZxolgvFxCPweb1YrQz8ZEcjHZBRg/C+PX+wNe04WxXkdGvW4NpeqFD6WwfpTA91FZBRhA2TQmK7PzTpjCibpgLU4yjk4lsOXVuKk4lFdhyyvQ1dXYtZXY8ipsWSUkGj9UaMmypYy/44/ceuNNLF2+jHsfvL/R26h14c/P4/STx/LIe7dSVrgCpSxRb10AsqkQp2bNta594IJbNLO/tDz/kGF1Ey514A/oQt4RfcnplktEhxiVJl6RYsWsBHmtoFVbhXJdHG0ITEhVIkZpqcOKYh/8KG3HWPyB3Vj09CzKv1nbdA0TDTpxUCnd2qZJpDTatXieIZHSuGQWw7zpw44t3cRGsByQW8WxbUo5oKCarEhIxLekanpRIlhCazOVw9IaJ1Kz3gigwzShmzlmfH9IU2m1w9tf5vDUtFYsWN18E/qF2JFJiBC7Hddfg0WRTvYgDHJJJvckEvlOggTg+cVYEyMIOxGYImzQn6j39Q4zEV2HSXSYxE0UQ/mCDe43bgQTzcVE80nnF2KjuYSxXGx+ASaaA55XFxzWm5dRk5T0en0a9b6uDVJKoSIeNisCeTloL/MYHaRwI7rua8fX2FSAW1WFTSQJy6pxkgmC0mpMSRW2Mk56bRVhSRxTvX5FqieefYrWRUVcfsHFdOrQkZvvvK1RQ5tysrO57tIrOf0HY7njnj/z9389QusuLoeeFaPP4Jo5KcYQjdTbvzBAebDHYMUlf4SFM0OeekizZuXW/+CdQT2JHjqQaPscPB0SptME2qI1pLVCa01VSZqgPE0saojELOXlPkZ5mMCCl+klSqcgq1Mue164N6tnlLL86a9Jrqra6naJzTH87JBiEjqz8rfnWxJJjeuDxvDyN/nMKW2e9UyaiiLkyJwqTskvYUB+nALXkHRUZj5HTUUlD4sxFq1VZvXtSKZMMGSqLdX2dVqTOU3SFkoTDh8tyuKR6a34etnuUtZWiIZJiBC7Jc8vxlqXIN0FawpIJvoRiX4ri6cBfnQxQSIbVBtC1YZ4uBdR50v0DhIkNkUHSXRlEiqL8YvnbnC/8SKEOQWE2QWYVoWEOXmEWbnY1vmYWA5EHGorp6j1RkbV+8apqdCy8UFU64ZZ+S5OJBtUDm77/LqRUzqdwovUbCNI4TgQVCbRVdWEVSlSpXFeKJtM6gnLr0/4BQeOGMntf72bSW+8tsmqTb7ncdThR3LlRZdQkF/ANTfdyJPPPQ1A8eKAJ2+toPfeHoeNi1LUxqBqzgNN2pAVrYtWRJyAQfta+g81fPIuvPCYQ9naLeuOMkrBoD3QBw7GaZsLTkCIIcSitYt1wGgwyhISsva7clZOWULx52vRnqLbUZ3pdmRHQscDT2ECi3E9FJBOQ97AtuT2bc2KKUtZ8/LXmLisP9LUTtqnlIJcg7Lg+qYmQFi0sqwt97jj/XYt3cSNimA4MVrKsTnlDPTi+FkGrVRdaKjtXfCtxVjQKlOuNuJTFx58lZnz4Dg14UEHhMbn3QW5PPd1Lu/Mz0NKsgqxjoQIsdvyIysAn3TQEUsBqfRAfG+G9EgAUf87EiabkHyM05akGkyEL3byaZSg00l0yUq8kpWwZMP7jedhCgsJ8/KhMB9bmI/NzUEVZkNeDvgedWnKWupOKOoHjto3ydq6x2Z6NWof9L3nORo3P0akVc3hOAiI+oYvWcC1M/7IT3ufxt233MaaK6/mlddfZ8Y3XzF77hwSySTRSIQ+vXozqN8AxhxxJK0Li5g8dQo33jqeJcs2HJM059M0cz5Ns98Yl1GneOTkKxy77kTcpNYFCsexHHBImhEHwXtvujzziEuieuMTRQ2Q2msv7MihOK1zcV1D6IS4GowKMGiMMQQozNo4JZ8tYu2U+QTl63phTNoy/8XFLHpzGV2O6U7HQzoRGI3ywBqLcTIpLAihcFRP8vfpzKqXv6N8yoZhUWwtw7hRJTg+uMqSSDp4EYPCkkhonviqgPLkjnPakGPTjPNKOcSrYEAsiYvFuhaFIpnWRPx1vQuetRiT6XRMpxUR36KNAuz6Q5oChVFQHd2D8m4nMJehXHr3lS26n0LsqHaco4EQLcCPLMIqjyDsQBjmktSDiTCjZlG23ZfWligzqVb7gY6S1h2xyiEWTN+lr8PpdBq9ciXuypUbvd94LqpNKyjIwxbmYlrnQ142Tn4U2yoHFfVRNYvsqfoVpuoFjvrvX918E2PqSscru643rDhZzF1z/kHHaHsObzOcQ485iHGnnoZW6+KcsYaV1cv4tvJjpn/3Kquyl3DANR5Bqivx0gBbnaKqJKRyTZpkeUjZqoDvPg34fHLAQSe6HHq8qWmVJeKuCxRhyhCNWXDhkDEpDjmkirdfi/LUo1HS6czrG6VI7DmMxNB9UK2zcSMhKgwxGIyxhDqzqnRgDcH8Faz9aBbJr5dv8mcQxkMWPDWXpa8votNxfWgzogOpQIOnMmHCzYQJ67q0PmUoeQf1ZvXEz0nO2vjPTGy5k0aW0bFtgFaGeFzj+wZqAkRJyuGBD4pauol0NClOp4TRuoL2Tpqoa7E2M1dDKUU61HiuRa8XHmqGLYWKiF4356H+kKZE0mFRyuOlxfk8ObeA2+/6PYWFhdi1Mg9HiIZIiBC7vYg/F5vUhHTA2HyS4V5E+FKChE4StZ8Rd0agHIdAdyL+/+zdd5hdVdn38e9au5w2fdJ7h1ClSG9KC4gKGEHA9/FR7AgqCCIiCgZQkKaCir3xSBULGHoNIKAICIGQ3sv0csoua71/nDMlIYGUMyXJ/bkurpk5Ze91hpnJ/p11r3u5mlT+xR06SLwTHUawcl3xP3q61xa6HuA5OMNq0XUV6LoM0dBKnJo0XqWPU59BpXx6Xf+jdFfg6AkOGyuNWplfze3L7kBp8I3HmMp6XOURBjnaWUVgCugwIOGD1gq/0kG7DlVDXFJucfbABBHpZPE8NghIJiyFrKWhNWDIMKiqikg5Dia22DAmnTBYAza2qDAmnbGcdEqOw4/M8chDaf7vhUPpnLYftroSm1DowGAciF2FVg6xhrA9T/zyG0TPvQ4dW7bBXdgWsvi211n14CKGn7QLNfuNKnbN8RRYi3FdFKBqMgz5/PspvLma5rteJG5s36LziC6G/3d8MyplyeUcEqUZqULOIZky3PCXoWy4SVo6lWL82HH4vk8QBCxZtpRsrvy7ok+Ocnyy0MR+NssEFRA5Ci9hsUZ1h4cg1viu7f6l9IzFWItWiijS+F2zEt76JU0L2hM81VTJn5bUsKYge48IsSUkRAgBJPy3KEQJYltHrGrJ231Jmn8P9LAGnKs6SMX/IesfBNohdMeBq0l1PL/TBol3FMbEKxqIVzQAvcJFF8/BH1GFV5/Bqc+QHpbCrUnhV3o4Q5M4KZfe5U69S6NUqZIoiHOsyC0r3h8E+KWLPa16nqednuf1WH8Nh1KQzCjctCI20N7ukB7ikMqAji0JxwEcXBviKoUxLiaImRe/l/iEfTnu2EqWrXVZujKm03p0hk7xoi4ysGAxvPQqZv5StnWVUaEhx9Lf/Ic1Dy5gyAd3p2L3EUSBRXkaa21xc0LAnTCUuos+RO6FBXT87V9Q6NuN9HY0M9/fwvARAfmcJpG0WCxBTpNMG/6zKMUTc4stXadMnMSZM0/n0IMOZtL4Cehe7duMMSxcspg5zz3LbXfdzvxFC7duMNZyQK6Tmflmjsh3UuEaPMcSOArlgRsXZx8UljBWeC6oCHCLMw/dsxIblDT5FEuaGmOXhxoruW1lHUty0llJiK0lIUIIihdUvvNf8uY9WOowVJBX+xPKuk1cu45E+Bq5zD4oVxEkJmA8Tbr5ue1+jUS/C2OCZc0Ey5oBaNvgbuUpEsMrSA9P49clqRiRJFmbwKv20ENcvJS7fjB4e4MprDXdt1uz8RkOx+l6rO3+PMhZGtcqEklLXbWltLk4yloC4/HKmr15vWlPciqDdRUV6YhdJlmmTMkTokmrZnbN/os9s88TD8uTnapoanVZ0+jS1uqwYq3HyrUeqxs9WrPOBiN6d4WV7az42XOkJtZRc9KepCYPJQoBV4O1xI4LSuPvM4mqPSZRePxVCo+/ukXn2FlpbTjjpGbycSlAWEuQ1yTTlkKouOae4YwZNZorvnEpRx56OA2Njcx+5CFu/e2vmL9wAbl8nlQyyZRJk9lrtz34wHEz+MQZZ73j+py3sZYj2to5pbGZfaMsFcbgJiHpQKiKm915phQeFASxetvMw4YlTb3XQ7SEmn9mK/h1Qy3/7cz03TdTiJ2IhAghSrSGJC+Tt/tidB2xqubVBXXU1A70yAZeIlyICSsJ/F2wrkOUnETO06TXPiMzEmVkQ0t+eTv55RsvyVGeIjM8ReWoFKl6n8qhLhVDPJK1HrV1FiejIbbdf9l7r8sozlSUPi81D7CmJyx0hZNCXrG6TVFfr3ASCRat3ZN5TdPJk0A54DohsXWwkcL1Lbsm3uCAzHNMchaQW2uxrsJWWrxSE5+gAF0NQfNZRcqxBJGitUlTCDTNHZr2Fod1bR4rmzya2x2WNvksb/Jpymo2LKHJLWoi96MnSE0fQcWMvfDH1hMFBlwPsBjlolIa/5h9UPvuSjj7BeLXF2/D/5XBb1vLik4+vpWKaoPngLEQ5ooBIo7hgeer2P/gs7j0a1+nuaWZr1xy0SY7hb3831e5+6/3MusH32PGMcdx4blf4f47/sysH3yfO+69+22Pd43h/U0tzGhqYUouT62xKAWOD2iIIgWO7TXzAKFReE4pILjgGTZZ0mQMPNmZ4a72Wh7tqNjud9gWYrCRECFEL1pbkvZl8mp/Yqpozbn8e16aSUObB3poAy7V+TJxogqbGgeOolA7FRxFZtWcgR7aTsOGlo7lWTqWb3zfCO1B5TCfurEeFUM8qoZqaoc7ZGocqioNvq8B213uZM3G98UIwgQvzN2VZa0T8ZIeOqXBUcUFrChqvCb2rH2FvWpepoYWHBOjFQypjYlDaGvTEHb12VfFJvvQXVHlu5a6TIxXFTGmDpxhxdsLBUWyFHYKWYWPpaPg0NKmyQaahk6HtnaX1R0ey1pbWPd/81k1bjK5w9+LMyJBFFisW7xQjHHQQ6vxPvZ+7KJ1mPvnwJodZ5FsucqKtDZ86MRW3JQlNBDnNamMIYqhtcMhl7mUq8//Krffc9dm71kSRhF/m30/jz75ON88/yKuvuxyhtTXc8svbyURxxy/rokDWtvYJZfHscWQqYBAQYJiBy5fA73CQ2QUrlNaFO1suqQpchVzowS352r4W7aGWIKDEH1GQoQQG9AqImn/RdY9GJSiLad5cX49Bg/Nzl1nnW56ho5UJXFyWLG0aeguWF9TseSpgR6aAEwIrSsCWlcEG73f8aBqmMOI8ZqaoZqaehg6GiqqFZUVoFWCxSunsqZhNFb5RMrBWoMNIVERsMuIRUwf+l/GZRbjl/ZUUZEpdrK1Fm1BOVBfHWMSivZOXezTX7qO6305V2piRRwpHHqFjN7dbxVUJ2MqiHGVJaoFr/QrmC8oUlhgGbmFT8ASj/ZUBe2mgladZK1XQ5vKsMSvZ3l1Pcs+fhiL3mjGPvYCKrtli7wHk3KXFZ10UjtDRhuysQt5QyZjCEKFtYoFrV/k3M99letv/uFW7Z7emc1yyazvsHL1Ki445zwOeeU1Wn9+K5Wl/91dPw8h4Jc+Jiju22Dd4s9AwRRLmmxMMTz0KmkqhgeLMYp51ue+oIrfZevIs/FWxEKI8pIQIcRGaBWSjv9J0v8MsdV0Bi7ZxKGkC8+i375cdqehialY/RhtUz6MddNY1yEYuTsdLlQskCAx2MUhNK+IaV6xfucxY5IETMUkR5Op86kZrsjUWdLVMcNHtDN55EKmJucyubKDqoTB6VUapUodYpXtygDFTzzXUlcZk1aGXFYTG9VdUmWMxe1et9FrIOst9yiVXGG79vfDlPr6Q/F8XYHDARJxQLqzieH5VpSjiHFwC8XXWYhdkvkIoxRt70kS5yNaOmNas5qmyGNF4NJUcFkc+SwKfVbGHoVBeCF62skfKWtZkVIxHzw1R5YExDHpioiOUOFElmw4iWOOm8Xt99y1VQGitx//4meMGjGSU667jmcefBCzeDGanvDQ9dNou36GFIQWfPXOJU1Lrc+jupLfxnU0GG+bxiiE2HISIoTYBE2BvSY18+aaKtBgvBqyzmGksk/hsPF3encGOs6RWfIQ7dM/hPVclGspjNsL6ykq33hyoIcntkAcJwnjccRqBFa72BBaGw1tLQrHrsKLljAvbqAYD5O4ns/Q4ZZjj2njgx/ooLYuxrEWnNJsQikEKAuU3i1O+pakGxMEio5AY63CxD1hwG6ifVPXJXwcK7zSY3tVX62na/dwYyxOHEGsiBW4XUHDlrpWWUsmCvBVRH3aooxB2RxhArxSd88ggkQMBRQteYfAKJqsQ2vgsNp6LLMea2OP+SrBInzyTv+EjS+e/VkuOOe8spUVAXzg1IBEpUshUqTSis7QwbERyUyMim+huaWZK6+/pizjv+qGaznioIOZfsstvH7iid0zD11NVbv+V71TSVNoFG2+w8NuBb9IDmGpTqw3eyWE6F8SIoR4B5lEzAHTWnnwpeK7XMatJFv9fjKtj+3UMxJevpGKxY/SsfsJWE9DwiGYsg8dnqLi1ScGenjiXcRRgigcTWSGYpWDdRQocEwHTrgSL1yB5u3vcEehZtVy+N1vavndb2o46bg2PjWzgdrKmDBwSGHRrsJ1DE6k8TyLNsUyJ08XZyYKoaIl6Lnw7r1morvcyVocVbwyNJuaqdhgJqL4WNWzTrwQFR/vaFSv9KFLC8gNDo5T3GfARpau1bjK9uxiPMRGuMBYAkrVW8USmkLxGGGk0DF0Kk1L6JBDs1Y5rItclns+SzyPFY7P/GSSDnfrw8ZpJ3+EC845r2xlResaGrjnvrs4ckZMIXJIJRSdgcaxMU5K8ca893DK+4/iK5dctFlhZXN0dHby/R/fxI1XXcNbu+4Kb7xBKWsWAwKbLmlah8PLmTS/zNTxUqKiLOMRQmw7CRFCvIuqtGWf8Y38VkVYJ4mlgmzNUaRbn0Db7be2elv5zUtILXmWzt2PQrmAq8jt9l5wFRUvPT7QwxMbYeIEYTAME9dhrYtSFqVitGrAVatw1ZZs1Kb4+4PVPPBoJf8zs5FTjmwlldaYqLjnREpbChRnByio0hoIQ1RQ+Mowf1WSt1YlqPVjRlWHVKdjKkoX8rFRdBWnrBciTKluCorrMCguDtd0BY6eGQ6sKk5zRDEqXyg+QSmc0gFjVQocSmFcD8KgeLJeQaVrPXivDcXftvWGay3VNqYyjNEGphnIlhojFQyY0qRlqyquqMo6mnWOQ4fjsM53Wee6rE74LEskWJNM0Oq5xSmckjGjRnPp175e1rKib114MbruGVKVC8H36AwsLiGOr2npMMSdnymut3j4wW0634YeeOQhmhoaGPOFL7Dsy19+x5KmWCueyaS5p66OxzOV631PhBCDg4QIITZDbToknfsn2YrDsI5D7NTQUfc+Ms2P4ZidN0iklr1MXFtPYdKemISD8hT5vfYD31LxT5mRGCzi2COOqjBRNVgPMGjdieM14bgNaL2JmqLNEEaaX/5pKPfcX8OXP76OI/dvp3d1epDXpBxbGofCNYBSTBlZoD4R8Y9/V3PRH0YTxBpHG8bWhUwckmdKbcjI6oAhyYgxmZCaZEyiq66Fnov62KieC/xeL0OtFwYsxIbYKlyjQRUXDq/3WKXAcYob/MUx1nY1BFUYeoeTjZzD0j1TEfW639qe5znWoC0kjCFZ2oBmaid0/fXIA0Hp0W1aEylFznF43/eup6W5qaxlRYcdfAhf+PhlvNryGbIFg6titA8dBcuzTzicedxhzH7koY2ut9gWQRhy/6MPc9Kxx7II3lbSFAHLUknuG1rLP2prMFo6KwkxmEmIEGIzudE6kp3/JFdzWPGywKskO+w4MmsfQpvN78m+o8m88ihRTS12/CRwYmzCITpwP/JeRPJpaf86kOLYwcQZrElijYtSEcrpxPVa0U55w29zm8d3bhnFxFF5LjxrLXtNyWGNJdHrOjDKazyneLUdBoq6ZMxZhzRx0j4t/GlOHb95uo7FDQkWNyR4bCPncJRhXHXIhOoCu9bkGZWJqPcjxiQCqj2Dt97mel0X/bZXuRMQx8XAYHoNbL39NHRxDVRsutda9A4D681UdB1X9fq813h7t9C1b3/6eo/t+lwBvjH4wLBp05hy3HFlLyu69kc3cuNV1/Ba8y4EzEO7imzeIczF/PXOOi79zARu/e2vynK+Db069zXOmnkacSYDnZ0YYIXv8XRdDfcOraewDWVfQoj+JSFCiC3ghyuh7VlydQdjHZeYDB0jjiWz5mGcuDz/yG9vFFA156+01p1JPHwoXsLguBHxYfsTOjHeE88N9BB3OsYoTOxjjQc4KBWivQ60k6Wv39xdtDLJF68dx3t36+BLJzcwdWRx7VAUQlL3uqgO6L7yTmrL549o4LT9mvnlU/Xc+a8a2Eh//9hqFrUkWNSS4LElVW+731OGsemAiRUBU1N5xqZChvkho4mocmJ8W7w4x1pUISxe0Wtd7DBVvBldms4wyituPGDNeiFjvdmHrvUVvcqdTK/AYVHr7b8BGw8OG37eZeLnP09TQ0PflBW1NDKx5mO82vw9wrwh4Ub8/W6PEUPGo7Vm/sIFZT1nl7cWzEdpTTx9V2YvXcx9w+pp9aSzkhDbIwkRQmwhv7AM25YkV/NecDXGr6Fj1PFUrHoQJ+oc6OENCB2HVD14Fx1nfhztJtCexfVAHf4eLBHqiRcHeog7BWPAWo01xXdzlROiVBbH2fpypa31wusVfOL1NKce3sqnZjRS4RhUaRxBXpHQPVfjji0u7K7LxJx35Dr+d78mfvL0EP7+ejVb0nontJqFnUkWdiZ5hLeHDAfDuETIlGSByW6BCV7ACDdkqFLUuS6JKCJpiyU8BlVs6qQ0KI1VEaq0F0Zx1L320OtdwrTeVIR92/2bWCeO3chtQ447jvsefbhvyooefIgTTzqIbN4l4cYsW6F4/D7D3nsUi4ty+b4p08wXiqHyZ9On8nK885aCCrEjkBAhxFZIdL6FdTzyQ/YHY7CJCjrGnUjFkvt22hkJJ9tJ5r57Cc44BcfzcG2Ioy3O0fsBEfET/xnoIe7Qei5ULUpHaG0HwVpUzT1P1fKXOVWc84EGTjmolZQfo6Ke+p9CwSFZWlBgrMW3MLwi4jszVnPme5r4xT+H8OiCtweCrRGjWVRIsKiQ4KEN7rNAOGFXRrx3V3bNNzGlfQ27tK5kVK6Fuo52RnS2kIny3Quzje3dTarX7MNG1kz03pVjY8Fhw3EAuBUVVE+bxit/+sNWvNJ39+rc1zjzo6fhuJUEKsu9v8oDiiAorgRPJZN9ct5kIgHQfR4hxPZLQoQQWynZ9jpWuxSGvge0xjgZOiZ/kIpF9+GEHQM9vAHhrlqDuv8hmHlsMUB44NsQffReRDqm8NirAz3EHVZXYNB6Y5emAys2Dj/823B++2g9X/7AWmbsVuwCZa3Fs6Z7siHIadKlK+8ohmm1AdfOWMGbDY3c8NRQXljZd+09FeAvfoOGxW/w6JR9+PvuR2PHJCgtkMCGFmUsu66ex54LnmTXxkVM1QHDTUS1jRmpQ1LGrD/70NXdqdd5zMaXV3R/3vXYzOTJfV5WpJUmlZjIC8++xsL/FkewZNlSjDFMmTSZl/9b/t/XqZOnYIxhybKlZT+2EKJ/SYgQYhukWl7B+mkKtbuCpzGqko5JJ5JZPBu30DbQwxsQzhsLsI9W4Mw4EJ8ITYzrKZLH74W2MbnHXx/oIe6wBn7m4Z21drpcccco/jAsz4UnrWW3Ybnuzk0mhmSvlkpRoPBKMxSTqgv87PhlvNqQ4nvPDGduY6rPxqiB5PyX8Be+Qn7yfuSnvRdrNMWGsJY3aqfwxnun4jUuJ73gKdzOBqgsPdlaJhQK7BrkGRcETOjIMySMSEUxlUGEv0EL2Q2DQ+/bdOkd+74uKwpyCR78Xc+eN9lcjoVLFrPXbntw91/vLft595y+OwsWLyKb23mbUQixo5AQIcQ2Sq99Dut5BHW7ABaTqaZjlw+SefNveDtpkFDPvIweVomz3yRcD1wV49iQug/sQbsNaXvirYEeohhAC9cm+cKvxnHolHa+euxaxtWFhAVFSnVt4gYp3Wu1c1Asf9pzaI5fzFjC62tTXPX8cBa19k3JDYA2Mem3nie56GXyk/cnP/49xU3plAPGEmZG0rb3R/FXv0lq2XM4YRaUYnEyyeKuUqAhGxzUWkbkC0zJ5RlTCBiez1MfhKSiGDeKcI3tCRali/y+Lit646UsLWvWXzMz57ln+cBxM5j1g++VdT2G73nMOPpY7ntwdtmOKYQYOBIihCiD1IqnsI5HMGQySimMn6Jzj5OpeO0vuPnWgR7egAjvfRq/PoU7bTiuiXAdcHXMsJOm46iY5scXDvQQxQCbM7+SOfMrOPk9LZxzcAOpVHH1gAnpXnAQBLp7EbY1Ft8q9h+W5c4TF/PYkgw3/Gc4K7P+Js6w7XRUIP3mHJKL/k12/AEEo/bARjFKaTAQ1E4hqp6Av+o/JNe8jLbxpg+mFKtTSVanNhEMrKW+EDAum2NcWwvv6+uyImu499Y33nbfbXfdzifOOIsZxxzH32bfX7ZzHn/0sQypr+ePd91etmMKIQaO7OQiRBloIL30Mbz2FVgseB4mUUH7Hh8mStcO9PAGTOfvH4M1jTiOwXNjXBPguoYxp+zKkCPGDvTwxKCguPc/tZzws8n89sU6Wjp1dytYay261zV5EDq4qqcI6OjhHfz1uIVc+d4V1Hjl7WC0IR3kqHjrCar++Xv8NfMAC1GIAoxyKAzdh/ZdTqNQPXnrT6IUjckEL9XV8Jeaiu6yor6w5/TdWbZ6Ce1tby8rmr9oIU/MeYqvfenLZNLpspyvIpPhwnO/whNznmLBInkDQYgdgYQIIcpEY8m89Q/cQkOpON1gK6ro2OcUwlTNQA9vYAQRTb98HCeXxTEhrjZ4ToxHwMRTpzDiiFEDPUIxSERG86Mnh/HR303koflVREZRKDh4qmcvBq9X/9SooNGAqywzRrbx4FHzuWz3laT0O8wElIGbb6Ny/qNUvXQHXvMyAFQUAwrjpsmOOIz28ScRJjasZdpyc557lhlHH4vnlrdowPc8Tjj2WB5//JlNPuayq2dRW1PLN8+/qCznvOSrF1JTXcNlV88qy/GEEANPQoQQZaSxVLz+d5zONeB7WKUwiRTtB59GVFE30MMbEKY1x9pfzcEJA3zP4BPiEpPwDbueNp5Rhw8b6CGKQaQ553HxA6M57f8mMnd1onulcRgonNLC8SiGRK9eqnGhuO/ER8a08o/D53PRlNX4qm/3xnBzjVQueICKN/6C074aABVHKBRRYgido2bQOewIjLP17+TfdtftDKmvZ8Yxx5Vr2ECxrKi+9p3LipavXMGsH3yf00+dyTlnf3abzvelT3+O00+dyXev/R7LV67YpmMJIQYPCRFClJk2IZWv34fONoGKsb6LTaRpO/BUosptf3dye5Rf0sKqO17GswGOjfC9GF+FuCpm77PGMv7wnTNgiU1b0pLg0/dN4JwHx7Kw2SfB+qGhqxFVGEGCnkXYlRg+PrqJRw99i8+MXYez0b2gy8frXEPVovvJLJ6N7mwEimECpQky42gffhL5qvdgcLb42H1VVnTReZtXVnTHvXdz3c0/5PxzzuOqS7+zxWOoyGS46tLv8NUvnssPfnwTd/7lnm0ZuhBikJEQIUQf0GGeypfuQZtcqbQpxlRW03b4R4mqds4g0fbSKlbd9xYJz+DrCMeE+G6M70Tsd+ZwJh1ePdBDFIPQsysqmPnniXz/xeE05R3CCJLdGy1YCKBro4kgUnil+yp1zDkjG3hs37c4Y3gjG9/arXz89uVULf076RWPo0td2VQUY7VLvmo3OoecQJCcuMWjKHtZ0fkXUl21+WVFt/zyVr5xxbc5acaJ/OPOe/ngjBPftbzK9zw+OONE7r/jz5w040QuvvwyfvKrn5dj+EKIQUS6MwnRR5wwR+U/76b94JmYqtriAsxkgtajz6D6sf/DbWkY6CH2u5UPLqV6lM+YA2rxXIPvRLhxgOfHHPbJehwb8tbTO+eO3+KdaG6fV8edb9Vw7h7rOGNSM0ltCSLdM0NhLU7cs1FGEGiSGGrdmK+PXcOn6xv58eqh/Lmpbxsd+B2LcTsWE1ZOpZCZjnErIIowOkOu6gACbxLJ7Mu48eb9/neVFV192eWsWLWSm39561aP7Uuf/hynnzKTiy+/bIvKiu64926eef45rvjGpdx41TU0XPB1Zj/yEK/OfY23FswnXyiQTCSYOnkKe07fnRmlLkxPzHmKy66eJSVMQuygJEQI0YfcXBuVL/yFtsNPwyQT4HsYPNqOPp3Kx+/Ga1w90EPsd3N/O5+aIdMYMT2FGxfwnGKYcOKQ93+yBsca3pjTNxtsie2bsZqbXh3Ob9+s5+vvWcP7a9q7d7suhMXQUHwc+KbXxnWhYrgb8d0xq/hEXSM3rx7GQx1VfTZODSTa38Jrn09QsStBcipWpyCOid1aOquOwssvJZl/FW3ffdO1O+69myH19VxwznmMHjmKK6+/hs7s5oftikyGS86/kNNPmcl1t2xdWdHylSv41LlfYMrESZw583QOOfAgzpx5Glr3FDQYY1iweBH3PTibP951u3RhEmIHJyFCiM1QU1PDj354w1Y/f531uS8xlgIO2rXEWpE48XhOyC1jhAnKONLtg9ERDaNfAL8NRxfwbYxDiKsDdp81HJYdjGqZ2q9jcl0X13XJ99EOwaL8XutYwm5v/pSa5rkkFChTDBFx7OOY4mZtFoeEiburmXZNu9w8dg3t9UnmHvJZmsfsvdnncxwHz/O2+GckNLCwqYqlDRkio9FYsOBgGVffwcSh7XibsWTilbde55QPfpgjDj2M7990PbMffvAdN4PzPY/jjz6Wi75yPnX1tcxZ/iLT99ptm/6WdXlr5UIWrl5COpVCK42xhmwuR2xiho4dxle+eu42n2Mg1dTUDPQQhBj0JEQI8Q5yueLFgtaaurqtX/xbB1TaDv6shlLQGhfQbsQjVZP5aNDICNu3Pe4Ho6rmI1k9ajaOU8C14OgYzxpcJ8ad9BjeujS6c89+H1e6TAtYRT+oq2PBuJ9Ruep5Jjx/Pcm2FVg0bhiW1iKBjR0gBgXWuugoBAWVjUt4793fJjd8Cos+fCHZ0dM3+7Rb8zMyfAjsO6nAm6vSLGtMEhuFBpqyGTqWD2Pa6A7GDg27hr1R2TDHa4vfYPzwMdx41TU0XfQN7n/wgU2WFZ1w3PHU19QyL1jO7LaH2a1txDb9HXsnDlCd6LtN/wZK178BQoi3kxAhxDu46667mTnzI6Q2tcPsFkgChzjtPJgajXENsQWs5TY3wfHNLYwMd74ZiWTnnoSTnsQ6nWgToWwMOo8mQtXeTkdbG0Hr5l/cbfU4ksnuC0NjDG1tbRjTt119RPk0Jaaw5LCbGb3sASa/dgdJsw4Ai4sulH6vrMWGlq696oxx0WFIevlcdrv507QMn85rJ3yJziHjNnqOyspKPM8DIAxD2tvbt2qsYzJN1HuaBWurWNOcxJZmJF5ogblJxdSRrdRUvfObCqvWrKYilWHcyDGcdMIJnPXR01G90oexljWFFubatTzb8jRNcQt7Lq6hKde0VWPeWeVyee666+6BHoYQg5aECCHewfMvvMjzL7xY1mPmJ+5Cx7EfwiqF64Yo3+HRfJ7MX+/GXbGqrOfaHux6SIIPfSGJthEJNyahA5woIulHaP96fvUHn5ee7/t3OL983pc44ID3orWmtbWN71z+XYJg5wt22zuXSr48Ls/pQ5twwxC/VMcUhIpEGBJT3Anb5kJKG2MThIrKBS9zwI8/w2OFCr7XOYIV9PzMnXbaTD78oQ8C0NLSwjcv/TYtLS3bPNaYNAVvN2I7tHiDicGAxzo88zqOLmzWcdKpFOPHjsP3ffwjptIyOUlo82hXQxiSe30ld/z6hW0erxBC9CYtXoXoZ8lFb5J5/B+4XjFAYC1OhUPhYx8hHD1yoIfX7954psCzf86ScEoBIg5JuiEJHZBQEed8pY39D+z7jk0/u/UXrFixEoDx48fxpXO+gONseW9/MbAiNNctHc6x/5nKk20VxFYVf8fCnscEge4OEMba7kXYGjiCDmYn53Odv5xqIo484vDuABHHMT/60S1lCRAADlnS4Yukojk4toGuLS0iW0/eHEIhnkocv0N9U0k2l2PuvDd5ZfFbLB6h6YhiQp0gKFjiGNbe82pZxiuEEL1JiBBiAKTm/ZfUnCcAg+tH4GnwXcxZHyYeP3qgh9fvnron5I3nCngmJOlEJN0QJw5JOCGVqQLnn9vA/vt09ukY8vk8N970Q3K5Yrec/fbbl89/7jPrlYmI7Udr7PKVxWP58JsT+WdbBqc0I2GMxY96dW6KdPfGdVEMfmxxgRNVK094i7hKr0LliyH2tv+7nTfefLPsY3VpIx2/QMo+j0MrGINFEdoxFOKDCOLR2M3YYCJ5zN5YP0GkfcKCwTgeTU8uIm6Vun4hRPlJiBBigCRf+jep558BV6NMcUGxSiWIT/8AduKYgR5ev7vjx4YVC2JSXoBjAjwVkXZD3DAko0OuOG8lB+7V0adjWLlyFdffcFN3GdMhhxzM2Z/63z49p+hbi4MkZy+ZwOdWjmNx6BMGPaEhtpDo1QrWhtDVMzbGIWMMw566j33POxHz7fN49P5/9OlYXdVCmn+SVK+gVWcpTPgE0WQKwT5EUc2mn1yRwt13KqHyiAKD0R6F5oD2h/7bp2MWQuy8JEQIMYASc57De+5FXNegHA0mwk272LM+gJ0waqCH16+sVfzkKpemVQbXRmS8ACcM8IKYjIlIWMtln17N/rtt3YLWzfX663P54Q9/TFRqnfm+9x3Fxz9+Zp+eU/S9OdkKPrBkCj9oGUaLLZapmbBnlimKevaWUIBve5YM2s6A977yDM/m3+SLwVqcPl507+oG0s4/STqvoyigTExsMgTBdPL5XTDm7Y0evOP2J3aTRAVLrFxC69J+/0vF/rJCCNEHJEQIMcASjz6F8/LrEEe4DqA0Sivc/zkRJu1cpU2FnOa672aI8zFeFOIGMWkbowOFKUClG3PVJ1ez39S+nZF46T8vc8tPftbdoemEGcczc+apfXpO0T9u66jniNVT+XlHXU+JkLWo0iyEUqCcJCqOgWK3LnLFmamMNXwh18CzrfP4n3wjm1VjtA1cZx1J9zl8bwFKBVhrMXEt+exeBPmxGFNas1NTgdlzF6LAYB2XCJdg0TqClxb16fiEEDs3CRFCDALu3x7BeXM+KIWOI1wPlO/innEsetrOVdq0bo3LDddUYToMKRPjRhaTL75LrEKLG1u+d9Yq9pvYt2sk/vnP5/n5L37V/fUpJ3+Yk046sU/PKfpHjObG9hG8r2kq/wiqyEUa1xZnIBztoINigLDWUij0tIWNLXixpdrEfLNzNY+se4uZnc19OlatwXNXk/RfwPeWgorBWqJwBIXsnkTBEMwRB2CsJnZ8AusSFwz5+6UbkxCib0mIEGKQ0Hc9CG8swPGL+2TpOMLPOCQ+fgx66s41I/Hf1zL87Nd1OJElyikcAzqyRDmNF1sqiLnqlJW8Z2zfBoknn3yK3/z2991fn/Gx0zn2mKP79Jyi/7TgckHHGD7WMZHX/Wq062LwimsRrCWMY7yw15qJSHUHisjAmELIlU0reWTVPI5ra+nTsWpt8fyVJJP/xvVWolSMRRGkphFMfS+RShPGmjiwBHOXYZet7dPxCCGEhAghBgllLfqOB7CLVqKjENezxZkJZan4xNE4u+5cMxIPPFnD//21Dh1Z3NgQ5zROaHFCQ5RXZBzDDR9ezl4j+7b960MPPcyfbr+j++v//d//YcaM4/v0nKJ/RRN2ZdVVd/HGV39EUDO8WDZkDHGgehZhG/C6FmFbIOhZTzEkH3H1yhXcu+gt9uvs21I7rWP85AoS6Vdx3XWY9+2K8ZMUgirCfIYo0pj75/TpGIQQAiRECDG4xAbz2/vQ6xpBKVQU4voK5WmqzjgMf/exAz3CfvXze4cy56UKTE6hAosbWeK8hhC8yJCI4frjlrPnsL4NEn/7233c+5e/dn/9/z5+Jp8++5Oyj8QO4MADD+Bbl15CbU0N7bvsz58/+32+64xmrXHWawVrY0WpSyyhAbcUKKyFqDRbMbYQcNOipfzuzfnsmu3bn0mtQ5zh7bBPNVEYYgJLrJMUHllN1FiBMdKaWAjRtyRECDHYRDH5X9yHXbEO1y9eCOgwxE17VH38cPzdd67Spm//ZiRvLk7gxRYbKAjAjw0mr7AB1KiYHx65nN3r+vai7c477+aeP9/b/fX73ncUF198IRUVFX16XtF3Tj31ZM479xwSiQQAb745j2uuvY7fh5W8j6n81q8jrzSRKa6FAMCC7tXVKRer7k3ijAUiy6RcgZ/PW8R1by1iXK7v9mjIHXIoUaRQpgPcLPG6ZtSTc4mjCqL8WMKwsq/XfgshdmISIoQYjAohud88gGlsR0cBbqL4q+oSM/R/DyO5585T2mSs5vxfj2FNg4splC7m8hQ/jww2DyljuOWgZexe1bdB4u67/8zNN/+kex+J3aZP54rLv83oUTtXO97tne/7nPulL/KRU0/pvu2JJ5/iqqu/T0dHcZ1NrDVXeyM5PDmVh3QVcWnTwdAonNIshLFggp6r9EKv3aVjC7t1ZPnpGwu4csFihhYKZX0NUXUt+THTsQVDZDzigiH51AMk3MUoncWiMWENYWE4JkqU9dxCCAESIoQYEMYU/3tHHXk6fvYPdL548eFEBZyEBkcz9Iz9yeyz8wSJjoLLeX8cS65TowNLXNC4EcXPA4UbWiqjmB/ttZxpFbk+Hcszzz7HrCuvprmlBYDhw4fxne98i7332qtPzyvKo7a2lksv/QYHHXQgUGzh+sfb/sStt/6ie2+Q3tq1y1czYzmxejL/8lI4Qc99uainxCkuzUJ0yZfyhAL2bOvkJ6/P5+KFS8ls5BxbI7vXYRBBHCcwWVBLV+K98RbaKZBIrcHz16B0DqxLGNYSBTU9LWGFEKIMJEQIMQCsVVj77jXLtjVL880PolrbcBIO2GKY8NIuw856LxX77DylTctaElx630hyWY0TFRdYx/nSYutcMVhU25hfTVvCtGTfBokFCxZy2WWXs2jxYgDS6TRf+9pXZcH1IDdx4gS+e8W3mTxpEgC5XI7rr7+R+zdjJ+rFToIzqybxuSFjWeb5GAu29yxEr2wQ2p4tJCwQUvzH9oDWdn7y2lucs3g5idI+FFsjrKghGDMVazzIxdgI0k8+vt5jtJvDTzbgeI0oFWCMTxTUEIVpWS8hhCgLCRFCDASri/9tBtPUTvOvHsd0FnDjAq6vsdbiqpjRn9ifyn13niDx/PIKbnhmGDosLrBWIbh5SxTo4h4SBUsqsvx8/FKm+H1Xiw7Q1NTEd797Jc8/X+zHr7Xm/338TD7z6U+RSPh9em6x5Q479BAu+9Y3qa2tBWDt2nVcfvksXvrPy1t0nCeTlRwzYiqXVY+ko7SwPjLF7RugGB56/+SF0N3hyQIYw4HNrdzy6pucvmzVFu1+nU6lmD5tF6Z/4Az2HDqEithCDIl5b+A2rNnocxw3j59swnHbQUVYkySOKjGRL+slhBDbxB3oAQixU7IaiwNs3ruR4cpWGn/5BKO+eDjWKlwToj0NxjDurD1Z4ULL8yv6dsyDxL1v1TIxVeCMsc24pXImFVjcsPR5CLVRxK/ql/DJteNZECe36PjpVIrxY8fh+z5BELBk2VKyuY3PbBQKAT/80c2ceurJnHrKyQAcddSR7LbbdH7+i1/x+utzt/Xlim1UU1PDpz75Cfbbb9/u2954801uvPFHtLe3b/Vx76yu4+7KGs5rWstJq5tJllZXB4ruEifL+r/hvcOFtpbDG5o4qKmZR4YN4e/D6mEj3b6mTJzEmTNP59CDDmbS+Alo3fPmgzGG+Q3NzHk8yZ9WzGX+ooWbHK/j5tBODhMnMLGHMQkwLtotoPXWz4oIIXZeatI+u29X70X86Ic3UFdXR1NTE+ee99WBHo4QWyUKU1jr4Plb1lM+OXUYYz59AE7KBWPwCNGuxoYRK29/lcbnVvbRiAefG/dZxuFVHZgAvLDYuckUwAsNNq8wIWRDzf9rncBC+85B4t0u1BYuWcyc557ltrtu3+SF2kEHHchnP3N2d6cfgEcffZzb/u9P5DYRQkTfOvLIIzjrzI+RyWS6b3v88Sf49W9+t9H1D1urMoy4ZMVKDmlup/fS/gLdjZswsN59nfQEjAjo0JqHRgzliWH1oBRjRo3mim9cypGHHk5DYyOzH3mIV17/L/MXLiCXz5NKJpkyaTJ77bYHM44+liH19Twx5ykuu3oWy1e+8xsKxoA1CYzRKKVQRCgnQEttghADZnu8vpUQIcQACAuVgMZLtG7xczN7jmDM/+6P68Q4roY4xtcRSsGiP7xGw3Oryj/gQcjB8Pu9FjPdy6MDiAKFF1jIW+JQ40YGlYfG0OP/ReNZqt7eoabcF2rDhw/j05/+FLtNn959W1NTE7/61W+2uGxGbL2hQ4dw9qc+yZ577tF9W0tLC7/+ze948cV/9dl5R+fyfGPpCiZn8xiKIaJLlp5AEbF+oOgdMRs9l/jLX+b/XX4FzS3N/ODHNzH74QcJ3yH0eK7LjGOO48Jzv0JNdQ2zfvB97rj37ncdrzGA9YprJJRCqQitY5QsmRCi322P17cSIoQYAGGhDmMcEql1W/X8mgNGM+7/7Q3W4qsQ7SgwMS4RC/70Fmue7v8gsSVlQOVS6UT8eeoC6ozBCS06Z4kjjQ4tTt4ShRonNLQVHE7zJ7Lc7QkSHz/tY1z85Qtoam7m2h/fWLYLNaUU73//+zjjY6eRSqW6b396zjP8/vd/pKOjb3c03pkppTj2mKM5/fSPkkz2zD49+dTT/OEPt9HZ2dkv43hPWwefXb6KEYViK6eY9YNCB+sHirD0uQEmXXIJ+155JbffcxdXXn8NnVuwaV0mneab51/E6afO5Lqbf8gtv7x1s55XDBMuxoJSoFSM1tvVpYEQ273t8fpW1kQIMQCM8cA62NI/2luq5fkV6IRm0mm7oB2FjWN8J0Y7DlNPn4LrWFY8sbr8A99AOcqAtkV77PKZBeP5w8glVAcRUahRUTFAxKHCCSy6AJWh4U+5xXz9Pcdw9Mc+zknHn0B9XR23//kurrxu8y7Uwijib7Pv59EnH+eb51/E1ZddzpD6+rddqFlreeSRR/nPf/7D2Wd/srv162GHHsKee+zBb377u+7F2KJ8Ro4cwWc+fTa77DKt+7aGhkZ+9avf8PIrr/TrWP5TVcEXd5vKjHWNnLVqHfTqxBTQEyC6Ojd1GXv22ex75ZVcf/MPuXkzA0Bvndksl8z6DitXr+KCc85jXUMDd/7lnnd9XvHXNioNrPh3qdjByUqJkxBikyRECDEQbAKLgzEKx9m6d/yanlpGIu0y5qSJ+I5BOxobRSR8w65nTQJjWPHU2jIPvGhjZUC3/vZXGy0D+sBxM/jEGWdtdr32lloUJrlozWhuqliGV+rQ1LXAWuctJlToEeMZMusWfnf0CbR3tFNZUdnnF2qNjU1cc811HH74ofy/j59FJpOhurqKL5/3Jf772mvcecfdzF+woBzfgp1aVVUVH/7wBzn6/e/D87zu2x96+BFuv/0Ocn24Y/S7mT20ngfqa/l/K9ZwVGMzjrXrlTj1nvdKTpjAPjfeyO333LVVP5e9/fgXP2PUiJF868KLefaFf27271wxMMSlPWyK7250dXCSEichxIaknEmIAZDvnApovOR8HGfbOqOMP2US42aMhyjCd2OUVtgwwncNr/9pCUseLW+QOO3kj3Dp177e5/XaW+pMv5FL1GpsoLABuAWLDRV65tk437mBtS0t/Py233PBOV/m77Pv55JZ39nmc1516Xc4acaJnHjaKe94oVZTU83/fuJ/eO9791/v9n/969/cedc9LFu2bJvHsrNJp9N84AMnMOP440kme8rUVq9Zwy9+8Svmzn1jAEf3dqko4pNLVzK9tZ2uBk69480B99+P3mtPZpx+6haVMG1KRSbD/Xf8mfkLF/Cpc7+wVcfo3QJWQoQQfWt7vL6ViUoh+pm1YG0Sa33KMRm45M8LWfXYsu4AQRiR8C3aUez+0dFMOX7otg+65Itnf5arL7ucv8++nxNPO4W/zb7/HQME9JQBnfDRk/n77Pu5+rLL+eLZny3bmLrcFtTzp6AOWygGCEKF8/lL8K/9OXc9MJvjTz+VIw85jOaWZq68/pqynPOqG66lpbWFK75x6Ts+rqWllRtv+hE33vQjVq/p6ee/3377ctWVV/Clc77A2LFjyzKmHV0mk+GUkz/MjTf8gJM//KHuAJHPF7j3L3/lG9+4dNAFCICc63LLpHF8d9cpLE0n6bXxNZnp0xlzwglcc/MPyxIgADo6O7n2Rzdy5KGHM3nipK06RnF9hAQIIcTGSTmTEP2sGCJKZRebsWv15pj/p/kkMpoR+9WS8C1KgQ1CkknDnqeNQlnDWw82btM5Tjv5I1xwznn9Xq+9JWbZkUyMCxxc6ER99Gy8r8/qHu+UiZM48tDD+colF5X9Qu3Gq65h8sRJLHiXdR8vvPAi//73SxxxxOGcesqHqaurQ2vNwQcfxMEHH8S///0Sf/nr35g/X8qcNlRTU80JM47n6KPfv96C9SiKeOSRR/nLX/9Oa+uWdzvrb2tTCa7ZZTK7tLXz0aUrqQ4jxn/+8zQ1NDD74QfLeq4HHnmIhsZGzpp5Oldce3VZjy2EEBIihOhn1rqgiptK2TL+Cr72y3mkMlMZvnctBCHJRHH5popC3nvmUFxtmTu7aauOPWbUaC792tcHtF57c30uMY6/1RkmX37DeuM9c+bpxfUbA3yhFscxjz32OE8/PYdjjnk/H/rgSVRVVQGw7777sO+++/D63Lk88vCj/OvfLxGG4bscccc2ZfJkjjjycA4/7FB8v2cn8DiOeXrOM9xzz700NDQM4Ai3zptVlczaYxcOWNfIj487jvsfffhdZ/W2VBCGzH7kIQ458KCyHlcIIUBChBADQGOd4kxEOUMEwIs/eosDvzyF0XtlQIEKQpIJCyj2OaUWzze88teWLT7uFd+4tOxlQIcdfAhXfOPSra7X3pRIa9Z9/6dUtrSsN95DDzqY2Y88NGgu1MIw5B//eIBHH32Mo448kg984ATq6+sB2G36dHabPp1sNsvzz7/AnDnPMPeNN7F2u1rCttWGDRvGYYcewqGHHsyIESPWuy8IAp548inuu+9+1q3b/sLDhl4bP5baadN45U9/6JPjvzr3Nc6ceRrpVKrPWy4LIXYuEiKE6EMb72yiQTulzx3KysILN88n9fWp1I31SgECbBiQSMN+M+tQxvLy3ze/7GMwlAFtiSkTJ3HoYUesN95MOs2k8RO49be/Ktt5etuWC7VCIeCBBx/i4Uce5bBDD+GkD36AUSNHAsXFw0cddSRHHXUkjY2NzHnmWZ5++hlWrCjv7M1gUFGR4cADD+SwQw9h2rSpb7s/l8vx8MOPMvuBB2hpGfxlS5tr3JixaK2Zv7BvStjeWjAfrTXjx45j7rw3++QcQoidk4QIIfpQcf3D+m1cDR7GKZUzqfL/CpoQnr52PsdfNpHU6ASEAYkkgEWHIYd+rArHsfz7L22bdbzBUga0uTY23u3hQi2OY5548imefOpppk/flUMPPYQDD3hvd/1/fX09H/rgSXzogyexaPFi5sx5hueff4HGxq0rURsMkskke+65B4cdegjvec/euO76vw/GGF6fO5c5c57lhRdeGNB2rX2lq0Qrl++b15YvFNY7jxBClIuECCH6kLUKG7vExDhOaYsp7YLqWljtbfrJ2yAqWB68cjEnXDKG+vEeWIsOIxIJAMvBJ6dI+IZn73z33ZMHWxnQu9nYeLenCzVrLa+/PpfXX5/Lb3/7e/bddx8OO/QQ9tprT5xS+Jw4YQITJ0zg42edSUNDA2++Oa/437x5rFixctCWPdXUVDNt6lR22XUXdpk2jfHjx623QWGXZcuW8fTTz/DMs8/R1LT9hqTNEQTFPk2pXjtsl1Oy+EvffR4hhCgXCRFC9CGlLJYEJo5wnNIFrPbALZUxRV6xYXwfCLOGh65bzknfGktVtSWRsIBFhSGJBBz44TQOEU/fuekL68FcBrQxmxrv9nqhFgQBzz33T5577p9UVVVy8EEHceihhzB5ck/LziFDhjBkyBAOPfQQADo6Opg37y3enDePeW++xcJFi4jKHAA318iRI5g2bRq77jKNabtMY8Tw4Zt8bHNzM8888xxz5jzDkqVL+3GUA2vJsqUYY5gyaTIv//fVsh9/6uQpGGNYsmzn+Z4KIfqHhAgh+pDWEBkHa32szRdbryoXWyrbMNZff9vaMss1G/5x9XJmXj4c62t0XAwQxlhcE3LER5JoBU/esfEgsT2UAfW2qfHuCBdqbW3tPPDgQzzw4EOMHDmSgw86kF133YUpUyaTSPRstlZRUdHd5QmKQWTdunU0NDbS2NBEY2Nj8fPGRhoaGmlubt6qkKGUorq6irq6eobU11E/pJ76+nqG1Bc/Dh06lMrKik0+3xjD8uUreHPePP714r/572uvDdoZlL6UzeVYuGQxe+22B3f/9d6yH3/P6buzYPEiWVQthCg7CRFC9DmNtSlMnMRx81jHBa80E2HcPg0RAB3rYu6dtZaZ36ylqlZjbTFA+L7FGsMRH3ZI+B4P/eHtrUS3pzKg3sfZcLw72oXaqlWruOfP9wLgOA4TJoxnl2nFd/t3mTa1u2UsFL8no0ePZvTo0Zs8XnNLC02NTRQKBeI4Jooj4igmjmO01jiOg+M6OI6D53rU1NRQX1/3tjUM7yQMQxYsXMi8N0uzJPPeIlumhfrbuznPPcsHjpvBrB98r6xlg77nMePoY7nvwdllO6YQQnSRECFEH9PaYuI0URTjuKvB8cArroUwUd+sidhQy8qIv1/fzKkX15BOxvi+xcQGjwjXg0M+4OCpiPt/v/47wdtbGdA7jXdHvVCL45gFCxayYMFC7v9HcQwjR45kl1KgmDx5MkOHDnnHoFZbU0NtTU3ZxmSMoaWlhSVLlvLmvOJ6jUWLFu/0e15sym133c4nzjiLGcccx99m31+24x5/9LEMqa/nj3fdXrZjCiFEFwkRQvQ1HWPiFNgExqzGOC7W77Umop+sXhBx3w3NnHZxBdbY7gBhI0NChRz5IY1WMX//Xc9ztrcyoHca7850obZq1SpWrVrF448/0X1bZWUl9fV165Uc1Q+pp76ueFtNTfVGFzlvTGdnJw0NxZKoxqZiiVRjQ0+ZVEtLK3Ec99XL2+HMX7SQJ+Y8xde+9GUeffLxsrRSrshkuPDcr/DEnKfK2kJZCCG6SIgQos/lsMoHNHFUjXITWL/4q2fD/m27uOT1mLtv6ORjX/Vxk8UA4esQxwEbG475YEjC09z9y2LI2d7KgN5pvDv7hVp7ezvt7e0sXrxko/crpXBdF7dUtuQ4Lo7jYIwhjuPSfxFRqcxJlNdlV8/i/jvu5ZLzL+Kbs76zzce75KsXUlNdw2VXz9r2wQkhxEZs3ttOQoit5roRygFcj1iPwPg+NuEW//MT7/r8clv4UsTfbi0QFXoChIlikk6Ao+HwYyPO+nyh+/FznnuWGUcfi7cF9e+bo6sM6Jl/PlfW477TeC+7eha1NbV88/yLynKuHelCzVpLGIbkcnk6OjppbW2lqamJlpYW2tvbyWazFAqBBIg+snhZB9/63t187NSZnHP2Z7fpWF/69Oc4/dSZfPfa77F85Y63MaEQYnCQECFEf/ALWNcndIYTex7Wd7C+g0n0f4gAePXpmId+X8DRYKOYtBviaDChIe1FHHV8yFmfyQOW2+66nSH19cw45riyjqGvyoDeabzLV65g1g++z+lyoSYGmSgax213Ps33brqH8885j6su/Q6ZdHqLjlGRyXDVpd/hq188lx/8+Cbu/Ms9fTRaIYSQciYh+oV2csSOB04Ck0yiEv2/JmJDzz1o8f2Yj/xPiNYQh4a0H6GUJQ4MM07sJOFF/OqWBdtVGdC7lS3dce/dDKmv54JzzmP0yFFcef01W/SaKjIZLvnqhZx+6ky5UBNlEYY1mCgDRNzyi1tobX2ZS7/2dQ47+BCu/dGNzH74wXdsBuB7HscffSwXnvsVaqpruPjyy+TnUgjR5yRECNEPtG7HJhKgFVF6BKq0FMJGAzMT0eXJv0NVleaYD0WkvVKAKBgyiRCl4IijcqT9kMuu/i7333Ev3zz/Ii7ZDuq1i/Xl92xyvLf88lYaGhvlQk0MClEwEmyE1gVcdzV33Hs3zzz/HFd841JuvOoaGi74OrMfeYhX577GWwvmky8USCYSTJ08hT2n786M0qzeE3Oe4rKrZ8nMmBCiX0iIEKIfOLYVkh5Ga8Lq4biJBhS2uNncAPv7bQ5VFRHvO6EUIJIhCoiCmIpkxFHvD7HRq8z6wdVcfdl3WbFqJTf/8tatPl9XGdDFl1/WZxc7K5Yv47/nn8/pP/3ZJse7pRdqJxxzHPV1dXKhJsoqiqqwptiS2POXoFTx9uUrV/Cpc7/AlImTOHPm6Rxy4EGcOfO09TpoGWNYsHgR9z04mz/edfugX9wvhNixSIgQoh845MGPwEtDdYrYrcGN2mEQhAiA22718f2YY44pLqiOSwECIM7FnHh0K48+8VPWXmY5/4pZg7sMyFq+OX8J2ZfnMq9+COdfeeUmx7s5F2rWWtY1NvD3B/4hF2qi7KJgGCiDo1tw3ba33T9/0UKuuPZqANKpFOPHjsP3fYIgYMmypbITtRBiwEiIEKKfKN2JTVZhq5JY34OOTrrrmgac4jc/TlJTGbPPPjkypQARZSMqExFgOXGfVlLNV9Ly2dV85PobOfKgg/nej28adGVAX1yygmmdxbCw8qqrKKxZwyk33sgRBx3M9zcx3t4XajVVVXzsIx/lE2d8nMpMBVffcB1/vOtPfTZesfOKogzWJFBEuInl7/r4bC7H3Hlv9sPIhBDi3UmIEKKfaNsK6XHYKg+TqcJEK8Ed2DUR69PceHWab88qsOdeEGfj7gBhOizDnAj3aIiCX9Ky/yNU3XgLN151Dc3nX8R9jz48KOq1T121loObW+nad9sDmn75S5555BGm31Icb9P5F3H/IBmv2LnFYR2oANdtwXFkN28hxPZFQoQQ/cQpNGAzPrbKgQoHE1WjOlsGelgbcJj17Touv3wd++xebPFqOqDGjfFii86Ceyw4zmJyp55Iftp0/LO/wEeOOWbA67WPaGrhrNXrAMgBpnS7C5jFi3npxBPJTJ/O2M9/nmOPP37Axyt2bnGUxhoHrUIcr2GghyOEEFtMQoQQ/cTrXIutdHHqNDZpUF417toWrNYoY979AP0kjjXf/e5Qrr06ZOLQPBWuocpGOFkgAVjwDgB9NXR+ay7R189jjXY5dc+9GTt+/IDUa0/ryHLu0pWU1qSSAvJA17ZoGsgA2blz+es3L+Gm39wq9eViQMVRBUrFOH4LWtt3f4IQQgwyEiKE6CdOkEW5AV61hUQMlUnc9hjjujhBMNDDW0+hoLn40uH89KrlVA6LSHUCPsW397OgPHAOgMrLILga/lRVR0chPyD12sMKAd9fsATPWrq+i4pikCgAXUUiGlibSnLT5HGA1JeLgRNHPliN0gVct32ghyOEEFtFdqwWoh85UTNeJsJPhCTSMW5tGuUPziyfzXqc+62xuCtK678tkAPlgjWg8qAPhPhb8Jua2gEZYyqM+NG8hSSNwaE4UdJbgmL2AVjn+1wxbSJo+bMnBpYx6WJHJq95oIcihBBbTf41FaIf+Z2rSSUjUomAZCLAG5JCJQdLh6a3a2/XONcbTDOo3gGiAHhgY4ina2747Cp6ViH0D2UMP1+wiJoo7r5N8/Yg4QMdnsc3d5mIkQAhBlgcu6VZiKwsphZCbNfkX1Qh+pHXvIaUlyfl5EjpPKkaF5X0BnpYm3RmoplUmyK+AWxQDBAEdAcIU4DAVew3qZObPrECpfovSNy0aCkT8gEZBY7quV0DyV6Pyzqai3eZSN4dnDM+Yudi4wSoEMfd/D1WhBBiMJIQIUQ/ctatK4YHt0BaF0i7Ad6uYwZ6WJt0WqYZL2ExbZC7BWgH5YCNgALkXE0UKnRBcdCkTm44azm6H4LE19esZN+Ozu6v04DXK0goikEi5zhcNHUibd7gDWpi52GMg8WiVQGtB08zBSGE2BoSIoToR04QkLI5UqpAyimQ0nkye44c6GFt1MHJdiYmAqxviVyFblCE/wcmD4RgHegIFDqwOMoSRoqDxmW55ePL+nRG4hNNDZzW3Izvg+0VHJKsX8oUK8Xlk8exMpXc8BBCDAhjXFAG7Q6uRgpCCLE1JEQI0Y9U0iUZdpB28qR1nrQTUDWxArR69yf3s3OGNqDSlsDXOB4o31JYrgjvBGWhPVQ4UbGUKAwVbmzRCvYckefW05f1yYzE+ztbOXftGqB43mSxyU03XxXDRKwUV04Yw7xMuuxjEGJrxLECa3GcADX4ft2FEGKLSYgQoh85CYdE2EFa98xEVGQMVXsOG+ihrWe8X2DP6hwFT+P4oFI9YYKlsPwvDtmCg6YUIEwxQASBwost+4zKcfOpy3DLGCR2C7Lc1LwCJ9FzBaYVpLzirEgXV8HN40byXE1V2c4txDazGq1jKWMSQuwwJEQI0Y8c38HLd5LSxZmIlMqTcQuM2L9uoIe2nnPGrSXyFNoHJ2UIfI1KgJOyBAnNDf8Zxg/+Ppx8QeF1BYiCwo8tGigU4L0jcvziI0vRKn7X872bkVHAH9YtwbeWtGtxe1UoKQUpl2J6AH4+chj/qBuYlrNCbIwxoLSBMvwuCCHEYCEhQoh+5KU1fqGDjM6RUVkyTo60l2f0bmkYJCUOaSfm4CFZlAduwlDwdPHzZDFMLNcef8nW8Zd/1fCLx+pBQVCAhCkFiAASWBSWadUFfvfBpds0I5E0ht+1LyZJz66+SQe8JN3fs2KQsNw5op7fDR+6bd8AIcqsWL5kZYsSIcQORf6kCdGPXF/hx3mSppO06goSAdXpPKP3rRjo4QHwvxMaSCUMbrIYIOgVJqwHP2ke0v3Y3z87hFsfrydhitfz+QIkrUUBhbwmaQ27Dclz6/FL8beijEMZw+0dCxlnQnTSEvXq5ZpwINErSDxUXcVNI0Zs24sXoo9IgBBC7Gjkz5oQ/chPKRIqJBFkSescKZWn0i9QobPscmBqoIcHGD44rg0vaQlcjfVU8XO/GCBWKo/7W2rWe8Yv5wzlTy/Vks8rUqXZgnyuGCAA8nnFPvU5fnP8YhJ6y8o5biwsZ9eoABSzgutbQrcnSHgaUkn4V2WGi0cM3la5YucmC6mFEDsiCRFC9CM/YUnoAm6Q7Z6JSKkclV6WybsZtPPux+hLHxzfysiaiMBXGE/hJ4sX7cYFP2m5YcXGF4Bf99hwHnurOJNSDBMGrC1+rixYy6RUwO/fv2SzZyQuCVdxvGkndFVPK1cFnmcJem0K8WYqyedGjpMrNSGEEKIfSYgQoh8lEoqkE+AUiuEhrXJkvAIVqpP6yhy77j+wF8Kf2LOZ0IfYVfgZS5SAyFV4SXgzSPJIw6Y7Hn3roVE89GYlKVsMDfmC7g4QxdImy9SKPL8+ZAnJdwkSH48a+J+gCQDXsUQemF5Bwvcsoa9Y7nl8bMhErNSKCCGEEP1K/uUVoh+lUjEpHeDk82R0cTaiws1RobNUOx0ccFg0YGN7z/As4+oLRFrhpy2hD6Fb/DxOwo8WvNuCZcXFD4/iuZVpCgXnbQHCWkuQ0+yRyfP7gxaRdjZe2nSkbePrzhrCXusfXA3Wg7hXxmpOOJw8dCIFCRBCCCFEv5N/fYXoR8kkJJ0AzwYkTZ60Ls5G1HgdVJBlnz3a0Vu4bqBcPvXeBiKt8ZOW2KP7c5OA1zuTPLm2cjOOovnSA2OY3+RDKTR0BYgwp0liscYy0Qv5v/0Wv21GYrrNcZNagUdx/UPQa/2D1oAPkVa0a4ePVk6k3fHK+j0QQgghxOaRECFEP0qnYtJugbRbwItyxRDhFKjUnVS5HdQnOznkkHy/j2toJmTv0Xm8VDE0hFrjJSyxD4FW/PT1Ie9+kBJjHT71wHheX5siQU+ASJQCRBQofAzjkwX+uMciMro4+1JPyE/8pSRKi7NVqWyp9/oHrSDnK86sHM9qxy/vN0EIIYQQm01ChBD9KJ2MSOkCKV3AjfKkyZHROSrCTmqiTqryOY7Zr6Xfx3X2oQ0k0waTsBS0xk1abNISOIq3OhLMWbk5sxA9Qqv5zGPjWNzhdQcI0x0gLMaCySumJQv8cbclDNEBtycXM9yJiTyL6Vok3RUk/OLXoVJ8PjmOee5g6GQlhBBC7LwkRAjRj9KJiKTKk1R5VK5A2mZJxQHVhQC/LSaVi9l7VA69DZuzbSnXiTlmz3ZIWQqqOANBshQmfPjhvzbekendZGOHTz4+gZaCgzEWUwoQcSlAeFhiAxPI82jtfEYTlMajML4l7tVtyXctuYTm6/5oXnQyZXndQgghhNh6EiKE6EdpP8S3BXxbwOQCUqZAwoY47eBmQbUpqk3M+/Zs77cxffzQZiqqYgpo3ATdYcLxLXNbE7y4Yusv2ptDlzOfmcC6Tq87NNArQKhAkWqBtLU4LlAqZXK0At8S6mKQMCiudkdwv1u9rS9XCCGEEGUgIUKIfpTxA9I6T1rn8W0BLyqQtAVsG3gdFtVuUW2K46a19dOIDB8+rIWC0mgfnKShQPFznbLc8OTwbT5DQ+Bx9r/H0VhwoKBwscRxMUAk2gxODlAUz+9DV5DQWuH4lkArfqaGcAe12zwWIYQQQpSHhAgh+lFlIiClCt3/uUGBRBzgZS22FfyshTbLPjV5FH3fpemovdupqTEoH9yMIa80ygM3afjXijQvL0+X5TzL8gm+8Mo4CkYRxaBC8AoGt9DrQQq0t36QUEpxh1PDTWxdSZUQQggh+oaECCH6UUWiQMrp+U/HAQkCnHZwskCbwuu0JHOG4yb0fUnTace2FENDxpJXGnzwKoph4pZHN78j0+Z4I5vi03PHEhY0XmDxOwAF+KWPJdoFJ1GMEY/YCmZFo8o6DiGEEEJsOwkRQvSjymShu5wprfOoKCClA0wruO3FWQjdDk67Zcawvi1pmjQmzy6TCngZSwGNdRReBgrK4T8r0vx3WfkXMP+3M8PVy4fh5umabCgGCK/0sXSbdiD0Ld8ubHs5lRBCCCHKzx3oAQixM6n28mR6lSmpwJDwIlTWYAsKL7bEocZzUuw/bhf2yU4mH4QsWbaUbC5X1rH8z8lN+BlLIVRYB5K+JQgVsYaf/qO8sxBdanXEV+vWEWtQtljWBPQEiRAwYAA/gHuSi/lIbhINSjaVE0IIIQYTCRFC9KMaW6AiWL99a0KHxO2gavYgdchn0dOOJTFiGkpr7io9xhjDwiWLmfPcs9x21+3MX7Rwm8ZRXRly8IGd5K3CokhlDEEIJoZXl6WYu7T8+zA4GH43bjH1OsagiDyLq0AFpQeUgoQJIe4o3lATxfxFLeRDdhKNEiSEEEKIQUNChBD9KBVZ3Lxd7zbtTCDzv7eQ2u0EmpsauO/hh3nl9T8wf+ECcvk8qWSSKZMms9due/CB42bwiTPO4ok5T3HZ1bNYvnLFVo3jtNPaKPgOOjCkM4ZCpDBKkUhZbrqzL2YhDL+cvJRxqYAoX/zDY1DErsVRoEoLrC09ASIIIRFZEjbijngRZzkTWK1ll2ohhBBiMJAQIUS/sbiBhbhnFXFm+Cdxx1/HuoYWvnHJRcx++EHCKHrbM1/+76vc/dd7mfWD7zHjmOO48NyvcP8df2bWD77PHffevUWjcF3DgYcH5HFJZSKyscZGlnQq5pn/pFm0vPyzENeOX8n+mSwAJmkJChrfWmIUyrE4SbB5iFqhd4DAQhAqRkch96iFnJqYxGpHgoQQfS2dSjF+7Dh83ycIgj4pqRRCbN8kRAjRT7SyxZampQxRNeFiaqZcwe1/vosrr7uGzmz2XY8RRhF/m30/jz75ON88/yKuvuxyhtTXc8svb93scRx1bAEv7YBvyVsXE8ek0yEdkctPbyv/LMRnR6/jfbXtxYUOFPd/UElDIa9JWEuEIlKg2y3EEETrBwi/9HllaPhLYSEfrpIgIURfmDJxEmfOPJ1DDzqYSeMnoHVP75Vyl1QKIbZ/EiKE6Ccp36BKpUyZcZ+iZsoVXH/zD7l5CwJAl85slktmfYeVq1dxwTnnsa6hgTv/cs9mPNNy+LERynXIW40NDMmEIo/mhX8nWLI8ucVjeScfHtrCOaMa0MqSDxWJ2KIo7v/gJw35gsaN4YurxnJi2MpJpnWjASKKFH5s8W3MnQ2LOKNuAsu9RFnHKsTOasyo0VzxjUs58tDDaWhsZPYjD3Hrb3/VpyWVQojtn4QIIfpJRcKgcuBkJlA1/Tpuv+eurQoQvf34Fz9j1IiRfOvCi3n2hX++6z/ou+5tGD5OU8AnLhiSXkwBTZiz/OEP1ds0lg29p6qTSyasRqticEp4llAp3MgWe0srhetbLl46ijnZCubYDHUq5n22fb0AEZYChLUQBYphccRdaxfy0SETWZYob+gRYmdz2skf4dKvfZ3mlma+0k8llUKIHYPsEyFEP6nwDE4Bqvf+EeuaWrjy+mvKctyrbriWltYWrvjGpe/62KNPgQCPbMHDOi6B8sgGHi+9lGLlivJ1PxqfKnDLXstJpAyB6lkD4rmW2IOY4iLq69YM5x9tNcU7leILdixPmYq3zUBYC3FQbIFrLHhZwx+XLmJ0UNjY6YUQm+GLZ3+Wqy+7nL/Pvp8TTzuFv82+f6MBoreuksoTPnoyf599P1dfdjlfPPuz/TRiIcRgIiFCiH6S9gxeclfSY2bw/R/+cLPWQGyOjs5Orv3RjRx56OFMnjhpk48bMgrGTC8GCKNdIu2RzXtExuNPv0uXZSwAFU7Er/dZQoUToxW4CUuhV5BwHbA+/HJdPb9bV7/+k5Xis3osLzspoqgYGroChFsKENk8EEMqMvzirUWMzUuQEGJLnXbyR7jgnPO4/uYfcsms72zx36OuksobbvkRF5xzHh/98Kl9NFIhxGAlIUKIflLpxmSmfZbm5gZmP/xgWY/9wCMP0dDYyFkzT9/kYw4/xSMfuMTKJdA+nXmfWLu8+EKChjXl+VPgKsNvDlpCZdJgSyvIlQI/YcjrniDxt6Yably18d2ordZ83J/AUuUXW74WegJEZ57iZnQW8gFUhjE/fWshE3L5soxfiJ3BmFGjufRrXy9bSeXt99zFty68mDGjRpdphEKI7YGECCH6SUbFqFHHct9DD79rycCWCsKQ2Y88xCEHHrTR+xNpmPieBLHyiFyfbMEjxKVgfe79bbn+DBh++t5lTK0I8D1L6Bb3ggBAKRIJS14r5rRl+NbCke94pFBrTqmcxKLYxzU9MxCqV4BQFiILOjLcMG8RY7LSflKIzXHFNy6luaV5QEoqhRA7DgkRQvST+nSaRP00Xnn9v31y/FfnvsbkCRNJp96+z8O+M9KohIdxXXIFl8i6GM/nhac0LY1qI0fbct98z2r2ru25kPdcSusfeo4/N0jyhTfGAu9+zoLWnF4/kRWOSzavwEC8QYDoOptnDNe8tZhxMiMhxDuaMnESRx56OD/48U39XlIphNixSIgQop+MGTEWpTXzFy7ok+O/tWA+WmvGjx233u1KwS5HZLCuTzbwCI2L9TzaOx0evb08MyJn79rARye24qYMeTZY/+BZQhSLcgk+/dJ47Bb82WlzXE4fOpF2rYktFDYSICIgAJLGcMVbixjf+fYZiXQqxfRpu7D3HnsyfdouGw1aQuwMzpx5Gg2NA1NSKYTYsUiLVyH6SdotbpCWy/fNu+X5QnGBse+vvxHb1EMzpIckyYUGZSCRcMgGhrnPhLQ2bvt5jxnbyhenrwOK+z8kUsX9H5LGAArHUSwruPzPv8cT2C1/32Kd5/Ox8ZP4zZsLqbDx2wJEWPo8AHRsuOytRVw+bSL+7rvLxllip6ONYWQQMimbY3yuQF0QMCQI8KMYP4o5cp/9+fsj/V9SKYTY8UiIEKKf+IXipW8q2Td7GyQTxc3XgiBY7/bpM2rJhi6OifETmnxoMPmQp+/a9jUEew3JMuvQVcRGocKe/R8SSVsMErGlJXQ4+/nxtEZb/+dmtefzhckT+PH8ReiouPX1hgGi61X748fzfzfezIgZM2TjLLHDcYxhgg3YLcgzLSwwPB8wKh+QKBhqchGxsVhrCSi2Ug6BAsXfl0JFBdXTpvHKn/7QJ2N7de5rnDnzNNKpFNmcrFESYkcnIUKIfhIuW4g1himTJvPyf18t+/GnTp6CMYYly5Z23zZ0WorMyAxBFJFIaPKRRcUhC54P6Ww223S+UZkCP37/MhKOBQdiBSZQuJQ2l0tYGjodPvf8ONYU/Hc52rtblEpy4cRxfH/+Eqy1dL2P2jtA1J19NpNvvJGG1hbZOEtslxLETHICppNjog4ZEwWMsiE1hZihcYQbWBKxJQwVXmjJhgoTWAoxGFMMDAHFWuWYnpplDaQnT+63ksq5897sk3MIIQYPCRFC9BO/vZ1g+Tz22m0P7v7rvWU//p7Td2fB4kXrvQM45fhhFCJNIuFRiCwqjtDW5bnbW7fpXBkv4tYPLMVzbPdtjgtGWcKCwsNSMIqvvjiG+R3lm3l5vSLDpZPGcenCpTjWUqBnNmLEJZcw+coruf2eu7jy+ms2a9Fo18ZZjz75ON88/yKuvuxyhtTXc8s2tr0UYlPSOmZCssAeqQKj/QITVcBQJ2JoEFGtDYmCwQWiHHgWwgh8awlQ+La46zuALS090sWeA3RtxaJLv5K9w0PXR1WarezvkkohxI5JQoQQ/SQdGvS/HuIDR5/BrB98r6w1yb7nMePoY7nvwdndtyXrPGp3rcG4kI8tKgpJ+D6vP9JEoWPrZyEcZfjlSUsZVRGBLZUtqeKVi3ZAJQ3ZnObSF0bxSlP5NrHr8nJVBddNGMOXFi/H2OJ5684+m8lXXsn1N/9wq/red22ctXL1Ki445zzWNTRw51/uKffQxU6g0o+ZXJVnalXAqGTAxGRArRsxyolIq5iqyGCtRRdKYSBbmjWIwbEQKcCCVQqs7WlktsFH1f2x9LtHcebB2fjDi+cqXeT3d0mlEGLHJCFCiH6SKcSYO35C7SnnMuOY4/jb7PvLduzjjz6WIfX1/PGu27tvm3D8aKznUzCgohDP8+nIxbx677ptOJPl6uNWMrmmdJHQvf5BkSyVMVmluOqVETy6smobzvPOnqupIjlmJJ9cthI1YQKTb7yxbBtnjRoxkm9deDHPvvBPWSMhNmCpSUVMGlpgcl3IqIqAcVUhNV7E6FSEj6HWiQlDhR9aohi8AhhjcQLAWmykUEp1X/B3lRwZpXCsLW3S2BMe7IbhoevLUnhwVHE2Tm94/0ZGn50/v99LKoUQOy4JEUL0k1TBYl+fS/jMg1z6lQtY17CO1rY2lixbuk2LECsyGS489ys8MecpFpS6DClPM/zA4QQ4qCDC8zwCYPHjKwm2YRbioiPWcPSUdqIIbKBwVc/6h3yg8I3lJ68O4e8La7b6HJvr8SG1OMbw3VtuoaG1pawbZx128CFc8Y1L+dS5XyjLMcX2wlJfHTFlVIFxw0JG1QSMqQup9WNGVIYksVQlYgo5RQpLPq9IKUOhoEgaSxAWa4u6ZwdKtUVagUWhVHEDRgfb/bFrxqGrMNB2z0QUb1GqeIPqTgddtxe/dN4WLorP763rJtPZSdu8/i2pFELsuCRECNEPpkycxOSTv4g+5P24E6cxRGv+eOuvgW1vN3rJVy+kprqGy66e1X3bqPePwSRTBIUQz3WLnVpaC7z199Vb/RrOeE8jp+3ZDIBbWv8QFBR+V5DwLb99tZZfvDp0q8+xpZYc+F6Gn3ACX7nkorJvnHXjVdcweeKk7mAmtn9KGeqHGCZNKDBieMSE4QWG1UWMqAwZUh2RcQxp3xB0KhKupdCpSDmGQqciqSyFvCodB7ClkGCLZXwYcLTt+YhCK4WhGCJiiv/gGoozED1hoddH6BUSusJD19c9gQR6lS0pQJWCgup++vqvu3gKNND84IOceOaZ/VJSKYTYsUmIEKIPjRk1miu+cSlHHno4TY0N3PHIw7zy+z+Urd3olz79OU4/dSYXX37Zeo8fctg4CgWF67igNQQhK+c0EmbjrXodR01p48tHrSUfaFKqOJOhHSBZvLBKKMsDi6q46YURW3X8rXXmzNOLbVz7cOOsK669uqzHFn1Haagbbhk9zlI/1DJ6TERNnWHU8AKVlYZhtXkcB/wwj6PBy8Z42hLnIOFYgs7iFfom5+q6LvRLCxB018fu0qJieFC6FB4AY3sWPwOYrtBQ+tpucEzVXc7U/Yji3arnYb1LnVRp/YTFknM1oVWscRyySrPGc2lzXFb5Lg2ex+qER/Lhf3Dneef1S0mlEGLHJiFCiD5y2skf4dKvfZ3mluaytxutyGS45KsXcvqpM/nBj29abxFw1XtGQkWaWMWgXaJCBAXL4vuXbdXr2HNUllknrsLVCjdpyRU0SQyK4kWUlzI8vbCCbzw2cquOvy0OPehgZj/ykGyctZPQLlSPcBgy2qVmqGLISE1FNQwdYUinLUPqI6yJqfAjjLGk3RCsJaVL4bn0tn9sNI42REbhaYsp3d79Jn7XRXrv1ka214W8tsXw4BQ/OtpibTE8xLZYYtS11iFWxbbHby9XKpYx9SyQ7vrYFRqKO713aIdAaVrQdLoO65RLo3ZYqX3WpFwWuz7LlUeL6/Yc5J0sX8YTc57ia1/6Mo8++XhZZvA2VlIphNjxSYgQog988ezPcsE555W93ajveRx/9LFceO5XqKmu4eLLL3tbF6HaIyYS4WC1RxREODisfXoNcX7LZyGGVQZ8f+ZKnF6tXJMJSyHQ+MailWVuQ4ovzx5DTzPJ/pFJp5k0fgK3/vZXfXJ82Tir/zm+omJUkoqhPpXDPKqHe2RqFNVDHVJpS029wgQR6aQpfYyJw5h0AkxkUJridATFgGttsSwoihWuY4ljheNYYrP+jMOGFUAbXtArB4hAdZUrORbC0gyDVaWZhuIah7hrrUN3EVHpHKXHZo2mM1I0FBzCSLE279IROKwKPBoDh2WRz6rQY6nxCLuLligGm0Tp823soHrZ1bO4/44/883zL+KSWd/ZtoOx8ZJKIcSOT0KEEGV22skf4YJzzitbu9FkIsHSFcvZc/ruzCiVDGyq5MkbXY03bgiRo4nDCAdNFBpW3L/l7w5mEhG3fmIZQyqL7+oWy5aK9yV8SxDBykafz9wzDtvPAQJg3JixaNk4a7uiEg7pURkS9WkywxMk61Nk6hxSdT6pCkWq2kWHBbwEqCAgmQAbhiSSFgoRpVXLpYOV1ieUVhYr3bVeQXWHhzhWuK7FlBYixKVremM3Ubakuw7dtTCaXmscwHEtBMXuSl3lSoFRBJGmtcMhHyoa2106Cg5rOxyacy6r213W5DxWZF3WFjzMAPyubGj5yhXM+sH3ufqyy1mxauU2dTXbVEmlEGLHJyFCiDIaM2o0l37t6+VrNzpyJJ//5KdRSrFg8SLue3A2f7zr9k2WDFQfvSvG9YmDCAeF9RM0PLAQG25ZRyalDNd9bAWjqotbuWmtUClLPqtJli6omvMun7prPPnIeadD9ZmuDa1k46zBQ6V9vBHVOLUZksMzuNUpUkOTOJUJ0rUuTtLFtwW0o3BNgONpnKiA6yt0aW+BrtKiruXAXe/o2w3rfnqFBmwxRBhTvPDvCQ9d5UulY5TCg91ws4Wu8KAt1kIh1uTyiuY2TaFT09ju0NHqsLbNo7lVs7LVp6HNZWmTT0eg2XhD1cHtjnvvZkh9PReccx6jR47a7BnTLu9UUimE2DlIiBCijK74xqU0tzSXr93o9ddy2EGHsnDxQv73nM+942NVRYLE7uMphOAYDb5L0JKj6bH5W3hWy/c+top9JuV69n9QxYs1P23I5TRBoPjs7eNoKwzcn5CuDa1k46z+YytSqKG1qNoKnCFV6MoU3tAKdEWCRH0KpTW+Z8CC74QowCvV/ShbDGW2NCtgTKlLUfeFPRt83KC1aVdo6Lrgd3rNOBhwSsfUGmJT6oTUNfNgFNmsor3ZwUaa1kaXMOfTtM4h26ZYu9aludVh1RqPhhaXfDAwwbi/3fLLW2lobOTSr32dww4+hGt/dOMm12512ZySSiHEzkFChBBlMmXiJI489PA+aDd6w2a1G02/bw8CPJwoAt/HRIa2JxdiC1u2FuK8E9Zx1K7tQHH/h0JY3P+h2EpSEbvwxdvGsqJ1YN+hX7JsKUY2ziobC8QVldjaWmxdNbauGlWZRtVXo9IJdH0l2hrchELFEZ4PKja4nilWGbldi5cNKLCxLV7oG4vSCmtUMTxYelf6U9p0fIPZAdtrlqBYU9RdrlTqfGQi6MwaCllL2GnJdxryrZBtM3Q2a9pboLXRoXkdtDRBf6/Z2V7cce/dPPP8c1zxjUu58apraLjg68x+5CFenfsaby2YT75QIJlIMHXylM0qqRRC7DwkRAhRJgPabtTR6L2nEIUWfI84tqi2HG1PbFkt/6kHN3P6kU0EOYVfKlvyPUsYgRMX39H92p2jeXNNaltf1jbL5nIsXLJYNs7aTFYponQ1NlNNXFmLqagmrqrCVFRjK9PE1dVoL0InHDQBOuWgTYibcLBRiHY0tvTWvi1d2K/XvahUgmSNQTmlVc2oXjMOpfs3WJfQ1eLUooiDmKA1IohC8i0BqlAg2xgR5wM6GyLCjojWNSG5lph850Y2ROgmgWFLLF+5gk+d+wWmTJzEmTNP55ADD+LMmaehdc/30RizWSWVQoidh4QIIcpkINuNOvvvgk0kMK4mMBYnjsjNmQ9bsBbiiN3bOf/Da3Ec0BlDvrNn/YPnQsEqZv1lBC8urtjm11Quc557lg8cN0M2zgJiFDZZjfErMZlajJ8hrqjBJCswlVWYZAY8BY4LrsG6LmgDngcqLL7jX/px6Z4V6LpOL9UQFRfQd++AULz9bTMPxW5G1hSDQ5wNMW0RQVsWgoCoNQu5gLC1QNxRoNCYI2wrkG8MsPE7BQPR1+YvWtj9RkU6lWL82HH4vk8QBCxZtnSHCdRCiPKQECFEGQx0u1F9wG4Y7WFi0CbE5CNyT87d7ONPGZ3n4jPWdHehUUqRqCgFCVXscf/DB4fx4GvV5XpJZXHbXbfziTPO2ik2zjI4GK8S42QwiSqMk8akqrFumjhdjXUTWN8triTwnWI5kKeKswauLV3wd00DdB20u5aopNcuZoDtXoDQtUWzwsYGsnlMvhObzWNzWejME3RmsW1ZbEcO09JJ3J7HtOXe3j9VbBeyuZx0JRNCvCMJEUKUwUC2G7VTx2KGDiGwoKMQx/UIH/93cXXpZhhaHXDTOcupqYwpFHr2fwBFImPJZRW3P1XLXc/X9sEr2zbzFy3cYTbOMrgYlcaoNNapxOg01q3AuCmMV4l1PKznopTFel4xEPhO8RrdKf0pt6W1BF3TAcb2KjWi1wKE9a/sVRigo050rgOHAirbjhvlUe1tOIU8tLSjcllobiMOih27tm7vcyGEEDsKCRFClMFAths1B+9DaF10EKJdj7i1k/i51zfruL5nuO6cFdRWFi8J/YQlCsEJVfesxH0vV/OTh4eV6ZWU3/aycZYxHpYExqaxKokhhdVpjEphnQxWueC4xUkAxyl+dF3AgPa6L/yt6VmA3J0ZSiVGqhQelLEQ59GFPJgC2uRQcQEV5HDCHAQd6EIWnSt9jMKyvlYhhBA7PgkRQpTBQLUbjYfWEY8fjwpjrHYxVqOe+A9qM2YhlDLc+NXlTBpfKO7/4BYvUl0PjLKEBcVzb2a49p7h5X9BZTRYNs4yxsMaD2OSgI8xaSw+hhSQxCgXpTRWK7C6WBrU3afIeVvZj7JdN5VKi6xBx3mUyaPiEBXnUIToOFsMCnEOFWXRYenjVn8XhBBCiHcnIUKIMhiodqPhAftjAnAcjXUcVEMT7guvbdYxL//savaekqNYtmTIdWpSpSChXcWLC1Jc9JtRbA8bafXHxlnGOFijsSSwRoNNY62DMRkwLsb6pd2SHUBhlS5uhKYUVjk9+x10saCIUBSKMwgE6DgGU0DpCGWyqHyINlmUDdBW9qsQQggxeEiIEKIMBqLdqEkmCSZMQcca42hUPiIx5yWUffeVrJ/+SAOH7d9BHIOjARTJ0vqHlGOZv8Lngp+Mwdrt5/3scmycddF3vs2df/4rxibAusVAYL1eHwE8AGzXR+Oi0KjSOhKtAlAGqyO0ikGFKB2DCopfE6BVgKWAQ2m6oWuBwYYfhRBCiEFKQoQQZdLf7Ubze+xHTAITO6hshNvZgX7p3WchPvS+Fv7nQ00oiusfbAhuqaommbYsWObzpR+OJYy3nwDRZWs3znr86TlcOutali1fBSSLLU6tWwoNDhCDAq0NqAKKGGstyonAWrSOsMRoHb19xkEIIYTYAUmIEKJM+rPdqFGK/JQ9MZGPiiK0C86zL6LfZRZin907+dzH1qHoWf8QawgKCt+xNLa6fPmHY2jLbr9/GjZ746xFi/jb7Af44513MX/hApTSKG1LnVBtaWbBoLe/LCWEEEL0ue33SkGIQaY/240WJu1BnKhG5QzWAdvaSeJd1mJMGFvguxesIp0yZLOKdGn9g+OASRkaGlzOu34MTa3eNo97MOi9cVYqWdw4K5HY+MZZxQ6pUkMkhBBCbC55j02IMrrs6lnU1tTyzfMvKsvxNtVuND95X1QhQkUGazxSLzzzjsufKysjvveNFWRSBlD4acjGPc8IQoeLbh7NklWJsox7sMnlc7zx1pu8/N9XmTvvTdl5VwghhNhGEiKEKKOudqOnnzqTc87+7DYdq6vd6Hev/d567UaDIWMw6TpUIcYajbt2LckFm14L4XuG71+5mvQQCHoFBz8FWaMJI8W3bx7Jm4tS2zReIYQQQuw8pJxJiDLr63aj+XHvgSACz4VcTOq/z77DLIThim+vZvzYYnvQQGlswZBwSqVMPlz1k+E885+KLX+hQgghhNhpSYgQog+Uo93oxZdf9rYAESWriGrGgdEQGNzORhLL5m7ymJ8/t5WJU3pq/bWriLTGZC1J13Drn+p5+OnqbX/BQgghhNipSIgQoo9sbbvRJ+Y8xWVXz9rojsmF0XtjYw2FGKUMqTf+uclZiNPObOeYY3OAQ0ceMm6IUqC0wmTgj3fXccff6vr0eyCEEEKIHZOECCH60Ga3G128iPsenM0f77p9vS5MvcXaI6ibBmExQOhCK4m1b230sQcfkefkUzu7v3aSDp0FRdoJ0AoeebyKX/5xSHlfrBBCCCF2GhIihOgHvduNplPFdqO+v/F2o5sSDJmONQ4qjMBxSC98bqOPm75HyGfP7STSLjaISPgGACehyQY+r7/scsMP68v34oQQQgix05EQIUQ/y+ZyzJ335hY9xwCF2umoIAJXoToa8ZsWv+1xw0bFfPWSdjwPQGGUS64QkUoUg8RbC5JcMasOacwmhBBCiG0hIUKI7UBUMR6rEmAMRC7p5c+/7TGZSsMF3ylgHBdLiAKUUuC5ZPMxTesU372sDmslQAghhBBi20iIEGI7UKiaDrFFWdD5Vfjty9e73/MMF87KUzfUAJps4JHyQrQCUDQ0e1x2cTWFggQIIYQQQmw7CRFCDHKhV0/s1aFiBXFIcu2/N3iE5ZMXxgwd0XOL9jS50CPpRHR2Kq68tIqOdqdfxy2EEEKIHZeECCEGuTCzS3EWIg7RYSN+btV695/xecOe+0FsXfKFiGRp/YP2NM2tHjdckaBxnQQIIYQQQpSP1DYIMYjFKknojUYFMTY2JFteXu/+Iz4IBx9TDA3d6x9yxcAQBoqbv59myUK/38cthBBCiB2bzEQIMYiFyakQGdAWt9CEV1jTfd9ehyhO/LgmG1Bc/6ABFDrh0N6p+OMtDm/NlRkIIYQQQpSfzEQIMUgZHEI9BhXHECuSHf/tvm/8rorTv6RRGpTnkI084rh4n7WKO3/t869nvAEauRBCCCF2dDITIcQgFTrjsMYFBW6wGjduAKB2OJx+QYLIRLhYALTrkIsVCRPy0D2KZx+R9weEEEII0XfkSkOIQSrU41AGiGISwesApCvgfy9LkqnW4Hvk8j2/wtrRPPaAyz/ukBImIYQQQvQtCRFCDEKRHYI1KWwc44arcU0z2oGZF2aoquv6tVWohNe9kPqVZy1/+/XAjVkIIYQQOw8JEUIMQgHjIY7RcYQfzwPgIxdkGLOLRyF2iaOex+qky3//pbntBjNAoxVCCCHEzkZChBCDTGwyxHE1Ko5xzFpcWnn//0szdd/iQmntagLrEoXFx69cYLjtByHWDuCghRBCCLFTkRAhxCATxmNQNgZr8e189pmRZu8TKt62/iHSLquWWH7z3fx6MxNCCCGEEH1NQoQQg4gxHnFUB8bg2nXsenDIkR+vRKFQvkc279A14dDeBL+/MkchO6BDFkIIIcROSFq8CjGIROFwQKGMZfS0JRzxqXqMjbvTvvZdsnlQYcRtV3bQ2TKAgxVCCCHETktmIoQYJIyBKByGMoba4av50MWVJDIOoXUJw57HxbHDbVd10rRSFlILIYQQYmDITIQQg0Qc1YPReOmAky4qkKostm5VWhNbFxNEONryt5taWLtIFkEIIYQQYuDITIQQg0QUDsVxQz707U6qx/vkCrp7/QNKE2uX2T9tY8krwUAOUwghhBBCQoQQg0EcVYB1OOarhhG7lMqUfJdcwcGUksSc21qZ90x+4AYphBBCCFEi5UxCDAJxVMX+H9eMPgCi0OD6xduV71AIFa8/0MSrszsGdpBCCCGEECUyEyHEADPGZZdjK9nrQy6OExNrj6jQc/+bT3fwz9tbB26AQgghhBAbkJkIIQbYsN2GsudpGZQKAYtSCuN6BPmQNXOzPPOrdQM9RCGEEEKI9chMhBADqGpcioPOHY2TcsgFFtu9lFqxekHEwzeuGtDxCSGEEEJsjIQIIQZIosbjoC9NwUsCKkb5DrnQxRhLy/ICj1+3BGQrCCGEEEIMQhIihBgATlJz4Nd2xampIChYlCqmBeU6NKwyPPy9xcThuxxECCGEEGKASIgQor8pOOAru1IxIo1SYD2PoFAsYyq0Rjx13SIKHTIFIYQQQojBS0KEEP1s909NIz2+EtOVE5TB+gk6mg1PX7eAfJNMQQghhBBicJMQIUQ/mvKRCYw8aCg4LkHkYIxBKYgDw/M3L6J1mWwmJ4QQQojBT1q8CtFPhh8ygtHvG1X6SqFcTWgMphDz8i8W0LJANpMTQgghxPZBZiKE6Ac1u9Ux5axdMF6CIN/VxtWA1rzyxyWs+XfzgI5PCCGEEGJLSIgQoo8lR2aY/pnd0W7x1816iWJHJmDBvUtZPUc2kxNCCCHE9kVChBB9yKv22fXcfYk8DxOXVlIrwPNZ8MAqFt+/fEDHJ4QQQgixNSRECNFHtK/Z9cv749ckUdohMA4mLAaJtc+vZtHdCwd4hEIIIYQQW0cWVgvRR8Z/9r24tZnur5V2CK2i/ZV1vPnruQM4MiGEEEKIbSMzEUL0gbH/szeVuw4h9nwKQc/t7YvbmfvTV8Fu+rlCCCGEEIOdzEQIUWZ1x06lZr/R3V9b1ydfCLHNHbz5o39BLAlCCCGEENs3mYkQooyqDhjH0A/uTmBd4sh03x60h7x+/YuYfDyAoxNCCCGEKA+ZiRCiTBKThzDijPcUv9CayPoQhhCELPjhP4k7gnd8vhBCCCHE9kJmIoQoA294JSPOPoQoUj03KkUQKBbc/DxhQ3bgBieEEEIIUWYSIoTYRroywcgvHIGT9sHzCAPAWmxkWPHL58kvbR3oIQohhBBClJWUMwmxLTzNkLOPQFcke25zXYJCSMMd/yY7T3ajFkIIIcSOR2YihNgGQz51BN64IYTKJQ57FlI33Psq7S/KbtRCCCGE2DHJTIQQW6ny1PeSmDay+IXSRDqBLRRof3Ie7c/IbtRCCCGE2HHJTIQQWyH9vt1JHrwrYWjBlvZ9UND63BKa7/vvwA5OCCGEEKKPSYgQYgv575lA5sR9AbCORxgqMJbcq8tp/fO/Bnh0QgghhBB9T0KEEFvAmTCM5MzDMGHPpnHWcemct46m3z49gCMTQgghhOg/EiKE2Ex6WDWZ/z0G5blEjk8cFINEtLKJll8/DsYO7ACFEEIIIfqJLKwWYnOkEyTOOgaV9Ltvil2feFUTbT97GHrNTAghhBBC7OhkJkKId+M6JD91AmpYLVEENi7OONi2HG2/eAibLQzwAIUQQggh+peECCHehXfa+9GjhwDF9Q+R0ZiOAh2/eADblhvg0QkhhBBC9D8JEUK8A33SYdjdJhMHPRvJ2djS8euHMWtaBm5gQgghhBADSEKEEJty2N7og/YAIHZ84oLBxobCnx7FLl83wIMTQgghhBg4EiKE2Ag7fRL2/Qdje3Vcih2f/N1PY+YuHcCRCSGEEEIMPAkRQmzAjh2BnXkc1nEJYwcTF0uZ4geew740b4BHJ4QQQggx8CRECNGLqakknnkCuKXux1oT4RI99TL26f8M6NiEEEIIIQYLCRFClJhkgujjp2KqqjBBr30f/jMPHnh24AYmhBBCCDHIyGZzQgBGKaIzPgT1NcWvXR8bhDhLl6H+/PDADk4IIYQQYpCRmQghgOCUDxCOGIXtvfP0irXwx/tQAzcsIYQQQohBSWYixE6vcMxRRLtOBSCyCieM0M0tOLf9BW3MuzxbCCGEEGLnIzMRYqdW2GtvCnvsBaVOrlYpTFMnzu/vQQfhwA5OCCGEEGKQkhAhdlrB5Cnk3n80RvnEOQMWVGeO5J/uwenIDvTwhBBCCCEGLQkRYqcU1Q0le+wJoIq/AlZ5mNY8yTv+jG5pHeDRCSGEEEIMbv+/vfuOj6LO/zj+2ppNJZBQQu9delGkd7ELgooN9Sf2cio2zooNe72zop4VsaKc0ovSqyBNei8hCenZMvP7Y5M1uQTMJoFNeT8fDx+XnZmd+STsJfOeb1OIkCrHGxVD6rmj8ZjhmHlTufq8hH//I7aDh0NbnIiIiEgFoIHVUqX47E5SzxuDERGFBfB6HdgNNxGzZ+DYvzfU5YmIiIhUCGqJkCrDsFhIHzwKwxlD3khqCxbC580l7M+toS1OREREpAJRS4RUGen9LsRTu6H/RbYPwkzCVy3Gtfn30BYmIiIiUsGoJUKqhIwzeuOu2zzfFhuutauJXPVbyGoSERERqagUIqTSy27eiax2Z2EaFiwe/9oPzt2biVo+J8SViYiIiFRMChFSqblrNiKj8yAALIBpWHHs2U7Ugu9DW5iIiIhIBaYQIZWWNyaetB4XYLoNMPwDqe1Jh4he8A1W0wxxdSIiIiIVlwZWS6XkdUWR2mskOJxYAHJ8WHOOEzPvK6yGL9TliYiIiFRoChFS6Rg2B+ndLsS0hgW2WbMziFnwJVZPdggrExEREakcFCKkUjEsFtK6XoAvuiaYYHG7MS0G0Yu/xpadEeryRERERCoFhQipVDJbDcRbo/5fG7wG0cumYU87FrqiRERERCoZDayWSiOzcU9yEtpCjg+LzwemQdTqH3EePxzq0kREREQqFbVESKWQXas1WU165L6yYLoNIjfPwZm4O6R1iYiIiFRGaomQCs9drR6ZTfthcXsC2yK3/Ybr0OYQViUiIiJSeaklQio0b3gcGa2Gg9XmH0id4ybs8Hpc+9aGujQRERGRSkshQioswx5OevOhmNa/PsZhh7YQuWNxCKsSERERqfwUIqRCMqwO0lqOwHRGg8fEYvdhT91L+I75oS5NREREpNJTiJAKxwAyGg3AFx6HBbAAtqT9RG77RYN8RERERE4D3XNJhZNVrzfeqIZY3F5ME6xZSURt/wWr6Qt1aSIiIiJVgloipELJiu+Iu0br3FdWbBlJRG//CavhOen7RERERKTsqCVCKgx3dBOya3QCn7/FweLJJGrHz1i9WaEtTERERKSKUUuEVAieiAQyE/pgsVgwfQYWXw5Ru2di86SHujQRERGRKkctEVLueR0xZNbqjZn7cbWYBpF7ZmPPTgxxZSIiIiJVk0KElGuG1UVmncGY1nAsXi+YBhEHFuLIOhLq0kRERESqLIUIKbcMLGTU7o/hiMrdYiX8wG8403eHtC4RERGRqk4hQsolE8iK64vXVgO8/pmXXMfWEJa+PbSFiYiIiIhChJRPWbHd8YTXwwJgWHAmb8B1fH2oyxIRERERFCKkHMoOb4U7rAkW0wTAmbmL8OTVIa5KRERERPJoilcpV9xhDcmJ7oTFBDwGdt9hXElL/C0SIiIiIlIuKERIueG11SArqmvgtc1zjIjkhVgxQ1iViIiIiPwvhQgpF3zWKLKizgbDhgUvFjKJSFmIFSPUpYmIiIjI/1CIkJAzcJAZdTaGNQwAizeLiNS5WE13iCsTERERkaIoREhIGVjIiuiFabjAYmDFS0TaQmxmTqhLExEREZETUIiQkMp29cRnrQ6AxefGlbUYm5Ee4qpERERE5GQUIiRksu1t8FrjA68jspZh9yWFsCIRERERKQ6FCAkJt60pHntzLAaYpheXZx1239FQlyUiIiIixaDF5uS081jiyba3Cbx2uTfg9O4NYUUiIiIiEgy1RMhp5aUa2bauWHw+TBs4vTtw+naFuiwRERERCYJChJw2PtNFtr0beQ1gDs9OXMam0BYlIiIiIkFTdyY5LQzTQbalG6ZhwzRN7MZhXMbGUJclIiIiIiWglgg55QzTQralMwYRYILNl0gYa7CEujARERERKRG1RMgpl2O0wTCjAbCRSri5BitmiKsSERERkZJSiJBTKsfXHJ9ZB9NnYjPTcJlrsFp8oS5LREREREpBIUJOGbcvAY/ZCACrxY3LXI3VkhPiqkRERESktDQmQk4Jry8Oj68FFryYVgOXZS1WqwKEiIiISGWglggpc15fJDm+NoAFMAizrMNmTQ91WSIiIiJSRhQipEwZRhg57rZg+udeCrNtxGFLDXFVIiIiIlKWFCKkzBiGjRxPOyAMDBOndRN227FQlyUiIiIiZUxjIqRMGAa4c1piEA6Aw74Th/1IiKsSERERkVNBIULKhMfTAsOoBnixO47gdOwPdUkiIiIicoooREipubPr4fPFAeCwJ+J07gxxRSIiIiJyKilESKl43fF4PXXB4sNqT8fh3B7qkkRERETkFFOIkBLzeqvhzmkMgNWahsOxGYsltDWJiIiIyKmnECElYvhceLJzV6O2ZuF0/YlVc32JiIiIVAkKERI0w3DgzmoO2LBYMnGG/4nV6gt1WSIiIiJymihESFAMw4I7qzEmDix4cUZsx2r1hLosERERETmNFCKk2EwTvDmNwAwD3DhcO7Fac0JdloiIiIicZurFLsXmyamL4YsCTJyuXdjsmaEuSURERERCQC0RUixedw18vkgs+LCH7cdmzwh1SSIiIiISIgoR8re8nhi83jgsFrA7D2B3pIa6JBEREREJIXVnkpMyfC58njhME+z2JOyO46EuSURERERCTCFCTsgwHHhzagEmdkcSduexUJckIiIiIuWAQoQUyTCseN01MbFitWXgUIAQERERkVwKEVKIYYDXHY9pWLBYM7E5joa6JBEREREpRxQipBCf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"/>
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
<h3 id="4.2-Argentina's-Pressure-Analysis">4.2 Argentina's Pressure Analysis<a class="anchor-link" href="#4.2-Argentina's-Pressure-Analysis">¶</a></h3><p>In this section we will try to understand at what positions argentine players dominated the most and at what level</p>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [15]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Filter pressure data</span>
<span class="n">mask_presure</span> <span class="o">=</span> <span class="p">(</span><span class="n">events</span><span class="p">[</span><span class="s1">'type'</span><span class="p">]</span> <span class="o">==</span> <span class="s1">'Pressure'</span><span class="p">)</span> <span class="o">&amp;</span> <span class="p">(</span><span class="n">events</span><span class="p">[</span><span class="s1">'team'</span><span class="p">]</span> <span class="o">==</span> <span class="s1">'Argentina'</span><span class="p">)</span>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [16]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Setup pitch</span>
<span class="n">pitch</span> <span class="o">=</span> <span class="n">Pitch</span><span class="p">(</span><span class="n">pitch_type</span><span class="o">=</span><span class="s1">'statsbomb'</span><span class="p">,</span> <span class="n">line_zorder</span><span class="o">=</span><span class="mi">2</span><span class="p">,</span>
              <span class="n">pitch_color</span><span class="o">=</span><span class="s1">'#22312b'</span><span class="p">,</span> <span class="n">line_color</span><span class="o">=</span><span class="s1">'#efefef'</span><span class="p">)</span>

<span class="c1"># Draw</span>
<span class="n">fig</span><span class="p">,</span> <span class="n">axs</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">draw</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">9</span><span class="p">,</span> <span class="mi">7</span><span class="p">))</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_facecolor</span><span class="p">(</span><span class="s1">'#22312b'</span><span class="p">)</span>
<span class="n">bin_statistic</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">bin_statistic</span><span class="p">(</span><span class="n">events</span><span class="p">[</span><span class="n">mask_presure</span><span class="p">]</span><span class="o">.</span><span class="n">x</span><span class="p">,</span> <span class="n">events</span><span class="p">[</span><span class="n">mask_presure</span><span class="p">]</span><span class="o">.</span><span class="n">y</span><span class="p">,</span> <span class="n">statistic</span><span class="o">=</span><span class="s1">'count'</span><span class="p">,</span> <span class="n">bins</span><span class="o">=</span><span class="p">(</span><span class="mi">25</span><span class="p">,</span> <span class="mi">25</span><span class="p">))</span>
<span class="n">bin_statistic</span><span class="p">[</span><span class="s1">'statistic'</span><span class="p">]</span> <span class="o">=</span> <span class="n">gaussian_filter</span><span class="p">(</span><span class="n">bin_statistic</span><span class="p">[</span><span class="s1">'statistic'</span><span class="p">],</span> <span class="mi">1</span><span class="p">)</span>
<span class="n">pcm</span> <span class="o">=</span> <span class="n">pitch</span><span class="o">.</span><span class="n">heatmap</span><span class="p">(</span><span class="n">bin_statistic</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="s1">'hot'</span><span class="p">,</span> <span class="n">edgecolors</span><span class="o">=</span><span class="s1">'#22312b'</span><span class="p">)</span>

<span class="c1"># Add the colorbar and format off-white</span>
<span class="n">cbar</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">colorbar</span><span class="p">(</span><span class="n">pcm</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">axs</span><span class="p">,</span> <span class="n">shrink</span><span class="o">=</span><span class="mf">0.6</span><span class="p">)</span>
<span class="n">cbar</span><span class="o">.</span><span class="n">outline</span><span class="o">.</span><span class="n">set_edgecolor</span><span class="p">(</span><span class="s1">'#efefef'</span><span class="p">)</span>
<span class="n">cbar</span><span class="o">.</span><span class="n">ax</span><span class="o">.</span><span class="n">yaxis</span><span class="o">.</span><span class="n">set_tick_params</span><span class="p">(</span><span class="n">color</span><span class="o">=</span><span class="s1">'#efefef'</span><span class="p">)</span>
<span class="n">ticks</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">setp</span><span class="p">(</span><span class="n">plt</span><span class="o">.</span><span class="n">getp</span><span class="p">(</span><span class="n">cbar</span><span class="o">.</span><span class="n">ax</span><span class="o">.</span><span class="n">axes</span><span class="p">,</span> <span class="s1">'yticklabels'</span><span class="p">),</span> <span class="n">color</span><span class="o">=</span><span class="s1">'#efefef'</span><span class="p">)</span>

<span class="c1"># Set the title</span>
<span class="n">axs_title</span> <span class="o">=</span> <span class="n">axs</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">'Pressure Applied by Argentina'</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">20</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'white'</span><span class="p">)</span>
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
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="5.-Conclusion">5. Conclusion<a class="anchor-link" href="#5.-Conclusion">¶</a></h2><p>Argentina's performance in the FIFA World Cup 2022 Final showcased their tactical discipline and cohesive play, particularly evident in their passing structure and defensive pressure.</p>
<p><strong>Passing Insights:</strong>
Argentina's passing network revealed a well-balanced approach, effectively utilizing both central and wide areas. The team prioritized ball retention and progressive play, with Lionel Messi orchestrating attacks through key passes. Their passing patterns created numerical superiority in crucial zones, allowing them to control the game's tempo and exploit spaces in France's defense.</p>
<p><strong>Defensive Pressure:</strong>
Argentina applied structured defensive pressure, particularly in the first half. Their pressing actions were concentrated in the midfield, aimed at disrupting France’s build-up play and limiting their access to dangerous areas. By maintaining compact defensive lines, Argentina forced turnovers and quickly transitioned into attack, a strategy that kept France under constant pressure.</p>
<p>This combination of controlled passing and well-coordinated pressing was instrumental in Argentina’s dominance for large parts of the match, ultimately contributing to their historic victory.</p>
</div>
</div>
</div>
</div>
</main>
</body>
</html>