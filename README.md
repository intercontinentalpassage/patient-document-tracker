# Patient Document Tracker

A single-file offline tool for a hospital registration department: `patient-document-tracker.html`.
It runs from the local file. There is no server, and nothing is uploaded anywhere.

## About this repository
- It is **public** so that the maintainer's assistant (Claude) can read the code. Treat everything in it as visible to everyone.
- It contains no patient data and no usable passwords. The starting passwords of the built-in accounts are stored
  only as salted hashes, and are given to the maintainer separately.
- Never commit patient files (Excel exports, screenshots showing patient data), passwords or tokens.
  `.gitignore` blocks Excel and CSV files and files with password-like names.
- No open-source license is granted. This is an internal tool.
- The file links to visa specimen images on Google Drive, and loads fonts and two libraries
  (Excel reader, charts) from the internet.

## Running it
1. Open `patient-document-tracker.html` in Chrome or Edge.
2. It needs internet access once per session for the fonts and the two libraries. If the network blocks them,
   uploading and charts will not work.
3. A fresh browser starts with two accounts, `admin` and `registration`. Their one-time passwords are given to the
   maintainer separately. Each must set its own password at first sign-in.

## Where the data lives
Tasks, users, roles and wording edits are stored inside each browser on each computer.
- Another computer, another browser, or a web address instead of the local file starts empty.
  (Chrome and Edge treat local files as one place; Firefox keeps each file separate.)
- Clearing the browser's site data deletes it. There is no export for tasks and users yet.
- The Status check wording can be exported and imported (Settings, Status check text).

## What is in it
- Task pool, Dashboard (Document completion, Insurance coverage), Stats, Upload data, Status check tab.
- Patient Status Check: public from the login screen (no sign-in) and a tab once signed in. English and Thai.
- Admin Settings: users, roles and access, and the wording of the Status check.

## Applying a patch from Claude
Claude cannot push to GitHub. Each change arrives as one patch file with the commands to apply it:

```
git status
git am --3way path\to\the-patch-file.patch
```
Open `patient-document-tracker.html` and test. Then, if the patch says to tag a version:

```
git tag v1.1.0
git push origin main --tags
```
If `git am` fails, run `git am --abort`, then `git log --oneline -3`, and give that output to Claude. Do not force it.

## Limits to remember
- Access control (sign-in, roles) runs in the browser only. It keeps screens and actions away from honest users
  but is not protection against someone who knows browser developer tools.
- Sharing data across computers needs a server database (Supabase or self-hosted). That is a later step.
