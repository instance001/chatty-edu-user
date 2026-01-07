# Chatty-EDU Teacher Manual (v0.4)

Audience: teachers and school IT. Everything runs offline by default; no accounts or cloud calls.

## What you need
- A Windows PC.
- The Chatty-EDU folder with `chatty-edu.exe` and the `data/` folder kept together.
- Optional: a USB drive if you want a portable setup (copy the whole folder to the USB).

## First run (GUI)
1) Double-click `chatty-edu.exe`.
2) Models (offline AI):
   - Bring your own GGUF model (none is included in this repo).
   - Drop any GGUF into `data/models/`, then File -> Models to select.
   - Model guidance/licensing notes: see `resources/models/` (e.g., `resources/models/qwen/README.md`).
3) Teacher lock:
   - Default PIN `0000`. Teacher menu -> unlock with PIN (or secret answer if set).
   - While unlocked: change PIN, set secret question/answer, adjust game and hint settings. Lock when done.
4) Import/build packs:
   - Home tab -> "Import pack file" (copies to `data/homework/assigned/`).
   - Sample pack: `resources/homework_pack_sample_bundle.json` (copy into your data folder or import directly).
   - If a pack references attachments, copy the `resources/attachments/` folder into `data/homework/assigned/`.
5) Review + tutor:
   - Home tab + Homework Dashboard: assignments, filters, submissions, metrics; Teacher menu shows submissions summary.
   - Homework & Revision module: "Ask for hints" + "LLM homework helper" tied to the selected assignment; hints-only mode is teacher-configurable.
   - Submissions are written to `data/homework/completed/` and include a hash-chained event log (start/answer/hint/retry/finalize) plus a final_hash for tamper-evidence.

## Homework basics
- Packs are JSON (`homework_pack_*.json`). Place/import into `data/homework/assigned/`.
- Students: select assignment, fill "Submit work", attach files if allowed, then "Export submission file" -> `submission_<assignment_id>_<student>.json` in `data/homework/completed/`.
- Collect student submissions and place them in your `data/homework/completed/`; click "Rescan packs + submissions".

## Revision basics
- Students can reopen any pack to practice.
- Tutor (in Homework & Revision) and Chat can give hints/steps, not full answers; hints-only mode can be enforced.

## Data layout (under `data/` next to the exe)
- `config/` settings/UI
- `homework/assigned/` packs
- `homework/completed/` submissions
- `models/` GGUF files
- `modules/` manifests
- `themes/` active theme + presets
- `runtime/`, `logs/`, `revision/`, `ide/` reserved folders

## Safety/offline
- Offline-first; no network calls in core flows.
- Content filter (Janet) on by default; external process modules disabled unless allowed.

## Troubleshooting
- Missing packs/submissions: click "Rescan packs + submissions" and confirm the `data/` folder is next to the exe.
- Model not listed: confirm the file ends in `.gguf`, then open File -> Models (refresh or restart the app).
- Reset settings: delete `data/config/settings.json` and relaunch.

## License
- Licensed under the GNU Affero General Public License v3.0.
- See `LICENSE` for the full text.
