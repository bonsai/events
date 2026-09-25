# events

Google Calendar / Gemini CLI / gws に引き渡すためのイベント台帳。

## Canonical format

各イベントは以下の項目を持つ。

- `id`: stable event id
- `date`: YYYY-MM-DD
- `start`: HH:MM
- `end`: HH:MM
- `title`
- `place`
- `address`
- `price`: `無料` / `¥金額` / `要確認`
- `paid`: `NO` / `YES` / `要確認`
- `status`: `候補` / `行く` / `済` / `中止`
- `source`
- `note`

### Price rule

- 有料は必ず **⚠️ 有料** と明記
- 金額が分かれば金額を記録
- 不明な場合は無料と推測せず **⚠️ 料金要確認**
- 「イベント自体は無料だがチケットが必要」の場合も `paid: YES` とする

## Gemini → gws workflow

1. Gemini CLI がこの repo の `events.md` / `events.yaml` を読む
2. 未登録・変更イベントを抽出
3. Google Calendar の既存予定と重複確認
4. ユーザー確認後、gws で Calendar に登録
5. 登録結果をこの repo に反映

Google Workspace CLI は Calendar API を構造化 JSON で扱え、Gemini CLI extension として利用できる。  
認証後は `gws calendar +insert` などを利用する。

例:

```sh
gws calendar +agenda
```

Calendar 登録時は最低限 `title / date / start / end / place / note / source` を渡す。

## Current focus

2026-09-25 → 2026-10-31 Halloween + 大学祭

- 歌舞伎町 / 新宿
- 渋谷
- 原宿
- 池袋
- 東京の大学祭
- RAVE / LIVE / Halloween
