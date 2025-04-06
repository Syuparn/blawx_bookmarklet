# blawx_bookmarklet

Blawx開発を補助するブックマークレット
Bookmarklets to support Blawx development (unofficial)

# About / 概要

BlawxのブロックをXML形式でコピー、貼り付けできるブックマークレットです。以下の用途等にご活用ください。

- ブロックを別プロジェクトへコピー
    - 開いている画面のブロックを読み取るため、画面単位でのブロックコピーが可能
- AIへの入力として使用
    - LLMはブロックのスクリーンショットよりもXML形式のテキストの方が解釈しやすい

（英語で記載、以下同様）

# Disclaimer / おことわり

本ブックマークレットは非公式です。今後Blawx本体のアップデートにより動作しなくなる可能性があります。

# Setup / 準備

以下のJavaScriptコードをブックマーク（ブックマークレット）のURLとして登録してください。

## Copy Blawx Blocks to the Clipboard as XML Text / BlawxブロックをXML形式テキストにコピー

```js
javascript:setTimeout(()=>navigator.clipboard.writeText(Blockly.Xml.workspaceToDom(demoWorkspace).outerHTML),100)
```

## How to Create Bookmarklets / XML形式テキストからBlawxへ貼り付け

```js
javascript:Blockly.Xml.domToWorkspace(Blockly.utils.xml.textToDom(prompt('ブロックから取得したXMLを貼り付けてください')),demoWorkspace);
```

## How to Create Bookmarklets / ブックマークレットの作り方

TODO

# Usage / 使い方

TODO

# How it works / 動作原理

(developのところに記載する)
