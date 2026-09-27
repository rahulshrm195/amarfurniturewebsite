# amarfurniture.in

Website of **Amar Furniture, Nashik** (since 1991), part of Amar Group.

Three departments under one roof:

- **Wooden Furniture**: bespoke solid-wood furniture
- **Modular Kitchen & Home Interior**
- **Lathe Works**: turned pillars, balusters, balls and railings

Live site: https://amarfurniture.in · Hosted on GitHub Pages behind Cloudflare · Data and photos in Firebase

---

## Pages

| URL | Page |
|---|---|
| `/` | Home |
| `/wooden-furniture/` | Wooden Furniture |
| `/modular-kitchen-home-interior/` | Modular Kitchen & Home Interior |
| `/lathe-works/` | Lathe Works |
| `/shop/` | Shop Products (`?cat=` filters a category, `?p=ID` opens a product) |
| `/projects/` | Completed projects (`?id=ID` opens a project) |
| `/about/` | About Us |
| `/contact/` | Contact Us |
| `/staff/` | Staff panel (Google sign-in, not indexed) |

Each page has its own title, description, canonical URL, Open Graph tags and structured data (JSON-LD) for Google.

## Files

```
index.html + one folder per page (index.html inside each)
assets/site.css      all styles
assets/site.js       all logic: settings, Firebase, shop, projects, bookings, staff panel
assets/*.png/.svg    logo and app icons
favicon.ico          browser/Google favicon
og-image.jpg         preview image shown when the link is shared
sitemap.xml          list of pages for Google Search Console
robots.txt           blocks /staff/ from search engines
site.webmanifest     app icon/name info
404.html             "page not found"
CNAME                custom domain (amarfurniture.in)
```

The main settings are in the `CONFIG` block at the top of `assets/site.js`: phone, hours, open days, closed days, address, landmark, Google Maps links (share, directions, embed), Google rating, warranty text, modular brands, staff admin emails and the Firebase config.

## Updating the website

1. Unzip the new build.
2. Upload all files to this repo, replacing the old ones. Keep the folder structure.
3. Commit.
4. In Cloudflare, go to **Caching → Configuration → Purge Everything** so visitors get the new version.

CSS and JS links end in `?v=<build time>`, so browsers always load the latest files after an update.

## Address and map

The address appears on the Contact page (with a live map and a Get directions button), in the footer of every page, and in the workshop-visit booking confirmation. It is also in the structured data (street, PIN, map coordinates) that Google and AI assistants read.

**Keep the address in `CONFIG.address` exactly the same as on the Google Business Profile.** If the address ever changes, update it in the Business Profile, in `CONFIG` in `assets/site.js`, and in the structured data in every page's head.

## Staff panel (`/staff/`)

Sign in with an admin Google account listed in `CONFIG.adminEmails`.

| Tab | What it does |
|---|---|
| Leads | Call-back and workshop-visit bookings from the website. Status goes new → called → visit → quoted → won / lost. |
| Shop products | Ready-made wooden products shown on `/shop/` |
| Completed projects | Completed work, shown on each department page and on `/projects/` |
| Customer reviews | Reviews shown on the site |
| Site photos | Hero slides, category tiles, department, workshop and about photos |

Photos are compressed to WebP in the browser before upload.

## Photos and SEO: read before uploading

**You don't need to rename photo files before uploading.** The staff panel names every photo automatically:

| Upload | Saved as |
|---|---|
| Product "Teak Wood Carved Zula" | `website/products/<id>/teak-wood-carved-zula-nashik-<code>.webp` |
| Project "3BHK Modular Kitchen, Gangapur Road" | `website/projects/<id>/3bhk-modular-kitchen-gangapur-road-nashik-<code>.webp` |
| Site photo slot "Zula" | `website/site/zula-amar-furniture-nashik-<code>.webp` |

Photo alt text (what Google reads) is set automatically: the product name for products, and "*label* by Amar Furniture, Nashik" for site photos.

What actually helps Google rank us:

1. **Descriptive product names.** The name becomes the page title, the alt text and the file name. Use "Teak Wood Carved Zula", not "Zula 2".
2. **Good descriptions.** Include the wood type, size, finish, uses, and "Nashik".
3. **Real photos.** Our own workshop and installation photos rank better than stock images.
4. **Several photos per product.** This helps with Google Images results.

Photos uploaded before auto-naming was added keep their old names. To rename one, remove it in the staff panel and upload it again.

## Firebase

- **Firestore collections:** `website_products`, `website_projects`, `website_reviews`, `website_leads`, `website_settings` (photo slots live in `website_settings/images`)
- **Storage:** `website/{folder}/...`
- **Auth:** Google sign-in, restricted to admin emails by the security rules

Anyone can read public content and submit a booking lead. Only admins can edit content or read leads.

## Google Search Console

- The domain is verified through a Cloudflare DNS TXT record.
- The sitemap is submitted as `https://amarfurniture.in/sitemap.xml`.
- After adding a new page, re-submit the sitemap and use **URL Inspection → Request indexing**.

## Amar Group

- **Amar Furniture**: amarfurniture.in
- **SR Shoes**: srshoes.in (Nashik, next to Amar Furniture)
- **AppCentrik**: appcentrik.in

**Workshop:** Chh Sambhaji Nagar Naka, Vaishnavi Park, Nashik, Maharashtra 422003 (near Janardan Swami Math)
[Open in Google Maps](https://maps.app.goo.gl/jqzGrUPHQp7oLZap8) · +91 82754 07603 · Open all 7 days, 10 AM – 7 PM
