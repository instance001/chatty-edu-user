# Chatty-EDU Student Manual

Audience: students with zero setup experience. Everything runs offline; no accounts.

## Quick start
1. Open `chatty-edu.exe`.
2. If your teacher gave you a GGUF model, place it in `data/models/`.
3. If your teacher gave you a homework pack, import it from Home -> "Import pack file", or copy it into `data/homework/assigned/`.
4. Pick your assignment on Home and read the instructions.
5. Under "Submit work", type your answers. Add attachments if your teacher asked for them.
6. Click "Export submission file" to save `submission_<assignment_id>_<your_id>.json` into `data/homework/completed/`.

## Homework
- Homework packs live in `data/homework/assigned/`. If you do not see yours, click "Rescan packs + submissions" on Home.
- Home shows your selected assignment, any worksheet or handout text included with it, and previews of text attachments when possible.
- The shared chat bar on Home and the main Chat tab both become homework-aware when an assignment is active. If you ask the assignment directly there, or rephrase one of the active homework questions, Chatty may still give you a hint instead of the final answer.
- Home includes a small live chat mirror at the bottom so you can keep working without leaving the page to see the latest reply.

## Chat
- Chat tab is the main full conversation view for general learning questions.
- `Chatty's thoughts` appears on the left and shows what Chatty can still remember in the current session. It clears when the app closes.
- `Memory jogger` appears on the right and shows short reminders from recent sessions. It stays across restarts.
- Sidebar entries may shorten inside the narrow panel, but you can hover them to read more.

## Revision
- Revision is separate from live homework. It uses work you have already submitted, plus any past papers your teacher imported.
- Revision can save your own notes or progress under `revision/notes/`.
- The Revision helper can explain more openly than live homework help because the work is already submitted, but it is still meant to teach and guide rather than just dump answers.
- Teacher-side scores or diagnostic labels are not shown in the student Revision view.

## File locations
- `data/homework/assigned/` - homework packs (`homework_pack_*.json`)
- `data/homework/completed/` - your exported submissions (`submission_*.json`)
- `data/revision/notes/` - your saved revision notes or progress
- `data/revision/past_papers/` - past papers your teacher imported for revision
- `data/models/` - local GGUF models
- `data/config/bookkeeper/` - local memory jogger and teacher-side log files

## Tips
- If the tutor says it cannot give the answer, ask for steps, a starting point, or the rule you need.
- If your homework refers to a worksheet, list, or table and you cannot see it, tell your teacher the pack may be missing the extra material.
- Teacher-only settings such as filters, games, and hints-only behavior are locked behind the Teacher PIN.
- The ECG widget in the top-right corner is a small machine-activity indicator for the local computer. It is there partly for transparency, so you, your teacher, or your family can see when Chatty-EDU is actively doing local work.

## Staying offline and safe
- Chatty-EDU works without internet; no cloud calls in normal use.
- Content filter (Janet) is on by default to block swears and mature topics.
- The app stores homework packs, submissions, and chat context locally on the machine you are using.
- `Chatty's thoughts` is session-only and clears on close. `Memory jogger` is a local cross-session reminder saved on the same machine.
- The ECG widget is part of that trust story: it is a visible local activity cue, not a hidden tracker, and it helps show that Chatty-EDU is doing work on your computer rather than calling home.
