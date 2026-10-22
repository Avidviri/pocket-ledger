# Pocket Ledger

A personal money tracker for iPhone. Split your money into wallets, log spending by category, and see how it changes over time.

Open the GitHub Pages link in Safari, then tap Share, then Add to Home Screen.

Your data stays on your phone. Nothing you enter is sent to this repository. Use Settings > Backup > Export to keep a copy.

## Read bank emails: setup

Pocket Ledger can read your bank's transaction emails from Gmail and turn them into entries you confirm. Your emails go straight from Google to your phone. They're never sent to this repository or anywhere else.

You do this once, on a computer or your phone, signed in to the Gmail account that gets your bank emails.

1. Open [console.cloud.google.com](https://console.cloud.google.com). Create a new project named **Pocket Ledger**.
2. Go to **APIs & Services → Library**, search for **Gmail API**, and click **Enable**. To show investments from your Google Sheet as well, also search for **Google Sheets API** and click **Enable**.
3. Go to **Google Auth Platform** and click **Get started**.
   - App name: **Pocket Ledger**. Support email: your Gmail.
   - Audience: **External**. Contact email: your Gmail. Agree to the policy, then click **Create**.
4. In **Audience**, under **Test users**, click **Add users** and add your own Gmail address. Leave the app in **Testing**.
5. In **Data Access**, click **Add or remove scopes**, tick `.../auth/gmail.readonly` (Gmail API, read-only). For investments, also tick `.../auth/spreadsheets.readonly` (Google Sheets API, read-only). Then click **Update** and **Save**.
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

## Investments from your Google Sheet

Pocket Ledger can show your investment wallet at today's market value, read from your own portfolio sheet. The wallet's balance still tracks the cash you put in, so you see both, plus your gain or loss. Net worth on the Money tab uses the market value.

1. Do the Google setup above, including the **Google Sheets API** and the `spreadsheets.readonly` scope.
2. In Pocket Ledger, go to **Settings → Investments**:
   - **Investment wallet:** the wallet you move your investing cash into.
   - **Google Sheet:** paste your portfolio sheet's link.
   - **Cells to read:** a range with a **Total value** heading and the number below it. The default, `'📊 dashboard'!B6:K8`, matches the summary row of the portfolio sheet. **Total cost** is read too if it's in the range.
3. Tap **Refresh now** and sign in with the Google account that can open the sheet.

After that, the market value refreshes by itself when you open the app (at most once an hour). You can also tap **Refresh** on the Money tab at any time. Each reading is saved, so the wallet's chart of market value against cash invested builds up over time.
