# Home Warranty Punch List

A shared phone app for photographing house damage, labeling it by room, and making a PDF report for the builder.

- Opens with a password screen. The password is **Bob**, and capitalization doesn't matter.
- Photos save to your Google Drive in **Warranty Punch List Photos**, with one subfolder per room.
- The item list saves to a Google Sheet called **Warranty Punch List**.
- Anyone with the link and the password can add items. Nobody needs a Google login.

## Step 1: Google backend (about 5 minutes)

1. Signed in to your Google account, go to **script.new**.
2. Delete what's there, paste in everything from `google-apps-script/Code.gs`, and name the project "Punch List".
3. In the function menu at the top, pick **setup** and click **Run**. Approve the access Google asks for. This creates the Sheet and the Drive folder, and their links appear in the log.
4. Click **Deploy → New deployment**, choose the type **Web app**, and set:
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Click **Deploy** and copy the **Web app URL**.

## Step 2: Connect the page

Open `public/config.js` and paste the Web app URL between the quotes.

## Step 3: Host on your domain (Vercel + GitHub)

1. Put this folder in a new GitHub repo.
2. In Vercel, click **Add New → Project**, import the repo, and keep the defaults (Framework: Other). Then deploy. No storage or environment variables are needed.
3. Under **Settings → Domains**, add `warranty.estimateconsultants.com` and follow the DNS instructions.

Share `https://warranty.estimateconsultants.com` along with the password. On iPhone, open it in Safari and tap **Share → Add to Home Screen**.

## If you change the script later

Go to **Deploy → Manage deployments**, click the pencil, set Version to **New version**, and deploy. This keeps the same URL.

## If photos don't show on other people's phones

Photos are shared as "anyone with the link can view," so the app can show them without a login. Only people with each photo's exact link can open it. If your Google Workspace blocks link sharing, open admin.google.com and go to **Apps → Google Workspace → Drive and Docs → Sharing settings**. Allow sharing outside the organization, at least by link.
