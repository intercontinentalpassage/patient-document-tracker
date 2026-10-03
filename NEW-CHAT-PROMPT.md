# Giving Claude a task (new chat)

Claude does not remember earlier chats. It reads this public repository instead, so push your latest work first.

## Before you start the chat
1. In this folder, `git status` must say "nothing to commit", and `git push origin main` must be done.
2. Open a new chat, paste the prompt below, and write the task where it says `[describe the change]`.
3. Optional but helpful: paste the output of `git log --oneline -3`.

## What Claude sends back
One patch file plus copy-paste commands. You run them in this folder:

```
git status
git am --3way path\to\the-patch-file.patch
```
Open `patient-document-tracker.html`, test it, then (if the patch says so) `git tag vX.Y.Z` and
`git push origin main --tags`.

If `git am` fails: `git am --abort`, then paste `git log --oneline -3` into the chat. Do not force it.

## Keep this file up to date
If a change alters how the app is built (new storage, new roles, new built-in accounts), update the
"What the app is" section in the prompt below in the same patch.

## The prompt

```
I'm Sai, a data analyst at MedPark Hospital in Bangkok. My Patient Document Tracker is a single-file
offline HTML/JS app in this public GitHub repo: https://github.com/intercontinentalpassage/patient-document-tracker
(branch main). I don't remember earlier chats and neither do you, so clone the repo, read
patient-document-tracker.html, README.md and CHANGELOG.md fully, and treat the repo as the source of truth.
Don't build anything until we have agreed a plan.

How I like to work: discuss requirements, then ask clarifying questions, then present a full plan,
then execute only after I confirm. No emojis (use inline SVG icons). One task at a time.

Delivery rules:
- You cannot push to GitHub. Work in a clone, make each logical change its own commit, and deliver ONE
  combined patch file (git format-patch) with present_files, plus the commands to apply it
  (git am --3way, test, tag, push) in one copy-paste code block. The patch must include the CHANGELOG.md
  update and the version number.
- Test before delivering: open the app in a headless browser and exercise the changed feature and the
  existing flows. Say plainly what you tested and what you did not.
- If a patch might not apply, don't guess: ask me for `git log --oneline -3`.
- Never hand-type large blocks of Thai text into the code. Copy exact text and verify it with a checksum.
- The repo is public. Never write passwords, tokens, patient data or real Excel files into any file,
  commit message or changelog. The starting passwords are given to me separately.

What the app is, so you can orient quickly:
- Registration department tool: tasks from Patient.xlsx exports, insurance dashboard from Microsoft Forms
  exports, Stats, Upload data, and a Patient Status Check (visa G1/G2/G3, English and Thai) that is public
  from the login screen and also a tab once signed in.
- Data lives in the browser's IndexedDB (database PatientDocTrackerDB, version 4: tasks, uploads,
  insuranceRecords, insuranceUploads, users, roles). Status check wording edits live in localStorage.
- Admin Settings: users, roles and permissions, and a Status check text editor (EN/TH).
  Built-in accounts: admin and registration (registration uses the built-in Registration role).
  Sign-in and access checks run in the browser only.
- Constraints to respect: the visa classification rules must stay exactly as in the original checker;
  nothing patient-related is stored outside the browser; keep the file self-contained.

Today I want to: [describe the change]
```
