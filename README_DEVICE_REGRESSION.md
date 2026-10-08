# Candidate124 Device Regression Runner v1 — TEST ONLY

Candidate124 release ID: `2026-10-08-candidate124-species-ocr-consensus-rescue`.
Formal baseline is **Candidate123**, Candidate124 is **PROVISIONAL / HOLD** until the two device gates pass.

1. Copy the exact same 142 `meka142` and 30 `nano30` image files from the previous validated Runner into `corpora/meka142/images/` and `corpora/nano30/images/`. Image files are **not included**.
2. Start a local HTTP server with `start_server.bat` / `start_server.command`. Access the test page using iPhone Safari and Android Chrome (same LAN).
3. Run `主要corpusを実行` on each device. Export and attach the two Candidate124 JSON results.
4. Do not use `legacy51` for formal Gate. Do not publish the test Runner.

## Priority Gate targets (retrospective hypotheses, not yet real-device outcomes)

- iPhone: `MEKA142-060` カイリュー should become safe UNIQUE with correct mainSkill/skillLevel/foods.
- Android: `MEKA142-044`, `MEKA142-049` クワッス and `MEKA142-056` イーブイ（ホリデー） should become safe UNIQUE with correct structured fields/foods.
- `MEKA142-107` ラティアス and `NANO30-001` バタフリー should remain blank + species review pending independent fixes.
- All remaining `meka142`/`nano30` species results should not regress. No newly silent-wrong species or values.
- iPhone memory guard: 89 successful worker recycles, 0 failures/processing errors (compare actual counters, which may depend on exact runtime session).
- Compare CSV/schema/checkpoints, OCR call counts, timing, and per-field review changes case-by-case versus Candidate123.

The Candidate124 patch uses no additional OCR calls; it reuses existing retry evidence and requires two agreeing PSM passes, classifier UNIQUE and a consistent carry match. If evidence is ambiguous it abstains.
