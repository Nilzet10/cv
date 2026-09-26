# Taking the demo live: step by step

The whole site is one file, `index.html`. There's no build step and no server code, so it can go on any static host for free. Your only required cost is the domain, about $10–20 a year.

---

## Step 0: Show her the demo (today, free)

Pick whichever is easiest:

- **Fastest link to text her:** go to <https://app.netlify.com/drop> and drag a folder containing `index.html` onto the page. In about 10 seconds you get a link like `random-name.netlify.app` that works on her phone. Anonymous drops can expire, so sign up (free) to keep the link working.
- **On your laptop:** double-click `index.html` to open it in your browser.
- **From this GitHub repo:** in the repo, go to Settings → Pages → *Deploy from a branch* and pick the branch with `/ (root)`. The demo then lives at `https://nilzet10.github.io/cv/`, or at the custom domain once one is connected.

## Step 1: Decide these with her

These answers shape everything after this step:

- [ ] **Brand name.** One umbrella site ("Nidha's Events" in the demo), or keep the henna business as the main brand with the tea cart and DJ as sections?
- [ ] **Domain name.** See step 2.
- [ ] **Contact.** Which phone number (or WhatsApp) and email should go on the site? Should form requests go to one inbox?
- [ ] **Photos.** 15–30 of her best photos from the three Instagram accounts, ideally the originals rather than screenshots.
- [ ] **Real menu** for the tea cart, the henna styles she offers, and the DJ services.
- [ ] **Prices:** show "starting at" prices, or keep it "custom quote"?
- [ ] **Reviews:** 3–6 real ones (Google, Yelp, Instagram DMs), with permission to use first names.
- [ ] **Policies:** deposit, travel fee, how far ahead to book. These go in the FAQ.

## Step 2: Buy the domain (about $10–20 a year)

**Where to buy.** Use a registrar that doesn't pile on upsells:

| Registrar | Why | Approx. .com price |
|---|---|---|
| **Cloudflare Registrar** | Sells at cost with no markup, and includes free email forwarding and DNS | ~$10–11/yr |
| **Porkbun** | Cheap, simple, free WHOIS privacy | ~$11/yr |
| **Namecheap** | Popular and beginner-friendly | ~$11–16 first year, higher on renewal |

Check the **renewal** price, not just the first-year deal. GoDaddy and similar registrars often double the price in year two and push add-ons you don't need.

**Name ideas.** I couldn't check availability from here, so search these at the registrar:
`nidhasevents.com` · `nidhashenna.com` · `nidhashennadesigns.com` · `nidhahenna.com`

- Get a `.com` if you can. Short, easy to spell out loud, and no hyphens.
- **Buy it in her name, on her account**, with her email. She should own it, not you.
- Turn on **auto-renew** and **WHOIS privacy** (free at all three registrars above).
- Optional: buy the other names later and forward them to the main site.

## Step 3: Host the site (free)

For a site like this, any of these is free and fast:

| Host | Good for |
|---|---|
| **Netlify** | Easiest. Drag and drop to update, and built-in form handling on the free tier |
| **Cloudflare Pages** | Best fit if the domain is bought on Cloudflare |
| **GitHub Pages** | Free and works well if you're comfortable with Git |

Recommended setup: create a **new GitHub repo just for her site** (for example `nidhas-events-site`), copy `index.html` into it, and connect that repo to Netlify or Cloudflare Pages. Every `git push` then updates the live site automatically.

## Step 4: Point the domain at the host (DNS)

The host's dashboard walks you through this. Choose **"Add custom domain"** and it tells you exactly which records to add at the registrar. For reference:

- **Netlify / Cloudflare Pages:** usually a `CNAME` record for `www` pointing to your `*.netlify.app` or `*.pages.dev` address. If the domain is on Cloudflare, this is one click.
- **GitHub Pages:** four `A` records for the root domain (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`), plus a `CNAME` record for `www` pointing to `<username>.github.io`. Then tick **Enforce HTTPS**.

DNS changes take anywhere from a few minutes to a few hours. HTTPS (the padlock) is free and automatic on all three hosts.

## Step 5: Booking requests (set up)

**How it works now:** the form emails each request through **Web3Forms** (free, about 250 a month) to `nidha@nidhasevents.com`, a free Porkbun forward that currently delivers to Nilesh's Gmail. A free **Zapier** Zap ("Gmail: New Email Matching Search `subject:\"New booking request\"`" → "SMS by Zapier") texts the email's subject, which holds the key details. The confirmation screen offers WhatsApp or text to (848) 667-1264 as a faster lane, and if sending ever fails visitors get those options instead.

