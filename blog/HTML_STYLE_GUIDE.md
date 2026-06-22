# gcff.jp ブログ記事 HTMLスタイルガイド（厳格版）
**Routineは記事を書く際、このファイルのテンプレートを「コピーして埋める」形で使うこと。**
**新しい書式・ショートコード・クラス名を自分で考案することは禁止。**

---

## 🚫 やってはいけないこと（過去に発生した失敗例）

以下は実際に過去のRoutine実行で発生した誤りです。二度と行わないこと。

| 誤り | 正しい対応 |
|---|---|
| `[speech_bubble type="ln" subtype="R1" ...]本文[/speech_bubble]` というショートコードを使う | 存在しないショートコード。下記「②吹き出し」のCocoonブロックコメント形式を使う |
| `<div class="tab-caption-box label-green">` のような独自クラス名を作る | 下記「③タブボックス」の正式なブロックコメント形式を使う |
| `<table>` を装飾なしで書く | 下記「④表」の通り、ネイビーヘッダー＋inline styleで書く |
| `<p>本文</p>` のように `<!-- wp:paragraph -->` を付けない | 全ての段落に `<!-- wp:paragraph -->` `<!-- /wp:paragraph -->` を付ける |
| 著者名を「うり」にする | 著者名は必ず **Julie** |
| `<h2>タイトル</h2>` を `<!-- wp:heading -->` なしで書く | 見出しは必ずブロックコメントで囲む |
| 強調したい文章に下線を使わない | `<span class="marker-under">` または `<span class="marker-under-red">` を使う |

---

## ① 段落（最も基本・全文章で使う）

```html
<!-- wp:paragraph -->
<p>ここに本文を書く。強調したい部分は<span class="marker-under"><strong>下線付きで強調</strong></span>する。特に注意を引きたい場合は<span class="marker-under-red"><strong>赤い下線</strong></span>を使う。</p>
<!-- /wp:paragraph -->
```

---

## ② 見出し（h2 / h3 / h4）

```html
<!-- wp:heading -->
<h2 class="wp-block-heading">大見出し（記事の章）</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3 class="wp-block-heading">中見出し（章の中の節）</h3>
<!-- /wp:heading -->

<!-- wp:heading {"level":4} -->
<h4 class="wp-block-heading">小見出し（節の中の項目）</h4>
<!-- /wp:heading -->
```

---

## ③ 吹き出し（Julieの実体験・感情を入れる。最重要パーツ）

**これが正式なCocoonブロック形式。これ以外の書き方（ショートコード等）は絶対に使わない。**

```html
<!-- wp:cocoon-blocks/balloon-ex-box-1 {"name":"Julie","index":"10","id":"11","icon":"https://gcff.jp/wp-content/uploads/2022/04/IMG_6518-1.jpg","position":"r","backgroundColor":"watery-green","backgroundColorValue":"#ebf8f4"} -->
<div class="wp-block-cocoon-blocks-balloon-ex-box-1 speech-wrap sb-id-11 sbs-stn sbp-r sbis-cb cf block-box not-nested-style cocoon-block-balloon" style="--cocoon-custom-background-color:#ebf8f4"><div class="speech-person"><figure class="speech-icon"><img src="https://gcff.jp/wp-content/uploads/2022/04/IMG_6518-1.jpg" alt="Julie" class="speech-icon-image"/></figure><div class="speech-name">Julie</div></div><div class="speech-balloon has-background has-watery-green-background-color"><!-- wp:paragraph -->
<p>ここに実体験・感情を書く。長くなる場合は<br><br>で段落分けし、要点には<span class="marker-under"><strong>下線</strong></span>を入れて読みやすくする。</p>
<!-- /wp:paragraph --></div></div>
<!-- /wp:cocoon-blocks/balloon-ex-box-1 -->
```

**ルール：**
- `name` は必ず `"Julie"`
- `icon` のURLは固定（変更しない）：`https://gcff.jp/wp-content/uploads/2022/04/IMG_6518-1.jpg`
- `position` は `"r"`（右）固定
- `backgroundColor` は `"watery-green"` 固定
- 100字を超える場合は `<br><br>` で2〜3段落に分け、要点に下線を引く（読みやすさ重視。1ブロックの壁にしない）

