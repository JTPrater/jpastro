JP ASTROPHOTOGRAPHY — ready-to-upload site
=============================================

WHAT'S IN HERE
  index.html    the whole site
  support.js    required — index.html will not render without it
  images/       the photos

Keep all three together, and keep the same folder structure.

PUTTING IT ONLINE WITH GITHUB PAGES
  1. Make a repository on github.com. Keep it public — on the free
     plan, Pages only works from a public repo.

  2. Upload the CONTENTS of this folder to the top level of the repo,
     not the folder itself. When you are done the repo root should
     show index.html, support.js and images/ side by side.

     No git required: use "Add file > Upload files" on the repo page
     and drag them in from Explorer.

  3. Settings > Pages > Build and deployment.
     Source: "Deploy from a branch"
     Branch: main,  folder: / (root)
     Save.

  4. Give it a minute, then open the address GitHub shows you.

  It is a plain static site, so any static host works the same way if
  you ever move — Netlify, Cloudflare Pages, whatever. You do NOT need
  WordPress hosting.

YOUR CUSTOM DOMAIN — jp-astro.com
  Do these in this order. If you set the domain in GitHub before DNS is
  ready, the github.io address starts redirecting to a domain that does
  not resolve yet, and the site looks dead while you wait.

  1. At your domain registrar, point DNS at GitHub:

       apex domain          four A records
       (jp-astro.com)         185.199.108.153
                              185.199.109.153
                              185.199.110.153
                              185.199.111.153

       www subdomain        one CNAME record
       (www.jp-astro.com)     JTPrater.github.io

     Those are GitHub's current addresses; if the check never goes
     green, confirm them against GitHub's Pages documentation.

  2. Wait for DNS. Anywhere from a few minutes to a day. Check it with
     nslookup jp-astro.com — when it answers with the 185.199.x.x
     addresses above, you are ready for the next step.

  3. Settings > Pages > Custom domain. Enter jp-astro.com and Save.
     GitHub commits a file named CNAME into the repo. Leave it alone —
     if it ever gets deleted, the domain stops resolving.

  4. Once GitHub reports the domain verified, tick "Enforce HTTPS".

  5. Nothing to do here — index.html already points its og:image tag at
     https://jp-astro.com/images/m31-andromeda.png, which is what makes
     the Andromeda photo show up when someone shares a link on iMessage,
     Discord, X or Facebook.

     If the domain ever changes, update that tag to match. It has to be
     the full address; a relative path is unreliable there.

THE CONTACT FORM — ONE-TIME SETUP
  Messages are relayed to jtpraterap@gmail.com by formsubmit.co.
  The first time anyone submits the form, FormSubmit emails you a
  confirmation link. Click it once and every message after that lands
  in your inbox. Until you do, sends will fail.

  Test it yourself right after the site goes live so the activation is
  out of the way before real visitors arrive.

  To hide your email address from the page source, get a random token
  from formsubmit.co and swap it into the URL inside index.html:
    https://formsubmit.co/ajax/YOUR-TOKEN

EDITING
  Photos, dates, gear and exposure live in the PHOTOS list near the top
  of the script at the bottom of index.html. Copy a block to add a photo;
  drop the image file into images/ and point src at it.

  Photos are listed newest first.

NOTE ON SPEED
  The seven PNGs total about 48 MB, which is slow on phone data.
  Converting them to high-quality JPEGs would cut that to roughly 2 MB
  with no visible difference at web size.

  This is worth more on GitHub than on a drag-and-drop host: a repo
  keeps every version of every file forever, so each big PNG you upload
  stays in its history even after you replace or delete it.