- **Change who receives requests:** edit the `nidha` forward in Porkbun. Nothing on the site changes.
- **Change who gets the texts:** in Zapier, edit the SMS step and connect the new number (the code goes to that phone). SMS by Zapier doesn't support T-Mobile numbers (including Mint, Metro, Google Fi).
- **Turn automatic sending off:** set `var WEB3FORMS_KEY = "";` in `index.html`; visitors then send their details themselves.

## Step 6: A professional email address (optional)

- **Free:** Cloudflare Email Routing (or the forwarding built into Porkbun or Namecheap) sends `hello@herdomain.com` to her existing Gmail.
- **Paid, about $7–8/user/month:** Google Workspace, if she wants to *send* from the new address with the full Gmail app. Zoho Mail has a free tier as a cheaper option.

## Step 7: Swap in the real content

Everything is in `index.html`. Search for these and replace them:

- **Photos:** the Gallery section shows her three Instagram profiles live, so new posts appear on the site automatically. Each account must stay public, with "Embeds" allowed in its Instagram settings (on by default). To add your own photos elsewhere on the page, put them in an `images/` folder and shrink each one to under ~300 KB first with <https://squoosh.app> (WebP format), or the site will load slowly on phones.
- **Reviews:** the reviews section was removed rather than show made-up quotes. Add it back with 3–6 real reviews (with permission) once she has them.
- **Email:** the site shows `nidha@nidhasevents.com`, a free Porkbun forward (Porkbun → Email Forwarding). Booking requests from the form go there too; change where it forwards in Porkbun, with nothing to change on the site.
- **Tea cart menu, henna styles, DJ genres, FAQ answers:** edit them to match what she actually offers.
- The `<head>` section: update the title and the description. The link preview image is `share.jpg`; swap in a real photo later if you like (keep it 1200×630 and under ~300 KB).

## Step 8: Help people find it

**Already on the site:** favicon and home-screen icons, `sitemap.xml`, `robots.txt`, a branded 404 page and a link-preview image (`share.jpg`).

**Google Search Console (free):** at <https://search.google.com/search-console>, add a **Domain** property for `nidhasevents.com`, copy the `google-site-verification=…` TXT record into Porkbun's DNS (Type TXT, Host blank), verify, then submit `https://nidhasevents.com/sitemap.xml` under Sitemaps.

**Visitor stats (free, no cookies):** sign up at <https://cloud.umami.is>, add the website `nidhasevents.com`, and paste its Website ID into `var UMAMI_WEBSITE_ID = "";` in `index.html`. Page views and taps on the booking, WhatsApp, text and Instagram buttons then show up in the Umami dashboard.

**QR code:** `print/booking-card-4x6.pdf` prints as a 4×6 photo; `print/qr-nidhasevents.png` is the plain code (it opens `nidhasevents.com/?ref=qr`).


1. **Google Business Profile** (free, and the biggest win for a local business): <https://business.google.com>. Claim or create a profile for each business, add the website link, photos and hours, and ask happy clients to leave Google reviews. This is what shows up for "henna artist near me".
2. **Instagram:** put the website link in all three bios. Link to sections directly, e.g. `herdomain.com/#dj` from the DJ account.
3. **Google Search Console** (<https://search.google.com/search-console>): verify the domain so Google indexes the site quickly.
4. **Wedding directories:** The Knot, WeddingWire, Zola and Yelp all take a website link.
5. **Analytics (optional):** Cloudflare Web Analytics or Netlify Analytics show visitor counts without cookie banners.

---

## What it costs

| Item | Cost |
|---|---|
| Domain | ~$10–20 / year |
| Hosting | $0 |
| HTTPS certificate | $0 |
| Booking form | $0 (free tiers) |
| Email forwarding | $0 |
| Google Workspace email (optional) | ~$7–8 / month |
| **Minimum total** | **~$10–20 / year** |

## Alternative: a website builder

If she wants to edit the site herself without touching code, use Wix, Squarespace or Shopify, at about $17–30/month. The DJ business already has a free Wix site (`litdjentertainment.wixsite.com`). Upgrading that plan and connecting the domain is another route. The trade-off is cost (about $200–350/year versus about $12) and less design control. This demo can still serve as the design reference.
