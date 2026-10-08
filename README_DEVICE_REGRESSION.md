# Candidate120 Device Regression Runner v1

## Purpose

This is a **test-only** package for the two primary device gates:

- iPhone Safari
- Android Chrome

It runs the permanent regression image corpora through the Candidate120 production analysis path:
image -> crop -> OCR -> parse -> food -> classifier -> review state.

## Corpora

- meka142: 142, highest priority (P0)
- nano30: 30, canonical PNG real-user corpus
- legacy51: 51, low-priority legacy / planned future deletion

Future real-user corpora such as `body30` can be added by following `corpora/registry.json` + per-corpus `manifest.json`.

## Important isolation / fidelity details

The runner is **not Candidate121** and must not be deployed over the production app.
Candidate120 production recognition logic is kept unchanged. The test copy `app_regression.js` has only two runner-specific changes:

1. IndexedDB name is changed from `bukkomi-scan-checkpoint-v1` to `bukkomi-scan-regression-c120-v1` so tests cannot overwrite a user's production recovery data on the same origin.
2. A narrow test API is appended at the end of the Candidate120 app closure so canonical files can be fed to the existing `runAll()` / `runAnalysisBatch()` path and diagnostics can be read.

Service Worker registration and automatic Tips display are disabled in the runner page only. This keeps the recognition/device comparison test isolated from production cache and UI state.

`app_candidate120_original.js` and `index_candidate120_original.html` are included byte-for-byte for provenance.

## How to run on phone

Host this folder over HTTPS (for example a separate GitHub Pages test path). Open `index.html` on the target device.

Recommended order:

1. On iPhone Safari, run **meka142** first and save the JSON.
2. On Android Chrome, run **meka142** first and save the JSON.
3. If both runs are stable, run **主要corpusを実行** (meka142 + nano30) on both devices.
4. legacy51 is optional and lower priority.

meka142 is automatically split 100 + 42 because production `MAX_FILES=100`.

## Result verdicts

- `PASS_AUTO`: every scored golden field is correct and no review remains.
- `CORRECT_NEEDS_REVIEW`: values are correct but the production UI still requires manual review.
- `FAIL_VALUE`: at least one scored golden field is wrong or missing.
- `PROCESSING_ERROR`: production analysis paused with a processing failure.
- `UNPROCESSED`: no result was produced (runner/infrastructure abnormality).

The output JSON includes full Candidate120 diagnostic snapshots per partition/subrun so device-specific OCR differences can be analyzed later.

## Device comparison

Open `compare_device_runs.html`, select the iPhone JSON and Android JSON, and it will list cases whose verdict, field results, or review state differ.
