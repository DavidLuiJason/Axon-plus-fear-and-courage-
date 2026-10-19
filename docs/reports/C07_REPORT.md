# C07 Report — Image editor zoom, pan and full-picture view

Date: 2026-10-19

## Delivery status and evidence

**PARTIAL DELIVERY — pure engines and their tests pass; full project validation is blocked by the unavailable/incomplete npm toolchain.** The UI integration is written and syntax-transpiled, but a full React/Capacitor type-check and the existing kernel suite were not completed. Do not mark C07 DEVICE-CONFIRMED or merge without the Director's independent validation.

The BASE check passed: all six required files exist at their specified paths, including `src/components/editors/ImagePipeline.ts`. `bitmapVersion` still has four increments and remains in the redraw effect dependencies. No dependencies or package files were changed.

## Top view

The finished AXON is layered from build/data foundations through the core English dictionary, reading and understanding, response, and reach through tools, settings, memory and media. C07 belongs to Media and changes only picture viewing in the existing image editor. Later risks include crop-coordinate regressions, resize/rotation and undo interactions, native Back handling, and performance on the Infinix Note 10. Zoom is applied through CSS to a wrapper, not by redrawing or changing canvas pixels, so export continues to use the original canvas dimensions.

## LAW CHECK (FL11)

### Foundation laws

1. **FL1 — Top view:** This is a Media-layer enhancement within the existing architecture.
2. **FL2 — Read everything, then act:** The complete v16.4 roadmap, v16.3 archive, job board, Director handbook, C07 prompt and required base paths were reviewed before implementation.
3. **FL3 — Plan reaches the end:** Crop, adjust, filters, undo/redo, picture switching, export, resizing and rotation interactions were considered.
4. **FL4 — Progress first:** Work was split into pure geometry, pure gesture reduction, UI integration and tests. No third fix attempt was made for an unresolved issue.
5. **FL5 — Dictionary is core:** No dictionary or knowledge files were changed or omitted from the base project.
6. **FL6 — Searchable compression:** No data compression/storage changes or dependencies were introduced; image pixels are not degraded.
7. **FL7 — Measure why:** Results below report commands actually run and failures actually observed; device behaviour is not assumed.
8. **FL8 — Source export is the way home:** The return ZIP contains only new/changed C07 lane files with root-relative paths.
9. **FL9 — Plan first:** Pure transform and gesture engines were implemented before the thin React layer.
10. **FL10 — Chat is the control surface:** No new chat capability is claimed or registered; this is an editor interaction only.
11. **FL11 — Every-Stage Law:** This law check is present and repeated here in the report.
12. **FL12 — One designed brain:** No brain, registry, provider, capability or chat-routing code was changed.
13. **FL13 — Structure before vocabulary:** No brain phrases or fixed phrase lists were added; no brain files were changed.

### Building rules

1. **Rule 1 — Size the carrier:** Pointer count is capped at two, pointer work is bounded, and the random test runs exactly 5,000 seeded events.
2. **Rule 2 — Respect the foundation:** The existing editor and `ImagePipeline.ts` are reused.
3. **Rule 3 — Foundation first:** Geometry and gesture logic are pure TypeScript and tested separately from React.
4. **Rule 4 — One builder, one proof:** Targeted tests and checks were run in small steps; full-project proof remains blocked as listed below.
5. **Rule 5 — Plan before work:** Changes stay inside C07's named lane.
6. **Rule 6 — Measure, design, build, prove:** Pass/fail outcomes and check counts below are measured; missing checks are explicitly marked.
7. **Rule 7 — Preserve quality:** Zoom is CSS-only; canvas pixels and export are not resampled for viewing. No compressed data is introduced.
8. **Rule 8 — Weakest supported phone:** The interaction path avoids React state updates per pointer move, uses a requestAnimationFrame style write, and limits active pointers to two.
9. **Rule 9 — Verify the hand-off:** The ZIP is restricted to the named lane and uses relative paths.
10. **Rule 10 — Roadmap size:** No roadmap file was changed.
11. **Rule 11 — Future compatibility:** The view transform is separate from image rendering/export and can be reused by future editor interactions.
12. **Rule 12 — Locks and tests:** Existing tests and R7 changes are preserved; new deterministic tests were added. The complete suite could not run because `tsx` was unavailable.
13. **Rule 13 — Portability:** No new dependencies were added; imports and archive paths are repository-relative. The missing local toolchain is reported, not concealed.

## Files in this return

### New

- `src/tools/imageEdit/viewTransform.ts` — pure fit, scale clamp, focal zoom, pan clamp, coordinate conversion and centre-preserving refit.
- `src/tools/imageEdit/gesture.ts` — pure pointer/wheel reducer, pinch-plus-pan, no-jump pinch lift re-anchor, cancel cleanup, tap recognition and typed errors.
- `src/components/editors/ZoomStage.tsx` — thin Pointer Events layer, pointer capture, CSS transform written through requestAnimationFrame, resize/refit and full-view callbacks.
- `tests/viewTransform.test.ts` — geometry boundaries, numeric focal-point invariance, conversions, refit, bad inputs and R7 regression checks.
- `tests/gesture.test.ts` — pinch/pan/lift/cancel/third-pointer/tap/id-reuse/wheel cases and 5,000 seeded events.
- `docs/reports/C07_REPORT.md` — this report.

### Changed

