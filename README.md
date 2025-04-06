# blawx_bookmarklet

Blawx開発を補助するブックマークレット

Bookmarklets to support Blawx development (unofficial)

# About / 概要

BlawxのコードブロックをXML形式でコピー、貼り付けできるブックマークレットです。以下の用途等にご活用ください。

- ブロックを別プロジェクトへコピー
    - 現在開いている画面のブロックのみコピーが可能
- XML形式のテキストをAIへのプロンプトに使用
    - LLMはブロックのスクリーンショットよりもXML形式のテキストの方が解釈しやすい

This is a list of bookmarkets which can copy and paste Blawx code blocks as XML format text. You can use them for developments below etc.

- Copy blocks to another project
    - able to copy blocks only shown in the current window
- Use XML text for AI prompt
    - it is easier for LLM to interpret XML text than block screenshot images

# Disclaimer / おことわり

本ブックマークレットは非公式です。今後Blawx本体のアップデートにより動作しなくなる可能性があります。

This bookmarklet is unofficial. It may not work in the future due to Blawx updates.

# Setup / 準備

以下のJavaScriptコードをブックマーク（ブックマークレット）のURLとして登録してください。

Please register these JavaScript snippets below as bookmarklet URLs.

## Copy Blawx Blocks to the Clipboard as XML Text / BlawxブロックをXML形式テキストにコピー

```js
javascript:setTimeout(()=>navigator.clipboard.writeText(Blockly.Xml.workspaceToDom(demoWorkspace).outerHTML),100)
```

## Paste XML text to Blawx blocks / XML形式テキストからBlawxへ貼り付け

```js
javascript:Blockly.Xml.domToWorkspace(Blockly.utils.xml.textToDom(prompt('ブロックから取得したXMLを貼り付けてください')),demoWorkspace);
```

## How to Create Bookmarklets / ブックマークレットの作り方

TODO

# Usage / 使い方

TODO

# How it works / 動作原理

(developのところに記載する)
