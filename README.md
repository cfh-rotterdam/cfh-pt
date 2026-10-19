# CFH PT

Coach dashboard for CFH personal training: https://cfh-rotterdam.github.io/cfh-pt/

Built the same way as [CFH Events](https://github.com/cfh-rotterdam/cfh-events): one `index.html`, no build step, served by GitHub Pages.

- Data lives in Supabase (project `cfh-pt`): tables `clients`, `blocks`, `documents`. Nothing about clients is stored in this repo.
- Sign-in with an email link. Only emails in `app_users` can read or write (Row Level Security).
- Views: Roster (queue, blocks in progress, all clients), Timeline, Documents. Click a client for the profile, edit it, or build the next block.
- Block builder: preview, save draft, download `.docx`, publish. Upload to Drive turns on when `GOOGLE_CLIENT_ID` is set in `index.html`.

## Setup (once)

1. **GitHub**: create the repo `cfh-rotterdam/cfh-pt`, add `index.html` and this README, then Settings → Pages → Deploy from branch `main`, folder `/ (root)`.
2. **Supabase** → Authentication → URL Configuration:
   - Site URL: `https://cfh-rotterdam.github.io/cfh-pt/`
   - Redirect URLs: add `https://cfh-rotterdam.github.io/cfh-pt/`
   Email sign-in links work after this step.
3. **Upload to Drive** (optional): create a Google Cloud OAuth client (Web), add the JavaScript origin `https://cfh-rotterdam.github.io`, enable the Google Drive API, add your account as a test user, then paste the client ID into `GOOGLE_CLIENT_ID` in `index.html`. Files go to the Personal Training folder (`DRIVE_FOLDER`).

## Access

Add a coach: `insert into app_users (email) values ('name@example.com');` in the Supabase SQL editor.
