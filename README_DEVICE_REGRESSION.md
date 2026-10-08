# Candidate122 Device Regression Runner v1 — TEST ONLY

Candidate122 `2026-10-08-candidate122-review-safety-guard` の主要実機Gate用Runnerです。

- 主要Gate: iPhone Safari / Android Chrome
- 主要corpus: meka142 142 + nano30 30 = 172枚
- legacy51はarchive専用で、Candidate122の正式Gate対象外
- 画像は同梱しません。既存GitHubリポジトリの `corpora/*/images/` をそのまま保持してください。
- Candidate122本体との差分は、Runner専用IndexedDB名と狭いTEST API hookだけです。Service Worker/TIPS自動表示はRunnerでは無効です。
- 採点ルールはCandidate120 Runner v3を継承し、メインスキル表示の括弧前空白差・おてつだいブーストのタイプ表示差・未設定slotの `―`/空文字を同値扱いします。

## 最重要確認

- Candidate121と**認識値が一致すること**（Candidate122は認識値を変えない）。
- Candidate121で確認した「誤確定なのに要確認なし」の観測例が、Candidate122では要確認へ倒れること。
- iPhone: MEKA142-034/060 mainSkill、MEKA142-107 subskills、NANO30-010 nickname。
- Android: MEKA142-044/049/056/073/086 mainSkill、MEKA142-069/107 subskills、NANO30-004 nickname。
- 正しい未確定種族ケースを不要にmainSkill reviewへ倒さないこと。
- processingError / iOS worker recycle failureを増やさないこと。


Candidate122ではlegacy51を正式Gate対象外とし、主要Gateはmeka142+nano30の172枚です。
