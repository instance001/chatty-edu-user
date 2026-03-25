# Chatty-EDU Teacher Manual

Audience: teachers and school IT. Everything runs offline by default; no accounts or cloud calls.

## What you need
- Windows PC
- At least 1 approved GGUF model placed into `data/models/`
- Optional: USB for portable data with `--base-path <USB path>`

## First run
1. Open `chatty-edu.exe` (add `--base-path ...` if you want data on a USB or managed folder).
2. Models:
   - Drop any approved GGUF into `data/models/`.
   - On startup, Chatty-EDU auto-scans that folder and assigns the largest valid GGUF to the main AI role.
   - If 2 or more valid GGUFs are present, the smallest detected model is assigned to the Bookkeeper role. If only 1 model is present, Bookkeeper stays in keyword-only summary mode.
   - You can still override or inspect roles via File -> Models.
   - Model guidance and licensing notes are included under `resources/models/`.
3. Teacher lock:
   - Default PIN is `0000`. Teacher menu -> unlock with PIN, or use the secret answer if you have set one.
   - While unlocked, change the PIN, set the secret question or answer, adjust game settings, and configure hints-only mode. Lock when done.
4. Import or build packs:
   - Option A (Markdown-first): put a pack `.md` into `data/homework/outgoing/` or generate it in the Teacher Dashboard, then click "Transcribe outgoing (.md -> .json)".
   - Option B (JSON): import a pack `.json` into `data/homework/assigned/` via the Home tab or Teacher menu.
   - Sample packs and attachment examples are included under `resources/`.
5. Review and tutor:
   - Home and Homework Dashboard cover assignments, submissions, metrics, and teacher summary tools.
   - Home and Main Chat are homework-aware. If a student asks or rephrases an active homework question there, the app intercepts it before generation and pushes the model into a Socratic hint-only response.
   - Chat includes `Chatty's thoughts` on the left and `Memory jogger` on the right.
   - Revision is separate from live homework and works from completed homework plus past papers.

## Homework basics
- Packs are authored in Markdown under `data/homework/outgoing/` and transcribed into JSON packs under `data/homework/assigned/`, or you can import JSON directly.
- Optional per-assignment sections in pack Markdown:
  - `### Student Printable` for a handout or visible worksheet text
  - `### Rubric` or `### Marking Guide` for teacher marking guidance
- Use `year_level` as the canonical metadata key in Markdown pack files. Import and transcribe also accept `year`, `year level`, `grade`, `grade level`, and `year group`.
- If a question refers to a worksheet, list, table, chart, or handout, place that material in `### Student Printable` or `attachments:` so students can actually see it in-app.
- Students export submission JSON into `data/homework/completed/`.
- Teacher Dashboard can export:
  - marking sheets to `data/homework/marking/`
  - student printables to `data/homework/printables/`
  - teacher rubrics to `data/homework/rubrics/`

## Revision basics
- Revision is separate from live homework. It uses completed submissions from `data/homework/completed/` plus any imported past papers in `data/revision/past_papers/`.
- Students can save their own revision notes or progress under `data/revision/notes/`.
- Student-facing Revision hides teacher-side scores and diagnostic labels.

## Memory and logs
- `Chatty's thoughts` is session-only. It shows recent message-pair context that the main chat is actively using and clears when the app closes.
- `Memory jogger` persists across sessions as a short local summary built from recent activity when the app closes.
- Sidebar entries may preview-truncate in the narrow panel, but they show fuller text on hover.
- Teacher-only Bookkeeper logs are available from File -> Models after teacher unlock. That tab is meant for local log search and support diagnosis, not for students.
- The in-app Bookkeeper tab is PIN-gated for convenience, but it is still just a local UI boundary; the underlying files remain local files on disk.

## CLI admin
Run:

```powershell
.\chatty-edu.exe --mode cli
```

Useful commands:
- `generate_pack_md`
- `transcribe_outgoing`
- `convert_submissions_to_md`
- `export_printables`
- `export_rubrics`
- `import_pack <path>`
- `import_submissions`
- `show_completed`
- `mode class`
- `mode free`
- `games on`
- `games off`
- `set_pin`
- `set_secret`

## Data layout
- `data/config/` settings, UI state, and Bookkeeper memory files
- `data/config/bookkeeper/` cold logs plus `memory_jogger.txt`
- `data/homework/outgoing/` pack Markdown
- `data/homework/assigned/` pack JSON
- `data/homework/completed/` submissions
- `data/homework/marking/` marking Markdown
- `data/homework/printables/` student printables
- `data/homework/rubrics/` teacher rubrics
- `data/revision/notes/` saved revision notes and progress
- `data/revision/past_papers/` imported past papers and teacher revision materials
- `data/models/` GGUF files

## Troubleshooting
- No model selected on startup: drop a GGUF into `data/models/` and relaunch, or refresh via File -> Models. If only one model is present, the main AI uses it and Bookkeeper stays in keyword-only mode.
- Revision or chat helper says no valid model is selected: choose a GGUF via File -> Models and confirm the file still exists under `data/models/`.
- Missing packs or submissions: click "Rescan packs + submissions".
- Missing worksheet, list, or attachment in student view: confirm it is included in `### Student Printable` or `attachments:` and not only mentioned in the instructions text.
- Odd symbols or broken table characters in chat: the app now normalizes most model output to plain readable text; if a model still emits malformed content, try a different prompt or GGUF.
- PIN issues: use Teacher menu or CLI `teacher` -> `forgot`, then set a new PIN.
