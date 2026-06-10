# One Year of Us

A single-file, mobile-first anniversary website. No build step, no backend, no
frameworks: just `index.html` and a `photos/` folder. Open `index.html` in a
browser and it works.

## Editing your content

Everything editable lives in one place: the `CONFIG` object at the top of the
`<script>` tag near the bottom of `index.html` (look for the banner that says
`EDIT ZONE`). It holds:

- `names` and the cover text
- `pier.timestamp`: the exact moment the counter counts from
- `vladPath` / `macyPath`: the two childhood timelines
- `meeting`: the how-we-met cards
- `yearMoments`: the polaroid wall (`caption` is the front, `note` is the
  handwritten back you see when you tap to flip)
- `starMemories` and `secretStar`: what the tappable stars over the pier say
- `boxNotes`: the slips that fly out of the memory box
- `ending`: the closing lines and sign-off

Adding a moment is adding one `{ ... }` block to a list. Nothing below the
`END OF EDIT ZONE` banner needs to be touched.

## Photos

Drop images into the `photos/` folder using the filenames listed in
`photos/README.txt`. Until a file exists, that spot shows a botanical
placeholder with the expected filename on it, so the page looks finished even
while photos are missing. Resize to roughly 1200px on the long side so it
loads fast on a phone.

## Previewing locally

From this folder:

```
python3 -m http.server 8000
```

Then open http://localhost:8000 on your computer, or visit your computer's
local IP from your phone on the same wifi.

## Deploying to GitHub Pages (free)

1. Create a GitHub account if you do not have one, then create a new
   repository at github.com/new. Make it **Public** (GitHub Pages is free for
   public repos only). Pick an unguessable name like `our-first-chapter-vm`
   rather than `anniversary`, since anyone with the URL can view the site.
   Do not initialize it with a README.
2. From this folder, push the existing git history:

   ```
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
   git push -u origin main
   ```

3. On the repository page, go to **Settings** > **Pages** (left sidebar).
   Under "Build and deployment" choose **Deploy from a branch**, branch
   `main`, folder `/ (root)`, and click **Save**.
4. Wait a minute or two. The page at the top of the Pages settings will show
   the live URL: `https://YOUR-USERNAME.github.io/YOUR-REPO/`.
5. Open that URL on your phone and scroll the whole thing to confirm.
6. Updating later is just: edit files, then

   ```
   git add -p
   git commit -m "Update content"
   git push
   ```

   Pages redeploys automatically within a minute.

## Writing the NFC tag

1. Install the free **NFC Tools** app (iOS or Android).
2. Buy NTAG213/215 stickers (any cheap pack works; a URL this size fits
   easily on NTAG213).
3. In NFC Tools: **Write** > **Add a record** > **URL**, paste the GitHub
   Pages URL, then **Write** and hold the tag to the top of the phone.
4. Optional: in NFC Tools, use **Other** > **Lock tag** so it cannot be
   overwritten. This is permanent.
5. Tuck the sticker behind the photo in the picture frame and test the tap
   with her phone model: iPhones read NFC near the top edge of the phone,
   most Androids near the middle of the back.

## Privacy notes

- The repo is public, so the photos and text in it are public to anyone who
  finds the repo or URL. The page includes `<meta name="robots" content="noindex">`
  so search engines are asked not to index it, and an unguessable repo name
  keeps casual visitors away. Avoid last names, addresses, and anything you
  would not want a stranger seeing.
- If you ever want it fully private, GitHub Pages on a private repo requires
  a paid plan; alternatives like Cloudflare Pages allow private repos on
  their free tier and deploy the same folder unchanged.
