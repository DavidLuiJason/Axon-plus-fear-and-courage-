# AXON JOB BOARD (live hand-over; keep current; updated 2026-10-18 by the Director)

Read after `docs/ROADMAP.md`. This file is volatile: update it after EVERY decision, inspection and merge, and give the owner the updated lines (roadmap 5.5). Status words: NOT SENT, SENT, RETURNED, INSPECTED-OK, INSPECTED-FIX, MERGED. All jobs are NOT SENT unless a line in the STATUS LOG says otherwise.

## 1. The jobs (prompt files are in docs/prompts/; the owner has copies)

WAVE 1, ChatGPT, engines only, all independent, can run at the same time (each in its own NEW chat with its prompt, AXON_ROADMAP_V16_3.md and a BASE.zip of the repository):
C01 small engines. RETURNED 2026-10-18: only loan and split and tip were delivered (its sandbox could not run anything); the Director fixed both and rewrote their tests (merge package C01-merge.zip). The other three engines moved to C11.
C11 remaining small engines (pattern tester, device profile, tool store). No dependency.
C02 JSON tokens and reformat, JSON view model, CSV and TSV. No dependency.
C03 YAML subset and XML. No dependency.
C04 Markdown, HTML to text, text format hub, file inspector. No dependency.
C05 QR code with an independent decoder proof. No dependency.
C06 file compare, zip tool, image conversion plan. No dependency.
C07 image editor zoom, pan, tap-for-full-picture (the only ChatGPT job allowed to change screen files). No dependency (needs R7 in the base).

WAVE 2, ChatGPT, after the jobs they need are MERGED:
C08 code formatter engine. Needs C02.
C09 engine registry, legacy descriptors, File Compare catalog entry, truth test. Needs C01 to C06 and C11 (adapts to what exists).
C10 Converter wiring for Data formats, Text formats, Image (engine side only). Needs C02, C03, C04, C06.

AI STUDIO, screens only, each in a NEW session that imports the repository after the listed jobs are merged:
A01 screen kit and Calculator, Case Converter, Find and Replace. No ChatGPT dependency. START HERE: it sets the look of every tool screen; the owner approves it in the preview.
A02 Text Cleaner, Sort Lines, Text Compare, Percentage Helper, Number to Words, Date Calculator. Needs A01.
A03 Password Generator, Random Picker, Encoder and Decoder, Hash and Checksum. Needs A01.
A04 Timer, Stopwatch, Tally Counter, Device Profile. Needs A01 and C11.
A05 Loan Calculator, Split and Tip, Pattern Tester, JSON and Data Viewer. Needs A01, C01 (merged), C11, C02.
A06 QR Code Maker, File Compare, File Inspector, Zip and Unzip. Needs A01, C04, C05, C06, C09.
A07 Converter new kinds (Data formats, Text formats, Image). Needs A01, C10 (and so C02, C03, C04, C06).
A08 Code Formatter screen. Needs A01, C08.

After these: write and run prompts for File Converter, Batch Convert, Summarizer (extractive), Document Reader, My Dictionary (UD1); refresh this board and the roadmap; one cloud build (type check, tests, APK); phone tests; then the brain from scratch (roadmap section 7, B3 onward: first write the B3 prompt with its positive and negative corpus).

