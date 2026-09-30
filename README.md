# Mail Digest

Checks all your inboxes and condenses unread mail from the last 14 days into one page,
sorted into **Needs attention** (bills, security alerts, deadlines), **From people**, and
**Automated & newsletters** (grouped by sender). Inboxes are opened read-only, so nothing
gets marked as read.

## Install

```
pip install -r requirements.txt
```

## Add your accounts

Run this once per address:

```
python mail_digest.py add
```

| Provider | What you need |
|---|---|
| Gmail | An **app password**: https://myaccount.google.com/apppasswords (needs 2-Step Verification on) |
| Yahoo / AOL | An **app password**: Account Info → Account security → Generate app password |
| iCloud | An **app-specific password**: https://account.apple.com → Sign-In and Security |
| Outlook / Hotmail / Live | A Microsoft sign-in in your browser (one-time setup below) |

App passwords are saved in Windows Credential Manager, not in any file.

### Outlook setup (once)

Microsoft no longer accepts passwords for this kind of access, so the script signs in the
same way desktop mail apps do. That means registering a small app of your own:

1. Go to https://entra.microsoft.com → **App registrations** → **New registration**
   (sign in with your Outlook account; if it asks you to create a free directory, do that).
2. Name: `Mail Digest`. Supported account types: **Personal Microsoft accounts only**. Register.
3. Copy the **Application (client) ID**.
4. Go to **Authentication** → **Advanced settings** → **Allow public client flows** → **Yes** → Save.

When `add` asks for the client ID, paste it in. It then shows a code; open the link,
enter the code, and approve. You only have to do this once per Outlook address.

## Run it

```
python mail_digest.py
```

This writes `digest.html` next to the script and opens it.

Options: `--days 30` looks further back. `--all` includes Gmail's Promotions/Social tabs.
`list` shows your accounts and `remove EMAIL` removes one.
