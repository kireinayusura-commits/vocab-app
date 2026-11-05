# VOCAB アプリ CSVフォーマット（v43時点）

単語学習アプリ「VOCAB」に読み込むCSVの書き方です。教材の写真からCSVを作るときは、この形式に合わせてください。
実際に記入した見本：LEAP必携英単語 p.56–57（119 pass 〜 125 avoid）＝ `leap_sample_p56-57.csv`

---

## 1. 基本ルール

- 1行目は列名、2行目から **1行＝1単語**。
- 必須は **question（英語）** と **answer（意味）** の2列だけ。ほかの列は使うものだけでよく、順番も自由。
- 列名の大文字・小文字は区別しない。
- 文字コードは UTF-8（BOMあり・なしどちらでも可）。Excel（.xlsx、1枚目のシート）でも読める。
- セル内に改行・カンマ・`"` を含むときは、セル全体を `"` で囲む（`"` 自体は `""` と書く）。
- 古い形式のCSV（`vocab_leap.csv` など、note に頻出・関連語をまとめて書いたもの）もそのまま読める。

## 2. 推奨の列（この順で作ると見やすい）

```
id,book,section,theme,type,category,question,answer,pron,example,example_ja,example_answer,example2,example2_ja,example2_answer,example3,example3_ja,example3_answer,phrases,caution,origin,related,note
```

例文が4つ以上ある単語があるときは、`example4,example4_ja,example4_answer` … を `example20` まで足せる。

## 3. 列の一覧

### 基本

| 列名 | 内容 | 例 |
|---|---|---|
| id | 通し番号（アプリでは使わない。見出し番号を入れておくと管理しやすい） | 119 |
| book | 教材名（**読み込み時には使われない**。8章を参照） | LEAP 必携英単語 |
| section | セクション | Part 1 |
| theme | 小テーマ（列名「小テーマ」でも可） | 可能性・確実性 |
| type | word（単語）／idiom（熟語）／grammar（文法）／order（並べ替え）。空欄なら word | word |
| category | 品詞・分類（名詞・動詞・形容詞・副詞・熟語 など） | 形容詞 |
| question | 英語（**必須**） | likely |
| answer | 意味（**必須**）。書き方は4章 | 〔形〕①（to do）〜しそうだ、可能性が高い 〔副〕②おそらく |
| pron | 発音記号（列名「発音記号」「発音」「ipa」でも可） | [láikli] |
| tag | 分類タグ（任意） | 課題リスト |
| choice1〜choice3 | 4択の不正解の選択肢（任意。なければアプリが自動で作る） | |

### 例文

| 列名 | 内容 | 例 |
|---|---|---|
| example | 例文1。空所は `____` | ① Things {are} ______ {to} improve. |
| example_ja | 例文1の訳 | 事態はよくなりそうだ。 |
| example_answer | 例文1の空所に入る語（実際の形で。過去形・複数形・文頭の大文字もそのまま） | likely |
| example2〜example20 | 2つめ以降の例文 | ② He will very ______ stay home. |
| example2_ja など | その例文の訳 | おそらく、彼は家にいるだろう。 |
| example2_answer など | その例文の空所の答え | likely |

### 詳しい情報

| 列名 | 内容（別名） | 例 |
|---|---|---|
| phrases | 頻出表現（頻出／頻出表現） | be likely to do「〜しそうだ」（＝It is likely that S V.） |
| caution | 注意（注意） | avoid doing（×avoid to do） |
| origin | 成り立ち・語源（成り立ち／語源） | a-［＝away 離れて］＋-void［空っぽの］ |
| related | 関連語（関連語） | 名 likelihood「可能性」 |
| note | メモ（上のどれにも当てはまらない説明） | 「（危険なものや嫌なもの）を遠ざける」 |

## 4. 意味（answer）の書き方

- **品詞の印**：〔他〕〔自〕〔名〕〔形〕〔副〕〔動〕〔前〕〔接〕など。【他】や [他] でも可。
  印は **その意味から後ろ全部** に効く（次の印が出るまで同じ品詞）。
- **番号**：①②③…で意味を分ける。
- 例：`〔他〕①〜を通り過ぎる ②〜を抜く ③（試験）に受かる ④（(人) A）（人）に（Aを）渡す 〔自〕⑤（時が）過ぎる 〔名〕⑥通行証`
- 意味が1つなら番号は不要：`〔他〕〜を避ける`、`〔副〕おそらく`
- アプリでの扱い：
  - 単語帳では、品詞がバッジ（他＝青、自＝緑、名＝金）で意味の横に出る。
  - 4択では、意味を1つずつ出題する（①〜⑥のどれか1つが正解になる）。
  - 自動めくりの読み上げでは「他動詞。1、なになにを通り過ぎる…」のように、品詞・番号・〜（なになに）も読む。
- 古い形式の「③（名）顔」のように意味の頭に（名）（動）（形）（副）と書いたものも、その意味だけの品詞として読める。

## 5. 例文の書き方

- 空所は `____`（下線2つ以上）。見出し語が入るところを空所にする。
- 空所が2つ以上あるときは、example_answer を `/` で区切る：`ordered / to`
- **意味の番号**：先頭に ①② を付けると、意味の番号と対応して表示される（`① Things {are} ____ ...`）。訳には番号は付けなくてよい。
- **青字**：本の青字（いっしょに覚える語・前置詞・構文）は `{ }` で囲む。
  - 例：`We {are} ____ {with} a crisis.`、`{It is} only ____ {that} you ...`、`____ {making} eye contact ...`
  - 読み上げでは `{ }` は読まない。
  - その単語のどれかの例文に `{ }` があると、その単語では自動の青字は付かない（`{ }` がない古いデータだけ、頻出表現から自動で青字を推測する）。