## 2. Lanes for verify_return.py (pass as --lane)
C01: src/tools/engines/finance/**,tests/loan.test.ts,tests/splitTip.test.ts,docs/reports/C01_REPORT.md
C11: src/tools/engines/code/patternTest.ts,src/tools/engines/device/**,src/tools/shared/toolStore.ts,tests/patternTest.test.ts,tests/deviceProfile.test.ts,tests/toolStore.test.ts,docs/reports/C11_REPORT.md
C02: src/tools/engines/data/jsonTokens.ts,src/tools/engines/data/jsonView.ts,src/tools/engines/data/csv.ts,tests/jsonTokens.test.ts,tests/jsonView.test.ts,tests/csv.test.ts,docs/reports/C02_REPORT.md
C03: src/tools/engines/data/yaml.ts,src/tools/engines/data/xml.ts,tests/yaml.test.ts,tests/xml.test.ts,docs/reports/C03_REPORT.md
C04: src/tools/engines/text/markdown.ts,src/tools/engines/text/htmlText.ts,src/tools/engines/text/textFormats.ts,src/tools/engines/files/inspect.ts,tests/markdown.test.ts,tests/htmlText.test.ts,tests/textFormats.test.ts,tests/fileInspect.test.ts,docs/reports/C04_REPORT.md
C05: src/tools/engines/create/qrCode.ts,tests/qrCode.test.ts,docs/reports/C05_REPORT.md
C06: src/tools/engines/files/fileCompare.ts,src/tools/engines/files/zipTool.ts,src/tools/engines/images/convertPlan.ts,tests/fileCompare.test.ts,tests/zipTool.test.ts,tests/convertPlan.test.ts,docs/reports/C06_REPORT.md
C07: src/tools/imageEdit/viewTransform.ts,src/tools/imageEdit/gesture.ts,src/components/editors/ZoomStage.tsx,src/components/editors/ImageEditorScreen.tsx,src/components/editors/CropOverlay.tsx,src/components/editors/MediaStrip.tsx,tests/viewTransform.test.ts,tests/gesture.test.ts,tests/imageEditHistory.test.ts,docs/reports/C07_REPORT.md
C08: src/tools/engines/code/codeFormat.ts,tests/codeFormat.test.ts,docs/reports/C08_REPORT.md
C09: src/tools/engines/legacyDescriptors.ts,src/capabilities/registerEngineTools.ts,src/capabilities/index.ts,src/tools/toolCatalog.ts,tests/engineTruth.test.ts,tests/tools.test.ts,tests/capabilityTruth.test.ts,docs/reports/C09_REPORT.md
C10: src/tools/converter/**,tests/convertBlocks.test.ts,tests/toolsConverter.test.ts,docs/reports/C10_REPORT.md
A01 to A08 (screens): src/components/toolScreens/**,src/components/tools/**,src/tools/screens/**,src/tools/toolCatalog.ts,src/App.tsx,src/components/AxonToolsScreen.tsx,src/components/ConverterScreen.tsx,src/components/converter/**,src/state/** (judge each job by its own LANE section; the AI Studio export is a WHOLE project, so use --make-delta and review only in-lane files)

## 3. After each AI Studio merge the Director must (tests do not block the cloud build, so do this by hand)
Update `tests/tools.test.ts` (the sorted list of available tool ids near line 103, the tool counts, any group counts) and `tests/capabilityTruth.test.ts` for exactly the catalog flips or removals of that job, run both with tsx, and say what changed. A merge package for a screen job = the in-lane delta plus these two test files.

## 4. Tool by tool (menu entries today: 61)
Open today (5): Text Counter, Interface Capture, Background Proof, Unit and Base Converter, Dictionary.
Engine exists, screen to build (16): Calculator, Case Converter, Find and Replace (A01); Text Cleaner, Sort Lines, Text Compare, Percentage Helper, Number to Words, Date Calculator (A02); Password Generator, Random Picker, Encoder and Decoder, Hash and Checksum (A03); Timer, Stopwatch, Tally Counter (A04, needs C01 tool store).
New (13): Loan Calculator, Split and Tip, Pattern Tester, JSON and Data Viewer (C01, C02, A05); Device Profile (C01, A04); QR Code Maker, File Compare, File Inspector, Zip and Unzip (C04 to C06, C09, A06); Code Formatter (C08, A08); Data formats, Text formats, Image converter (C02, C03, C04, C06, C10, A07; they retire the entries data-converter, text-format-converter, image-converter).
Later, no internet or model needed (5): File Converter, Batch Convert, Summarizer (extractive), Document Reader, My Dictionary.
Not possible honestly yet or waiting for the owner (12): Web Search, Link Analyzer, Content Extractor, Currency Converter, Translator, Rephraser, Grammar Helper, PDF Tools, Document Converter, AXON Code, AI Assistant, Backup and Restore.
LEFT OUT by the owner (11): Market Scope, Audio Converter, Text to Speech, Voice Library, Voice Cloner, Speech to Text, Video Converter, Video Maker, Video Downloader, Collage Maker, Picture to Table or Code. (Also the audio and video editors.)

## 5. STATUS LOG (newest first; add a line after every step)
2026-10-18: C01 RETURNED and INSPECTED-FIX. ChatGPT delivered loan and split-and-tip only, with thin unrun tests; the Director's run found a failing test and three defects (false 'unpayable', wrong round-up for uneven shares, silent rounding of 3-decimal bills) plus wrong descriptor ids; fixed by the Director, tests rewritten with independent Python-derived tables (720 and 15,281 checks pass, strict tsc passes). Merge package: C01-merge.zip. ChatGPT cannot install dependencies in its sandbox; prompts now say so and forbid delivering fewer items for that reason. Pattern tester, device profile, tool store moved to C11. Prompts patched to carry the exact catalog toolIds. Next: owner merges C01-merge.zip, sends C11 and the other wave 1 jobs.
2026-10-18: Round 8 planned. Roadmap v16.3, this board, the handbook and the prompt files C01 to C10 and A01 to A08 written. Earlier plan (round 7, three big ChatGPT jobs that also built screens) is SUPERSEDED: ChatGPT stopped without building on the first big job and correctly refused the dependent job on a missing base. Nothing from round 7 was merged. R7 (Image editor redraw fix) is applied by the owner. Next: owner uploads the docs package, downloads BASE.zip, sends wave 1 and A01.
