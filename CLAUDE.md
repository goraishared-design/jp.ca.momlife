# CLAUDE.md — Claude Routine 作業手順書

このファイルは、スケジュール実行される Claude が「1回の投稿準備」で行う手順をまとめたもの。

## 前提・守ること

- **声・トーン**: Instagram カルーセルは知的で落ち着いた文体。Threads はカジュアルな話し言葉。
- **ファクトチェック必須**: 数値・固有名詞は必ず一次情報（公的機関・査読論文・権威報道）で確認し、出典をスライドに入れる。確認できない情報は使わない（推測で補完しない）。
- **身バレ防止**: 子どもの人数は SNS 上「2人」で統一。早稲田はOK、学部は伏せる。
- **3本柱**: ①教育（ディープグリーン）②マネー（ネイビー×ゴールド）③日常（テラコッタ×オフホワイト）。
- **Canva 自動生成は使わない**: 既存テンプレートのテキスト差し替えのみ。`find_and_replace_text` を使う（`replace_text` はブロックされる）。
- **投稿時刻**: 日本時間（JST）21時。Blotatoに予約登録。

## 1回分の手順

### ステップ1: plan.md を読む
以下のURLから最新版を取得する：
```
https://raw.githubusercontent.com/goraishared-design/jp.ca.momlife/main/content/plan.md
```
`status: 次` の中で最も日付が近い投稿を1件選ぶ。

### ステップ2: 時事ネタをチェック（任意）
教育・マネーまわりの最新ニュースをWeb検索（Bloomberg / NYT / 公的統計）。関連があれば1スライドに差し込む。無理に入れない。

### ステップ3: カルーセル本文を作る
- 5〜8枚構成。1枚目フック / 中間1枚1メッセージ / 最終枚まとめ＋保存CTA＋ブログ送客。
- 各データに出典を明記。

### ステップ4: Canva でテキスト差し替え
1. 対象テンプレートをコピー（`copy-design`）。
   - 教育系: `DAHLnXlbqAg` / マネー系: `DAHLf3Flhu0` / 日常系: `DAHLVNBMOJ0`
2. `start-editing-transaction` で開始。
3. `perform-editing-operations` で `find_and_replace_text` を使い全テキスト差し替え。
4. 必要なら背景写真を差し替え（`upload-asset-from-url` → `update_fill`）。
5. プレビュー確認 → `commit-editing-transaction` で保存。

### ステップ5: Slack に下書きを通知
チャンネル `#sns投稿確認`（ID: `C0B8BC4BKV3`）に以下を送る：

```
📋 *投稿下書き — [日付] [ピラー]*

*タイトル*：[タイトル]
*Canva編集URL*：https://www.canva.com/d/[デザインID]

---
*キャプション案*
[本文＋ハッシュタグ]

---
✅ 内容に問題なければ、Blotatoから予約済みの投稿をそのまま確認してください。
修正がある場合は、Canvaで直接編集するか、このスレッドに返信してください。
```

### ステップ6: Blotato に予約投稿を登録
- Instagram account ID: `51161`
- Threads account ID: `7202`
- 投稿時刻: その日の **JST 21:00**（UTC 12:00）
- カルーセル画像: Canva export → Blotato `create_presigned_upload_url` で再アップ → `blotato_create_post` に mediaUrls で渡す

### ステップ7: plan.md の status を更新
GitHub API で `content/plan.md` の該当投稿の `status: 次` を `status: 予約済` に更新する。

## トラブル時

- Canva の `replace_text` が "No approval received" → `find_and_replace_text` に切り替える。
- 画像URLが弾かれる → Canva一時URLをBlotatoの presigned upload 経由で永続URL化する。
- GitHub API が到達不可 → plan.md は直近セッションから引き継いだ内容を使い、後でGitHubを同期する。
