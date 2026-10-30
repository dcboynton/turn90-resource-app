# Turn90 Resource Finder

A free, phone-friendly web app that helps people coming home from incarceration find housing, jobs, health care, and other help in their South Carolina county. It also points people to Turn90's own programs (First Shift and Reentry Navigation).

Live site: https://dcboynton.github.io/turn90-resource-app/

## What's in this repo

There are only two files that matter:

- **index.html** is the app itself: how it looks and how it works. You will rarely need to change this.
- **resources.json** is the data: every organization, with its phone number, address, categories, counties, and so on. **This is the file you'll update most often.**

The master spreadsheet (Community_Org_Database) is where the data is really maintained. It is intentionally **not** in this repo, because this repo is public. Keep it in Turn90's shared drive.

## How to update the resources (the most common task)

1. **Edit the master spreadsheet.** Add, change, or remove organizations as needed. Save it.
2. **Turn the spreadsheet into a new resources.json.** Open a chat with Claude, attach the updated spreadsheet and the current resources.json (download it from this repo by clicking the file, then the download icon), and say something like:
   > "Rebuild resources.json from this spreadsheet in the same format as the attached current version. Check for blank or duplicate Resource IDs and tell me what changed compared to the old file."
   Claude will send back a new resources.json and a list of what was added, removed, or changed. Skim that list to make sure it matches what you meant to do.
3. **Upload the new file to GitHub.** On the main page of this repo, click **Add file, then Upload files**. Drag in the new resources.json (same name as the old one, so it replaces it), then click **Commit changes**.
4. **Wait a minute or two,** then open the live site on your phone. The "Last updated" date on the front screen should show today's date (it comes from the date the spreadsheet was last saved). If you still see old data, refresh the page or open it in a private/incognito window, because phones sometimes hold on to the old version.

## Rules for the spreadsheet (so nothing breaks)

- **Resource ID:** every row needs its own unique number. Never reuse an ID, and don't change an existing one. People's saved resources are remembered by ID, so changing it would make their saved item disappear or point to the wrong organization. Names can change freely, and IDs are what keep things stable.
- **Turn90 Refers:** enter Yes for organizations where people must be referred through Turn90, and No for everything else. For "Yes" rows, the app hides the organization's own phone and website and shows a "Call Turn90 to be referred" button instead.
- **Public information only.** Everything in resources.json is visible to anyone who visits the site. Don't put private notes, internal contact people, or anything sensitive in columns that feed the app. If you're not sure whether a column feeds the app, ask Claude to list which columns end up in the app.

## If you need to change the app itself

Changes to wording, colors, or how a screen works are edits to **index.html**. The easiest way is to ask Claude: attach the current index.html, describe the change, and upload the new version the same way as above (Add file, then Upload files, then Commit changes). For example, the program descriptions for First Shift and Reentry Navigation live in this file.

## Where things stand and what's still open

- **Hosting:** the site runs on GitHub Pages (Settings, then Pages, deploying from the main branch). It updates automatically within a couple of minutes after each upload.
- **Account:** this repo currently lives on a personal GitHub account. It would be wise to move it to a Turn90 organization account so the project doesn't depend on one person's login (Settings, then scroll to "Transfer ownership").
- **Analytics:** there is no visitor tracking yet. Ideas that were considered include Plausible and GoatCounter (simple, privacy-friendly counts of visits, counties picked, resources opened, and Call taps).
- **QR code:** once the final web address is settled, make a QR code that points to it for flyers and handouts.

## If something looks wrong

- **The page is blank or says it can't load resources:** resources.json is probably missing, misnamed, or has a formatting problem. Re-download the last working version from the repo's history (click the file, then History) and upload it again.
- **A phone number or address is wrong for one organization:** fix it in the spreadsheet and repeat the update steps above.
- **You're not sure what changed:** every upload is saved in the repo's history, so earlier versions can always be restored.
