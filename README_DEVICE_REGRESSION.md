# Candidate125 Device Regression Runner v1 — TEST ONLY

Candidate125 release ID: `2026-10-09-candidate125-carry-corroborated-first-food`.
**Formal baseline: Candidate124**. Candidate125 is **PROVISIONAL / HOLD** until both real-device Gates pass.

## 実機テスト手順

1. 前回と同じ142枚の `meka142` 画像と30枚の `nano30` 画像を、それぞれ `corpora/meka142/images/` と `corpora/nano30/images/` に配置します。ZIPに画像は含まれません。画像やGoldenを改変しないでください。
2. `start_server.bat` / `start_server.command` 等でHTTPサーバーを起動し、同一LANのiPhone Safari・Android ChromeでRunnerにアクセスします。
3. それぞれ「主要corpusを実行」を実行し、`candidate125_regression_primary-corpora_...json` をダウンロードしてChatに添付してください。
4. `legacy51` は正式Gateに含めません。TEST Runnerを製品として公開しないでください。

## Gate expectations (offline replay; not device results)

- iPhone `NANO30-001` バタフリー：食材1を `とくせんリンゴ`→`あまいミツ` に修正、種族を安全に `バタフリー` へ一意化。食材1の `reviewState.foods` は **true** を維持（画像一部遮蔽）。ケースは `FAIL_VALUE`→`CORRECT_NEEDS_REVIEW` の見込み。
- Android `NANO30-001`：同じ改善と要確認維持を期待。
- 他の各171ケースはCandidate124から認識値・要確認状態・classifier/inferenceの意図しない差分なしが原則です。
- `MEKA142-107` ラティアスは未救済。曖昧な情報で種族を強制確定させないでください。
- iPhone memory guard・Tesseract呼び出し・worker recycle・CSV header/schema・checkpoint・processingErrorをCandidate124の実機JSONと比較してください。
- Candidate125は追加OCR呼び出しなし。既存の食材画像候補・最大所持数一致・classifier一意性を組み合わせた限定的な食材1救済であり、根拠不足では従来値と要確認を保持します。

元の製品Runtimeは別ZIPです。Runner専用hook・IndexedDB名前空間・ServiceWorker無効化は製品コードに含まれません。
