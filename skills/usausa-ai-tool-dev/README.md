# usausa-ai-tool-dev スキル ― Windows / VS Code での使い方

書籍『黒猫先生の日めくり』のプロンプトを、**Claude の "Skill"**（SKILL.md形式）にまとめたものです。
Windows の VS Code（Claude Code 拡張）で使えます。

## このスキルでできること
「単一HTMLで動くAIツールを作りたい」「要件定義して」「テスト項目出して」「レビューして」と
声をかけると、要件→設計→実装→テスト→レビュー→品質の手順とプロンプトで伴走します。

## フォルダ構成
```
usausa-ai-tool-dev/
├─ SKILL.md                         ← スキル本体
├─ README.md                        ← このファイル
└─ references/
    ├─ prompt-library.md            ← 各工程のプロンプト（コピペ用）
    └─ single-html-checklist.md     ← 実装・出荷前チェック
```

---

## 導入手順（Windows + VS Code / Claude Code）

### 前提
- VS Code に Claude Code 拡張機能を入れていること
- Windows の場合、ユーザーフォルダは `C:\Users\あなたの名前` です

### 方法A：プロジェクトで使う（そのリポジトリだけで有効）
1. 使いたいプロジェクトフォルダを VS Code で開く
2. フォルダ直下に `.claude\skills\` を作る（エクスプローラーまたはターミナルで）
   - PowerShell なら：
     ```powershell
     mkdir .claude\skills
     ```
3. この `usausa-ai-tool-dev` フォルダごと `.claude\skills\` の中にコピー
   - 完成形：`プロジェクト\.claude\skills\usausa-ai-tool-dev\SKILL.md`
4. VS Code の Claude Code を開き直すと、スキルが読み込まれます

### 方法B：自分用にいつでも使う（全プロジェクトで有効）
1. ユーザーフォルダに `.claude\skills\` を作る
   ```powershell
   mkdir "$env:USERPROFILE\.claude\skills"
   ```
2. `usausa-ai-tool-dev` フォルダをその中にコピー
   - 完成形：`C:\Users\あなたの名前\.claude\skills\usausa-ai-tool-dev\SKILL.md`
3. Claude Code を開き直す

> どちらでも動きます。まずは方法Aで試すのがおすすめです。

---

## 使い方（例）
VS Code の Claude Code に、こう話しかけてください。

- 「推し活に使える単一HTMLのタイマーを作りたい。要件定義から手伝って」
- 「このHTMLをレビューして。安全性と保守性を見て」
- 「このツールのテスト項目を10個出して」

スキルが自動で手順とプロンプトを使い、一緒に進めてくれます。

## うまく動かないとき
- スキルが反応しない → Claude Code を一度閉じて開き直す／フォルダの場所（`.claude\skills\usausa-ai-tool-dev\SKILL.md`）を確認
- パスは Windows では `\`（円マーク/バックスラッシュ）で区切ります
- それでも迷ったら、Claude Code に「このフォルダのスキルを読み込んで」と伝えてください

## 注意
- このスキルは書籍購入者向けの学習用です。
- スキルは「嘘をつかない／存在しないものをでっち上げない」を最優先に作られています。

*面白きこともなき世を面白く。*
