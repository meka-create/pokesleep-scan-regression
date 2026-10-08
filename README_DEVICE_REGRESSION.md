# Candidate121 Device Regression Runner v1 — TEST ONLY

Candidate121 `2026-10-08-candidate121-help-seconds-tolerance` の主要実機Gate用Runnerです。

- 主要Gate: iPhone Safari / Android Chrome
- 主要corpus: meka142 142 + nano30 30 = 172枚
- legacy51は低優先・将来削除予定
- 画像は同梱しません。既存GitHubリポジトリの `corpora/*/images/` をそのまま保持してください。
- Candidate121本体との差分は、Runner専用IndexedDB名と狭いTEST API hookだけです。Service Worker/TIPS自動表示はRunnerでは無効です。
- 採点ルールはCandidate120 Runner v3を継承し、メインスキル表示の括弧前空白差・おてつだいブーストのタイプ表示差・未設定slotの `―`/空文字を同値扱いします。

## 最重要確認

- `IMG_4226.png`: species=メタモン、foodsが空欄にならないこと（nicknameは別課題）。
- `IMG_4250.png`: species=ウォーグル、foodsが空欄にならないこと。
- meka142でCandidate120比の新規core regressionがないこと。
