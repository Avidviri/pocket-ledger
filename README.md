# Pocket Ledger

A personal money tracker for iPhone. Split your money into wallets, log spending by category, and see how it changes over time.

Open the GitHub Pages link in Safari, then tap Share, then Add to Home Screen.

Your data stays on your phone. Nothing you enter is sent to this repository. Use Settings > Backup > Export to keep a copy.

## Read bank emails: setup

Pocket Ledger can read your bank's transaction emails from Gmail and turn them into entries you confirm. Your emails go straight from Google to your phone. They're never sent to this repository or anywhere else.

You do this once, on a computer or your phone, signed in to the Gmail account that gets your bank emails.

1. Open [console.cloud.google.com](https://console.cloud.google.com). Create a new project named **Pocket Ledger**.
2. Go to **APIs & Services → Library**, search for **Gmail API**, and click **Enable**.
3. Go to **Google Auth Platform** and click **Get started**.
   - App name: **Pocket Ledger**. Support email: your Gmail.
   - Audience: **External**. Contact email: your Gmail. Agree to the policy, then click **Create**.
4. In **Audience**, under **Test users**, click **Add users** and add your own Gmail address. Leave the app in **Testing**.
5. In **Data Access**, click **Add or remove scopes**, tick `.../auth/gmail.readonly` (Gmail API, read-only), then click **Update** and **Save**.
6. In **Clients**, click **Create client**.
   - Application type: **Web application**. Name: **Pocket Ledger**.
   - Authorized JavaScript origins: `https://avidviri.github.io`
   - Authorized redirect URIs: `https://avidviri.github.io/pocket-ledger/`
   - Click **Create**, then copy the **Client ID**. It ends in `.apps.googleusercontent.com`.
7. In Pocket Ledger (opened from the home-screen icon), go to **Settings → Bank emails** and paste the Client ID.
8. On **Home**, tap **Check bank emails**.
   - Google will say it hasn't verified the app. That's expected, because it's your own private app. Tap **Continue**, then allow reading your email.
   - Pick which senders are your bank. Your new transactions then appear for you to review.

The Client ID isn't a password. It only lets your own Google account sign in to your own copy of the app.
