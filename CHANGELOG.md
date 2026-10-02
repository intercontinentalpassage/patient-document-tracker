# Changelog

## v1.0.1 - first public version
- The starting admin account now uses a one-time random password stored only as a salted hash. The old
  default password and its hash were removed from the code. Computers that already have an admin account are unaffected.
- Documentation for the public repository and for receiving changes as patches.
- Repository history starts here (a fresh history, so the old default never appears in it).

## v1.0.0 - features
- Patient Status Check (visa eligibility, G1/G2/G3), English and Thai. Public from the login screen,
  and a "Status check" tab for every signed-in user. Results match the original checker.
- Dashboard: Insurance coverage shows its cards (with zeros) when no insurance data exists,
  the same way Document completion does.
- Admin Settings (Admin only): create users, set roles, and choose what each role can access
  (Task pool, Dashboard views, Stats, Uploads, Work tasks). Users are deactivated, not deleted.
  Passwords are salted and hashed; a temporary password must be changed at first sign-in.
  The last active Admin cannot be demoted or deactivated.
- Themed role dropdown in Add/Edit user (no default role, so an Admin is never created by accident).
- Status check wording editor (Settings): edit any English or Thai wording, search, reset, save,
  export and import. Only changed text is stored. Rules, visa codes and nationality names are fixed.
- Built-in accounts: `admin` (first Admin) and `registration`. The `registration` account uses the
  built-in Registration role: Task pool, Work tasks, Dashboard (Document completion), Stats and both uploads.
  A `registration` account made by an earlier file moves to this role once.
- Fixes: database upgrades no longer delete uploaded insurance records; the mobile menu opens again in the
  signed-in app; the Status check toolbar no longer covers the account menu.

### Known limits
- Data is stored per browser, per computer. No export of tasks or users yet.
- Access control is enforced in the browser only.
- Needs internet access for fonts and two libraries (cdnjs).
