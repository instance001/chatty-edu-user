# Chatty-EDU User Release

This repository contains a prebuilt Windows app and bundled sample content. No model weights are included.
For source code and build instructions, see https://github.com/instance001/chatty-edu.

## Quick start (Windows)
1. Download or clone this repo and unzip it.
2. Double-click `chatty-edu.exe`.
3. Data is stored in the `data/` folder next to the exe.
4. Add a GGUF model to `data/models/`, then select it in the app via File -> Models.

## Models (BYO)
- Chatty-EDU does not include model weights.
- Put your approved GGUF in `data/models/` (example: `qwen2.5-1.5b-instruct-q4_k_m.gguf`).
- Model guidance and licenses live in `resources/models/`.

## Sample resources
- Sample packs and a dummy attachment live in `resources/`.
- To use the sample bundle, import `resources/homework_pack_sample_bundle.json` and copy `resources/attachments/` if needed.

## Manuals
- Teacher guide: `teacher_user_manual.md`
- Student guide: `student_user_manual.md`

## Source code
- https://github.com/instance001/chatty-edu

## License
- Licensed under the GNU Affero General Public License v3.0.
- See `LICENSE` for the full text.

## Notes
- Offline by default; no cloud dependency.
- If you want a clean reset, delete `data/config/settings.json` and relaunch.