---

## ④ タブ形式の情報ボックス（特徴まとめ・注意点まとめに使う）

```html
<!-- wp:cocoon-blocks/tab-caption-box-1 {"content":"ここに見出しテキスト","icon":"fab-lightbulb","borderColor":"ex-d","notNestedStyle":false,"borderColorValue":"#f2a742"} -->
<div class="wp-block-cocoon-blocks-tab-caption-box-1 tab-caption-box block-box has-border-color has-ex-d-border-color cocoon-block-tab-caption-box"><div class="tab-caption-box-label block-box-label box-label fab-lightbulb"><span class="tab-caption-box-label-text block-box-label-text box-label-text">ここに見出しテキスト</span></div><div class="tab-caption-box-content block-box-content box-content"><!-- wp:paragraph -->
<p>ここに本文。</p>
<!-- /wp:paragraph --></div></div>
<!-- /wp:cocoon-blocks/tab-caption-box-1 -->
```

### アイコン・色のバリエーション（用途別に選ぶ）

| 用途 | icon | borderColor | borderColorValue |
|---|---|---|---|
| ポジティブな情報・メリット | `fab-lightbulb` | `ex-d`（オレンジ） | `#f2a742` |
| 注意・警告 | `fab-exclamation-circle` | `orange` | `#f39800` |
| チェックリスト・確認事項 | `fab-check-circle` | `ex-g`（緑） | `#1a6b3c` |
| まとめ | `fab-pencil` | `ex-d` | `#f2a742` |

### 箇条書きを入れる場合（タブボックス内）

```html
<!-- wp:cocoon-blocks/tab-caption-box-1 {"content":"見出し","icon":"fab-check-circle","borderColor":"ex-g","notNestedStyle":false,"borderColorValue":"#1a6b3c"} -->
<div class="wp-block-cocoon-blocks-tab-caption-box-1 tab-caption-box block-box has-border-color has-ex-g-border-color cocoon-block-tab-caption-box"><div class="tab-caption-box-label block-box-label box-label fab-check-circle"><span class="tab-caption-box-label-text block-box-label-text box-label-text">見出し</span></div><div class="tab-caption-box-content block-box-content box-content"><!-- wp:list -->
<ul class="wp-block-list"><!-- wp:list-item -->
<li>✅ <strong>項目1</strong>：説明</li>
<!-- /wp:list-item -->
<!-- wp:list-item -->
<li>✅ <strong>項目2</strong>：説明</li>
<!-- /wp:list-item --></ul>
<!-- /wp:list --></div></div>
<!-- /wp:cocoon-blocks/tab-caption-box-1 -->
```

---

## ⑤ 表（必ずネイビーヘッダー。装飾なしの`<table>`は禁止）

```html
<!-- wp:html -->
<div style="overflow-x:auto;margin:16px 0;">
<table style="width:100%;border-collapse:collapse;font-size:13px;">
  <thead>
    <tr style="background:#0d2240;color:white;">
      <th style="padding:10px 12px;">列1</th>
      <th style="padding:10px 12px;">列2</th>
      <th style="padding:10px 12px;">列3</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background:#f0fdf4;">
      <td style="padding:10px 12px;font-weight:bold;">行1セル1</td>
      <td style="padding:10px 12px;">行1セル2</td>
      <td style="padding:10px 12px;">行1セル3</td>
    </tr>
    <tr>
      <td style="padding:10px 12px;font-weight:bold;">行2セル1（白背景）</td>
      <td style="padding:10px 12px;">行2セル2</td>
      <td style="padding:10px 12px;">行2セル3</td>
    </tr>
  </tbody>
</table>
<p style="font-size:11px;color:#999;margin-top:4px;">※ 出典や注記はここに小さく入れる</p>
</div>
<!-- /wp:html -->
```

**ルール：**
- ヘッダー行は必ず `background:#0d2240;color:white;`（ネイビー×白）
- データ行は1行ごとに `style="background:#f0fdf4;"`（薄緑）と無指定（白）を交互にする（ゼブラストライプ）
- 強調したい列（項目名など）は `font-weight:bold;`

---

## ⑥ 箇条書きリスト（通常のリスト）