- `src/components/editors/ImageEditorScreen.tsx` — wraps the displayed canvas/preview in `ZoomStage`; full-picture mode hides the existing header/action/bottom areas, respects safe-area insets, preserves the same canvas/export path, and registers a temporary Capacitor Back listener plus browser Escape fallback. `bitmapVersion` increments and dependency are preserved.

### Not changed

`src/components/editors/CropOverlay.tsx`, `src/components/editors/MediaStrip.tsx`, `tests/imageEditHistory.test.ts`, `package.json`, `src/App.tsx`, `src/tools/toolCatalog.ts`, dictionary files and all other screens.

## Commands and measured results

- `node --experimental-strip-types tests/viewTransform.test.ts` — **PASS, 86 checks**.
- `node --experimental-strip-types tests/gesture.test.ts` — **PASS, 25,020 checks**, including 5,000 seeded events.
- `tsc --noEmit --target ES2022 --module ESNext --moduleResolution bundler --allowImportingTsExtensions --skipLibCheck src/tools/imageEdit/viewTransform.ts src/tools/imageEdit/gesture.ts` — **PASS, 0 TypeScript errors** for the two pure engines.
- TypeScript `transpileModule` syntax/transpile check for `ZoomStage.tsx`, `ImageEditorScreen.tsx`, `viewTransform.test.ts` and `gesture.test.ts` — **PASS, 0 syntax/transpile errors per file**. This is not a type-check.
- `tsc --noEmit -p tsconfig.json` — **FAIL / blocked by environment**: `TS2688: Cannot find type definition file for 'vite/client'`.
- `npm run test:kernel` — **FAIL / blocked before first test**: `sh: 1: tsx: not found`.
- `npm ci --offline --ignore-scripts --no-audit --no-fund` — **FAIL**: npm cache miss for `yauzl-2.10.0.tgz` (`ENOTCACHED`).
- `npm ci --ignore-scripts --no-audit --no-fund` — **NOT RUN to completion**: command hung until the execution transport timed out; the partial `node_modules` tree was unusable and the process was stopped.
- `npx --no-install tsx --version` — **NOT RUN to completion**: execution timed out; no working `tsx` executable was available.
- `npx tsx tests/viewTransform.test.ts` and `npx tsx tests/gesture.test.ts` — **NOT RUN** because `tsx` was unavailable and dependency installation could not complete.
- `npx tsc --noEmit -p tsconfig.json` — **NOT RUN as an npx invocation**; the equivalent available global `tsc --noEmit -p tsconfig.json` command was run and failed for missing `vite/client` as recorded above.
- Whole existing `test:kernel` — **NOT RUN to completion**. It stopped before `askChoices.test.ts`; therefore no existing kernel test is claimed to have passed in this run.

The test expectations use independent geometric equations: fit is `min(stageWidth/pictureWidth, stageHeight/pictureHeight)`, focal zoom is checked through forward/inverse coordinate conversion, and the scripted pinch scale is independently `160/100 = 1.6`. The random sequence uses fixed seed `0xC07A11` and a bounded 5,000-event loop.

## Package script lines for the owner

Add these individual commands to the existing `test:kernel` chain in `package.json` (do not replace the current chain):

```text
tsx tests/viewTransform.test.ts
tsx tests/gesture.test.ts
```

Recommended insertion point: immediately after `tsx tests/imageEditHistory.test.ts`.

## NOT RUN / unfinished

- Full project type-check: **NOT PASSING / blocked** because dependencies are incomplete and `vite/client` types are missing.
- `test:kernel`: **NOT RUN to completion**, blocked because `tsx` is missing.
- UI type-check against the project's actual React and Capacitor declarations: **NOT RUN**. The UI files passed syntax/transpile only.
- Browser preview and all physical-device checks: **NOT RUN on device**. No phone was available in this environment.
- Director's independent overlay/BASE diff review and cloud build: **NOT RUN**.

## Owner phone checklist — every item NOT RUN on device

1. **NOT RUN on device:** Pinch at the picture edge; confirm no jump or blank gap.
2. **NOT RUN on device:** Pinch while moving both fingers; confirm pinch and pan remain continuous.
3. **NOT RUN on device:** Lift one finger mid-pinch and continue dragging the remaining finger; confirm no jump.
4. **NOT RUN on device:** Fast flick while zoomed; confirm pan clamps cleanly without drift or stuck state.
5. **NOT RUN on device:** Compare a tap with a tiny drag under 8 px and a slow press over 250 ms.
6. **NOT RUN on device:** Tap the picture to enter full-picture view, then tap again to restore the editor.
7. **NOT RUN on device:** Rotate the phone while in full-picture view; confirm the picture remains stable and bounded.
8. **NOT RUN on device:** Press Android Back in full-picture view; confirm it exits full view before leaving the editor.
9. **NOT RUN on device:** Switch pictures while zoomed; confirm the next picture starts at fit.
10. **NOT RUN on device:** Open Crop while zoomed; confirm fit reset, correct crop-handle coordinates and normal crop behaviour.
11. **NOT RUN on device:** Export while zoomed; compare output dimensions and pixels with the unzoomed edit.

## Acceptance note

The pure geometry and gesture engines are complete against their current tests. This package is intentionally evidence-labelled as a **partial delivery** because the required full-project type-check and complete `test:kernel` run could not be performed in this sandbox. The Director must not treat UI integration as fully verified until those checks run in a complete dependency environment.
