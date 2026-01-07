# Chatty-EDU Student Manual (v0.4)

Audience: students with zero setup experience. Everything runs offline; no accounts.

## Quick start
1) Open `chatty-edu.exe` in the folder provided to you.
2) Models: bring your own GGUF (none is bundled here). If your teacher gives you one, drop it in `data/models/` and choose it via File -> Models. Model guidance lives in `resources/models/` (e.g., `resources/models/qwen/README.md`).
3) Import homework: Home tab -> "Import pack file" to load `homework_pack_*.json` (or copy it into `data/homework/assigned/`).
4) Pick your assignment in Home. Read the instructions.
5) Under "Submit work", type your answers. Add attachments if your teacher asked.
6) Click "Export submission file" to save `submission_<assignment_id>_<your_id>.json` into `data/homework/completed/`. Upload that JSON (and any attachments) using your normal hand-in method.

## Homework & Revision
- Homework packs live in `data/homework/assigned/`. If you do not see yours, click "Rescan packs + submissions" on Home.
- The Homework & Revision module has "Ask for hints" and an "LLM homework helper" tied to the selected assignment. These give hints, not full answers (teacher can configure hints-only).
- Chat tab is for general learning questions (still filtered for safety).

## File locations (under `data/` next to the exe)
- `homework/assigned/` - homework packs (`homework_pack_*.json`)
- `homework/completed/` - your exported submissions (`submission_*.json`)
- `models/` - local GGUF models; pick via File -> Models
- `config/`, `themes/`, `modules/` - app settings/themes (usually leave alone)

## Tips
- If you change computers, keep the whole folder together (the exe and `data/`).
- If the tutor says it cannot give the answer, ask for steps or key ideas instead.
- Teacher-only settings (filters, games, hints-only toggle) are locked behind the Teacher PIN; students cannot change them.

## Staying offline and safe
- Chatty-EDU works without internet; no cloud calls in normal use.
- Content filter (Janet) is on by default to block swears/mature topics.

## License
- Licensed under the GNU Affero General Public License v3.0.
- See `LICENSE` for the full text.
