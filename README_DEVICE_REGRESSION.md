# Candidate123 Device Regression Runner v1 — TEST ONLY

Release: `2026-10-08-candidate123-numeric-review-guard`. Candidate122正式baselineからの数値安全ガード（review-only）を検証します。

1. 既存の Candidate122 Runner に置いていた `corpora/meka142/images/` と `corpora/nano30/images/` を、このRunnerの同名フォルダへコピー（画像は同梱していません）。
2. PCで `start_server.bat` 等を使用してRunnerを起動し、同一LANのiPhone SafariとAndroid Chromeからアクセス。Candidate122版とは異なるテスト用IndexedDB名です。
3. **「主要corpusを実行」** を各端末で1回ずつ実行。legacy51はarchiveであり正式Gateには使用しない。
4. `candidate123_regression_primary-corpora_...json` を両方保存。デバイスの処理中にブラウザを閉じない。

## 重要Gate

- 合計172枚/端末、処理エラー0、Recognition output / classifier / foods / CSVがCandidate122と同値。
- 追加Review flags（対象フィールドのみ）を確認。
  - iPhone: MEKA142-034 SP、MEKA142-105 carry、MEKA142-107 helpSeconds/carry（合計4）
  - Android: MEKA142-069 SP、MEKA142-105 carry、MEKA142-107 helpSeconds/carry、MEKA142-133 carry（合計5）
- SP再読取の誤候補だけで正しいSPを誤って警告することがないか（特にMEKA142-061）。
- すでに正しく自動確定した値に不要なreview増加がないこと。
- iOS Tesseract worker recycle全成功、processingError 0。
- Android速度悪化は別評価。

## 注意

この版は **PRELIMINARY / HOLD** です。実機Gate終了まで本番公開しないでください。数値は自動修正されず、要確認バッジだけを追加します。数値手動編集UIの実装は含まれません。

CSVの列・値および出力判定の処理はCandidate122から変更していません。数値フィールドは本CSVには出力されないものとして扱います。