- **赤字**（見出し語）は空所 `____` と example_answer で表す。
- 穴埋め問題は、空所のある例文の中から毎回違うものを選んで出題する。空所のない例文は表示・読み上げだけに使われる。
- 1つのセルに改行で複数の例文を書いてもよい（その場合は訳・答えも同じ順に改行で並べる）。ただし example2… の列に分けるほうが確実。

## 6. 頻出・注意・成り立ち・関連語・メモの書き方

- 1つのセルに複数書くときは **改行** か **全角の「／」** で区切る（半角の `/` は区切りにならない）。
- **phrases**：`英語「日本語」` の形で書くと、英語部分が太字になる。補足は後ろに（ ）で。
  `(人) be faced with ~「（人）が〜に直面している」（受動的）`
- **caution**：誤りやすい点・区別。×の例はそのまま書く。
  `Don't put your head［×face］out of the window.「窓から顔を出すな。」`
- **origin**：`prob-［証明］＋-abl-［可能］から「証明できそう」→「おそらく」`
- **related**：先頭に「名・形・副・動・反・同・類・派」＋半角スペース＋英語。
  `名 likelihood「可能性」`、`反 unlikely「〜しそうにない」`、`形 facial「顔の」⇒ facial expressions「顔の表情」`
  関連語がアプリに登録されていれば、タップでその単語のカードに飛べる。
- **note**：上のどれにも当たらない説明（コアイメージ・ニュアンス・比較など）。

## 7. セクションと小テーマ

- section と theme を別の列に書くのが確実：section=`Part 1`、theme=`感謝・謝罪`
- section に `Part 1 感謝・謝罪` とまとめて書いても、同じ「Part 1」に2種類以上の続きがあれば自動で「Part 1」＋小テーマに分かれる。

## 8. 読み込むときの注意

- **設定から読み込む**：**ファイル名が教材名** になる（book列は使われない）。
  例：`LEAP 必携英単語.csv` → 教材「LEAP 必携英単語」
- **同じファイル名で読み込み直す**：その教材が丸ごと置き換わる（習熟度は単語ごとに記録しているので消えない）。
  iPhoneで同じファイルを再ダウンロードすると「〜 2.csv」と名前が変わり、別の教材として増えることがあるので注意。
- **教材の画面から取り込む**：その教材に追加される（既存の単語は残る）。
- 同じ英語（question）の単語は、教材が違っても習熟度を共有する。

## 9. 本（LEAP）の表記との対応

| 本の表記 | CSV |
|---|---|
| 見出し語・発音記号 | question・pron |
| 他／自／名 などの黒い四角と ①② の意味 | answer（〔他〕①… 〔自〕⑤…） |
| 赤字の見出し語（例文中） | 空所 `____` ＋ example_answer |
| 青字（例文中） | `{ }` で囲む |
| 右ページの例文①②…と訳 | example〜exampleN（先頭に①②）・_ja |
| 頻出 | phrases |
| 注意 | caution |
| ▶（コアイメージ・補足説明）、◇（比較） | note |
| 📌の語源（prob-[証明] など） | origin |
| 📌の派生語・反意語（形 passing、反 unlikely など） | related |

## 10. 記入例（likely・avoid）

| 列 | likely | avoid |
|---|---|---|
| section | Part 1 | Part 1 |
| theme | 可能性・確実性 | 直面・回避・解決・問題 |
| category | 形容詞 | 動詞 |
| question | likely | avoid |
| answer | 〔形〕①（to do）〜しそうだ、可能性が高い 〔副〕②おそらく | 〔他〕〜を避ける |
| pron | [láikli] | [əvɔ́id] |
| example | ① Things {are} ______ {to} improve. | ______ {making} eye contact with monkeys. |
| example_ja | 事態はよくなりそうだ。 | サルとは目を合わせないようにしなさい（サルと目を合わせることを避けろ）。 |
| example_answer | likely | Avoid |
| example2 | ② He will very ______ stay home. | |
| example2_ja | おそらく、彼は家にいるだろう。 | |
| example2_answer | likely | |
| phrases | be likely to do「〜しそうだ」（＝It is likely that S V.） | avoid doing「〜するのを避ける」（×avoid to do） |
| origin | | a-［＝away 離れて］＋-void［空っぽの］（vacant「空いている」と同じ仲間） |
| related | 名 likelihood「可能性」（改行）反 unlikely「〜しそうにない」 | 形 unavoidable「避けられない」 |
| note | | 「（危険なものや嫌なもの）を遠ざける」 |

CSVにすると（likely の行。related は改行を含むので `"` で囲む）：

```
id,section,theme,type,category,question,answer,pron,example,example_ja,example_answer,example2,example2_ja,example2_answer,phrases,caution,origin,related,note
120,Part 1,可能性・確実性,word,形容詞,likely,〔形〕①（to do）〜しそうだ、可能性が高い 〔副〕②おそらく,[láikli],① Things {are} ______ {to} improve.,事態はよくなりそうだ。,likely,② He will very ______ stay home.,おそらく、彼は家にいるだろう。,likely,be likely to do「〜しそうだ」（＝It is likely that S V.）,,,"名 likelihood「可能性」
反 unlikely「〜しそうにない」",
```