```html
<!-- wp:list -->
<ul class="wp-block-list"><!-- wp:list-item -->
<li><strong>項目名</strong>：説明文</li>
<!-- /wp:list-item -->
<!-- wp:list-item -->
<li><strong>項目名2</strong>：説明文2</li>
<!-- /wp:list-item --></ul>
<!-- /wp:list -->
```

---

## ⑦ 関連記事・ツールへの送客（blogcard）

```html
<!-- wp:cocoon-blocks/blogcard {"style":"blogcard-type bct-related"} -->
<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-related">
<a href="https://gcff.jp/記事のURL/">https://gcff.jp/記事のURL/</a>
</div>
<!-- /wp:cocoon-blocks/blogcard -->
```

公開済み記事のURLは必ず `blog/published_articles.md` から確認すること。存在しないURLを書かない。

---

## ⑧ 強調表現（下線）の使い分け

| 用途 | コード |
|---|---|
| 通常の強調（ポジティブ・重要ポイント） | `<span class="marker-under"><strong>テキスト</strong></span>` |
| 警告・注意・「実は損するポイント」 | `<span class="marker-under-red"><strong>テキスト</strong></span>` |

文章の中で「ここだけは読んでほしい」という1〜2箇所に絞って使う。多用しない。

---

## ⑨ 余白調整（セクション間の区切り）

```html
<!-- wp:spacer {"height":"40px"} -->
<div style="height:40px" aria-hidden="true" class="wp-block-spacer"></div>
<!-- /wp:spacer -->
```

大きな章の切り替わり（吹き出しの後など）に時々使う。多用しない。

---

## ⑩ カード型の図解（メリデメ・ステップ・カテゴリー比較）

数値や選択肢を視覚的にカード分けしたい場合：

```html
<!-- wp:html -->
<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin:16px 0;">
  <div style="background:#f0fdf4;border:2px solid #1a6b3c;border-radius:10px;padding:14px;text-align:center;">
    <div style="font-size:22px;margin-bottom:4px;">🏠</div>
    <div style="font-size:13px;font-weight:bold;color:#1a6b3c;margin-bottom:4px;">見出し</div>
    <div style="font-size:11px;color:#6b6560;">説明</div>
  </div>
  <!-- 必要な数だけdivを増やす -->
</div>
<!-- /wp:html -->
```

---

## 記事冒頭のメタ情報ヘッダー（必須）

すべての記事は、本文の前に以下3点をHTMLコメントで記載する。**タイトル・キーワード・メタディスクリプションの3点セットは必須。**

```html
<!-- タイトル：（32文字前後・主要キーワードを前方に含める） -->
<!-- 狙うキーワード：キーワードA / キーワードB / キーワードC -->
<!-- メタディスクリプション：（110〜120文字。記事の結論と読むメリットを要約し、主要キーワードを自然に含める。検索結果に表示される文章なので、クリックしたくなる具体性を持たせる） -->
```

### メタディスクリプションの書き方ルール
- **文字数**：110〜120字（PC検索結果で全文表示される目安。長すぎると途中で「…」と切れる）
- **主要キーワードを前半に**自然に含める（SEO評価とユーザーの視認性の両立）
- **記事の結論・数字・具体策を1つ入れる**（例「手数料ほぼゼロ」「最大18ヶ月」など）。抽象的な煽りだけにしない
- 「〜を解説します」「〜を実体験を元にお伝えします」など、読むメリットが伝わる締めにする
- 誇大表現・確約表現（「絶対」「必ず儲かる」等）は使わない

---

## 記事の標準テンプレート構成（この順番で書く）

```
0. メタ情報ヘッダー（上記：タイトル・キーワード・メタディスクリプション）
1. <!-- wp:paragraph --> リード文（2〜3段落、検索意図に答える導入）
2. <!-- wp:cocoon-blocks/balloon-ex-box-1 --> Julieの一言（記事を読む理由を一言で）
3. <!-- wp:cocoon-blocks/tab-caption-box-1 --> この記事でわかること（箇条書き）
4. <!-- wp:heading --> 本編の章（H2）→必要に応じてH3で細分化
   - 表・タブボックス・吹き出しを適度に挟む
5. <!-- wp:heading --> まとめ（H2）
6. <!-- wp:cocoon-blocks/tab-caption-box-1 --> この記事のまとめ（箇条書き、fab-pencil）
7. <!-- wp:cocoon-blocks/blogcard --> 関連記事・ツールへの送客
```

