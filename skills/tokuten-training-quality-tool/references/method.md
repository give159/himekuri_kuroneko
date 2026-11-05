# 設計の進め方（要件 → データ → ロジック → 画面）

## 1. 要件（最初に言葉にする）
- 誰が使う／何を学ぶ・測る／合格やゴールの条件は何か
- 1画面で完結するか／保存は必要か／オフライン前提か

## 2. データ層を先に作る
教材を「配列」で持つ。ロジックは入れない。例：
```js
const QUESTIONS = [
  { id:"q1", text:"…", choices:["A","B","C"], answer:1, why:"…" },
  // データを足すだけで増える。ロジックは触らない。
];
```

## 3. ロジックは純粋関数で
DOMを触らず、同じ入力なら同じ出力を返す。だからテストできる。
```js
function score(answers){            // answers: 選んだ番号の配列
  let correct=0;
  QUESTIONS.forEach((q,i)=>{ if(answers[i]===q.answer) correct++; });
  return { correct, total:QUESTIONS.length };  // DOMを触らない
}
```

## 4. 画面層でつなぐ
表示・入力・保存はここだけ。出力は必ずエスケープ。保存はlocalStorage＋try-catch。

## 5. 仕上げ
版を3箇所で一致・CHANGELOG・テスト全PASSで完成。
