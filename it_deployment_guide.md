# Chatty-EDU IT Deployment Guide

Audience: school IT, sysadmins, and deployment teams.

This bundle is intended to run offline on local school hardware. It stores data as files on disk under a configurable base directory.

The small ECG indicator in the GUI is part of that deployment story: it is a visible transparency feature intended to help schools, students, and parents see that Chatty-EDU is actively doing local work instead of hiding background activity.

## Quick start
1. Place `chatty-edu.exe` in a writable folder, or plan a dedicated writable data folder and use `--base-path`.
2. Place approved GGUF model files into `<base>/models/` or `data/models/` if running portable.
3. Launch GUI:

```powershell
.\chatty-edu.exe --mode gui
```

4. On startup, Chatty-EDU auto-scans the models folder and assigns roles where possible. Use File -> Models to inspect or override the selection.
5. Teacher unlock: default PIN is `0000` and should be changed immediately.

## Deployment models
- Portable folder:
  - Keep `chatty-edu.exe`, the docs, `resources/`, and `data/` together in one writable folder.
  - By default, Chatty-EDU uses `./data` next to the executable.
- Installed binary plus separate data:
  - Use `--base-path` to point to a writable managed location such as `C:\ProgramData\Chatty-EDU\data`.

## Data directories and backup
All runtime state is stored under the base path:
- `config/` settings, UI state, and Bookkeeper memory files
- `config/bookkeeper/` local cold logs plus `memory_jogger.txt`
- `homework/outgoing/` teacher-authored pack Markdown
- `homework/assigned/` homework packs
- `homework/completed/` student submissions
- `homework/marking/` marking exports
- `homework/printables/` student printables
- `homework/rubrics/` teacher rubrics
- `revision/notes/` student revision notes and progress
- `revision/past_papers/` imported past papers and teacher revision materials
- `models/` GGUF model files

Backups are file-based: copy the entire base directory to back up or migrate a deployment.

## Models
- Place approved GGUF files under `<base>/models/`.
- On startup, the largest valid GGUF is auto-assigned to the main AI role.
- If 2 or more valid GGUFs are present, the smallest valid GGUF is auto-assigned to the Bookkeeper role.
- If only 1 model is present, the main AI uses it and Bookkeeper falls back to keyword-only summary mode.
- If no model is present, the app stays friendly and prompts the user to drop a GGUF into the models folder to get started.
- You can still inspect or override the selection in the GUI via File -> Models.

## Teacher controls and device posture
Teacher controls are gated by a local PIN or secret stored in `config/settings.json`.
- Default PIN: `0000` and should be changed immediately.
- This is not a strong security boundary. Anyone with file access can still edit local settings.

Recommended controls:
- Separate Windows accounts where appropriate
- Restrict access to the base path
- Use disk encryption and standard endpoint protections

## Transparency and trust
- The ECG widget is intentionally visible in the UI so people in the room can see when Chatty-EDU is active.
- It is not a replacement for firewall or endpoint controls, but it supports trust in the zero-calls-home design by avoiding a silent black box feel.
- For family-facing or school-review deployments, it is reasonable to explain the ECG widget as a local transparency cue: model work causes visible activity, while Chatty-EDU itself still operates without cloud endpoints in normal use.

## Troubleshooting
- No model selected on first launch: confirm the models folder contains at least one valid GGUF, then refresh or relaunch. Single-model deployments are valid; Bookkeeper will simply stay in keyword-only mode.
- No packs visible: confirm the correct base path and that packs are in `homework/assigned/` or `homework/outgoing/`.
- Use the Diagnostics tab or File -> Copy Diagnostic report when preparing a support request.
