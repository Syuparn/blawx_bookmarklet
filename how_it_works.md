# How It Works

These bookmarklets uses several tricks and dirty hacks.

## Copy Blawx Blocks to the Clipboard as XML Text

```javascript
javascript:setTimeout(()=>navigator.clipboard.writeText(Blockly.Xml.workspaceToDom(demoWorkspace).outerHTML),100)
```

This oneliner can be beautified to below.

```javascript
const blawxXmlDom = Blockly.Xml.workspaceToDom(demoWorkspace);
const xmlText = blawxXmlDom.outerHTML;
setTimeout(() => navigator.clipboard.writeText(xmlText), 100);
```

- `demoWorkspace` is a global variable defined in Blawx, which is a workspace of Blawx blocks
- [`Blockly.Xml.workspaceToDom`](https://developers.google.com/blockly/reference/js/blockly.xml_namespace.workspacetodom_1_function?hl=en) encodes blocks as XML DOM.
- [`outerHTML`](https://developer.mozilla.org/en-US/docs/Web/API/Element/outerHTML) is a property of DOM interface which contains serialized string of the dom itself
- [`navigator.clipboard.writeText`](https://developer.mozilla.org/en-US/docs/Web/API/Clipboard/writeText) write the specifed text to the clipboard (just like `ctrl + c` copy)
- `setTimeout` is a trick to use clipboard API in bookmarklets
    - clipboard API only works when `document` is focused, but it is not focused when the bookmarklet is clicked
    - once bookmarklet is clicked, `document` is focused again
    - use `setTimeout` to evaluate `writeText` **after** the clicking so that it is executed after `document` is focused

## Paste XML text to Blawx blocks

```javascript
javascript:Blockly.Xml.domToWorkspace(Blockly.utils.xml.textToDom(prompt('ブロックから取得したXMLを貼り付けてください')),demoWorkspace);
```

This oneliner can be beautified to below.

```javascript
const message = 'ブロックから取得したXMLを貼り付けてください'; // paste XML received by blocks
const inputXmlText = prompt(message);
const blawxXmlDom = Blockly.utils.xml.textToDom(inputXmlText);
Blockly.Xml.domToWorkspace(blawxXmlDom,demoWorkspace);
```

- [`prompt`](https://developer.mozilla.org/en-US/docs/Web/API/Window/prompt) displays the popup to get user input
- [`Blockly.utils.xml.textToDom`](https://developers.google.com/blockly/reference/js/blockly.utils_namespace.xml_namespace.texttodom_1_function?hl=en) converts XML string to a DOM
- [`Blockly.Xml.domToWorkspace`](https://developers.google.com/blockly/reference/js/blockly.xml_namespace.domtoworkspace_1_function?hl=en) decodes XML DOM to blocks on the workspace
