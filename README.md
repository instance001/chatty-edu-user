# Chatty-EDU User Bundle

Offline, local-first learning assistant for schools. No cloud, no accounts, no tracking. This folder is a packaged Windows bundle for end users, not the source repository.

Chatty-EDU never connects to the internet in normal use and does not require external services to function.

## Start here
1. Open `chatty-edu.exe`.
2. Put an approved GGUF model into `data/models/`.
3. Launch the app again if needed, or use File -> Models to refresh and inspect the current model roles.
4. Import a homework pack into `data/homework/assigned/` or use Home -> "Import pack file".
5. Keep the Teacher menu locked on student-facing machines and change the default PIN on first teacher use.

## Included in this bundle
- `chatty-edu.exe` - the desktop application
- `README.md` - this quick overview
- `student_user_manual.md` - student-facing usage guide
- `teacher_user_manual.md` - teacher-facing usage guide
- `security_privacy_statement.md` - privacy and local-data posture
- `it_deployment_guide.md` - deployment guidance for school IT
- `design_intent.md` - product boundaries and intent
- `GLOSSARY.md` - terminology reference
- `CHANGELOG.md` - recent changes
- `resources/` - sample packs, attachments, and model guidance notes
- `data/` - starter runtime folder for models and local files

## Current highlights
- Markdown-first homework packs: author `*.md` in `homework/outgoing/` and transcribe to JSON packs in `homework/assigned/`.
- Homework-aware chat guardrails: active homework questions are intercepted and steered toward hints instead of full answers.
- Separate Revision workflow: Revision pulls from completed homework, keeps revision notes under `revision/notes/`, supports past papers under `revision/past_papers/`, and uses a looser helper than live homework.
- Tri-helix memory surfaces: Chat includes `Chatty's thoughts` on the left for current-session context, `Memory jogger` on the right for recent cross-session summaries, and a teacher-only Bookkeeper log search view behind the Teacher PIN.
- ECG window: a small top-right activity trace acts as a transparency and trust feature, showing visible local activity on the local machine.
- Automatic model role selection: on boot, Chatty-EDU scans `data/models/`, gives the largest valid GGUF to the main chat role, gives the smallest to the Bookkeeper role when 2+ models are present, and falls back to a friendly setup message when no model is available.
- Plain-text-safe rendering: model output is normalized before display so unsupported Unicode, prompt-template markers, and odd table characters degrade into readable text instead of broken glyphs.

## Models
- Model weights are not included in this bundle.
- Drop an approved GGUF into `data/models/`.
- On startup, the largest valid GGUF becomes the main AI role.
- If 2 or more valid GGUFs are present, the smallest valid GGUF becomes the Bookkeeper role.
- If only 1 model is present, the main AI uses it and Bookkeeper stays in keyword-only summary mode.
- If no GGUF is present, the app shows a friendly setup message instead of a raw technical path error.
- Model guidance and attribution are included under `resources/models/`.

## Bundle layout
- `data/models/` - drop GGUF models here
- `data/homework/assigned/` - homework packs (`homework_pack_*.json`)
- `data/homework/completed/` - exported student submissions (`submission_*.json`)
- `data/revision/notes/` - saved revision notes or progress
- `data/revision/past_papers/` - imported past papers and revision materials
- `data/config/bookkeeper/` - local Bookkeeper files including `cold_log.jsonl` and `memory_jogger.txt`

The rest of the `data/` tree is created automatically as the app runs.

## Recommended docs
- Students: read `student_user_manual.md`
- Teachers: read `teacher_user_manual.md`
- School IT: read `it_deployment_guide.md` and `security_privacy_statement.md`

## Offline and trust stance
- Offline by default; no network calls in core flows.
- Bookkeeper memory stays local under `data/config/bookkeeper/`.
- `Chatty's thoughts` is session-only, while `Memory jogger` persists locally across sessions.
- The ECG window reads local Windows counters only; it is a transparency cue, not telemetry.