---

## 文字数・トーンの基準

- 3,000〜5,000字
- 知的で落ち着いた文体（Julieの声）
- 数値・固有名詞は必ず一次情報で確認し、出典を本文または表の下に明記
- 確認できない情報は「現時点で確認できる信頼性のある情報は存在しません」と書く。推測で埋めない



---

## ⑪ アフィリエイトリンク管理（記事ごとに「貼れるか」を必ず検討する）

**重要：ブログ記事を書くたびに、下記のアフィリエイトのどれかを自然に貼れないか必ず検討し、文脈に合うものはなるべく貼る。**
ただし読者の信頼を損なう不自然なねじ込みは禁止。記事テーマと関連し、読者にとって本当に役立つ場合のみ設置する。

### 保有アフィリエイト一覧

| サービス名 | ジャンル | 主な訴求対象記事 | 報酬・備考 |
|---|---|---|---|
| **Wise** | 海外送金・多通貨カード | 二拠点のお金管理／CAD⇄JPY／移住前準備／海外口座維持 | 個人登録＋送金完了で報酬。Cookie無期限。最優先で設置を検討 |
| **保険のマンモス** | 保険相談・見直し | 海外移住の保険／医療費／帰国準備 | 既存記事「保険のマンモスで海外移住の保険を見直した話」あり。blogcard送客＋本文導線 |
| **エンワールド（en world）** | 外資・グローバル転職エージェント | 駐在妻の帰国転職／二拠点キャリア／外資転職／キャリア系 | バイリンガル・外資志向の読者向け。キャリア記事で本文導線＋CTA |
| **JACリクルートメント** | 管理職・専門職／海外・外資転職 | 帰国転職／二拠点キャリア／ハイクラス転職 | エンワールドと並べて「外資・グローバル転職の2大エージェント」として比較紹介可 |
| **Cambly / Cambly Kids** | オンライン英会話（ネイティブ） | バイリンガル育児／年齢別英語ツール／小学生〜の英語 | トピック15と連動。幼児はLingokids等→小学生〜Camblyの導線で設置 |
| **ディズニー英語システム（DWE）** | 幼児向け英語教材 | バイリンガル育児／未就学児の英語／英語の始め方 | 高単価教材。幼児期の英語記事で資料請求導線。家庭の方針次第なので押し付けない紹介に |
| **リモフル（Remoful）** | リモートワーク特化の転職エージェント | 海外で働く／Workaway等の海外滞在／二拠点キャリア／場所に縛られない働き方 | ビジネス職×フルリモート×正社員特化。海外から勤務可能な求人あり。もしもアフィリエイト経由で提携可。「無報酬の文化交流の先に、収入も得る働き方」という導線で送客 |

> ⚠️ **このリストはうりが随時更新する。** 新しいアフィリエイト契約が増えたら、この表に「サービス名・ジャンル・訴求記事・報酬/備考」を追記すること。Routineは記事執筆時にこの表を確認し、テーマに合うものを優先的に提案・設置する。

> 📝 **整合性メモ（ディズニー英語システム）**：トピック15「バイリンガル育児」では、未就学児にはLingokids／Khan Academy Kids等を入り口として推す論調。DWEは「高単価でも家庭でしっかり取り組める層向けの選択肢」として、Lingokids等と並べて中立的に紹介する（「DWEだけが正解」という書き方はしない）。読者の信頼を損なわないことを最優先。

### 設置のルール
- **文脈優先**：記事テーマと関連が薄いリンクは貼らない（信頼が最優先）
- **設置箇所**：本文中の自然な流れ（例：「私はWiseを使っています」の箇所）＋記事末尾のblogcard/CTA
- **誇大表現の禁止**：「絶対お得」「必ず儲かる」等は使わない。事実ベースで紹介
- **ステマ回避**：アフィリエイトリンクを含む場合、記事内に「本記事はアフィリエイトリンクを含みます」等の表記を入れる（景品表示法のステマ規制対応）
- **一次情報の明記**：手数料・レート・キャンペーン条件は変動するため「最新は公式で確認」と必ず添える


