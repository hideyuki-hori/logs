# 目的

04/12 

Design Systemの構成要素を確認して、エンジニアがどう動ける状況になればいいのかを調べる。
絶対飽きるので今日中に終わらせる。

# Figma

design toolはこれ一択。
過去のdesign toolが生まれては死んでいったので、Figmaに依存することが怖い。
toolが吐き出すschemaに規格がないか調べる。

今のところ w3c が Design Tokens Community Group を立ち上げてるので、そこを見るのが良さそう。

- https://www.w3.org/community/design-tokens/
- https://zenn.dev/sakito/articles/c96625b2d30540

tokenをDLしたあとにtransformする層で考えたい。

# Tokenをjsに変換するもの

以下ChatGPTの調査結果。

## Style Dictionary

Amazon製。デザイントークン（JSON）を多形式に変換できるツール。
TypeScript、CSS、SCSS、Android XML、iOS plist などへの変換に対応。
拡張性が高く、大規模なDesign Systemに適している。

- 入力形式：JSON（design tokens）
- 出力形式：TS, CSS, SCSS, etc.
- Figma Tokensとの連携：token-transformerと併用されることが多い
- OSS: https://github.com/amzn/style-dictionary

-> repoを見る限りあまり活発でないように見える。

---

## token-transformer

Figma Tokens でエクスポートされたJSONを Style Dictionary 形式に変換するCLI。
構造が特殊なFigma出力をプレーンなtoken構造に整理する目的で使う。

- 入力形式：Figma Tokens JSON
- 出力形式：Style Dictionary互換JSON
- 開発元：tokens-studio（旧Figma Tokens）
- OSS: https://github.com/tokens-studio/token-transformer

このrepoはなくなってる。

---

## Panda CSS

TypeScriptでDesign Tokenを定義できるCSS-in-JSライブラリ。
独自のプリセット形式で、`panda.config.ts` にtokenを記述。
Token→スタイル→コンポーネントの流れが明確。

- 入力形式：TSファイル（定数定義）
- 出力形式：型付きユーティリティ関数
- 特徴：型安全・preset化しやすい・WASM対応可能
- 公式: https://panda-css.com/

---

## Theo

Salesforce製。Style Dictionaryと似たtoken変換ツール。
現在はあまりメンテされておらず、Style Dictionaryに移行する例が多い。

- 入力形式：YAML / JSON
- 出力形式：SCSS, LESS, iOS, Android, etc.
- OSS: https://github.com/salesforce-ux/theo

---

## Tokens Studio (for Figma)

FigmaのDesign Token管理プラグイン。
JSON形式でのエクスポートに対応し、Style Dictionaryやtoken-transformerと連携可能。

- 入力/出力：Figma UI ↔ JSON
- 特徴：GUI管理可能・Figma内でTokenを扱える
- プラグイン: https://tokens.studio/

-> figmaに全ふりできるならこれでいいと思う。

---

# ここまで

ここまででfigma -> コード化というのは実現できる。
後はAIを使用した開発効率向上だが、これはdesign systemの本筋から外れる。
なのでMCPサーバの概要だけ抑えて、構成を考えたい。

# mcpサーバ

design systemで活きるmcpサーバの概要を調べる。
https://zenn.dev/ubie_dev/articles/f927aaff02d618

design systemというより、コーディング支援だったので、mcpサーバは一旦考えない。

# ubie

https://github.com/ubie-oss/design-tokens/blob/main/scripts/figma.js
figmaの内容を見て、そのままjsonに落としてる。

# 今後

design tokenにでてくるキーワード(colorsなど)をちゃんと理解するほうがいいとおもった。
そういう意味ではw3cを理解するのがはやそう。

