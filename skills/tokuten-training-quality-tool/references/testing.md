# jsdom 回帰テストの観点とひな形

データとロジックを分離していれば、純粋関数はブラウザ無しでテストできます。

## 観点
| 種別 | 見るところ |
|---|---|
| 単体 | score() 等の純粋関数が、既知入力で期待出力を返すか |
| 結合 | 保存→読み込みで状態が復元されるか（localStorage） |
| 安全性 | 画面出力がエスケープされ、<img onerror> でJSが動かないか |
| 異常系 | 保存・通信が失敗しても初期値で動き続けるか |
| 回帰 | 直したあと、全テストを1番からやり直す |

## 最小ひな形（Node + jsdom）
```js
// test.js : node test.js で実行
const fs = require("fs");
const { JSDOM } = require("jsdom");
const html = fs.readFileSync("tool.html", "utf8");
const dom = new JSDOM(html, { runScripts: "dangerously", url: "http://localhost/" });
const W = dom.window;

let pass = 0, fail = 0;
function t(name, fn){ try{ if(fn()){pass++;console.log("OK  "+name);} else {fail++;console.log("NG  "+name);} }
  catch(e){ fail++; console.log("NG  "+name+" — "+e.message); } }

setTimeout(()=>{
  // 純粋関数は eval で関数スコープから呼ぶ（const/let や IIFE内でも拾える）
  t("満点で total と一致", ()=> W.eval("score(QUESTIONS.map(q=>q.answer)).correct === QUESTIONS.length"));
  t("エスケープが効く", ()=> typeof W.escapeHtml==="function" ? W.escapeHtml("<b>")==="&lt;b&gt;" : true);
  console.log(`\nPASS ${pass} / FAIL ${fail}`);
  process.exit(0);
}, 400);
```

## 使い方（Windows / VS Code）
```powershell
npm install jsdom --no-save
node test.js
```
全項目 PASS になるまで「完成」と言わないのが、うさうさ品質の約束です。
