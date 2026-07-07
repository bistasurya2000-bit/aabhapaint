# 🎨 Aabha Joshi — Art Portfolio Website

A complete, free-to-host website for selling original paintings, blogging, and announcing exhibitions & auctions. Built as a static site (plain HTML/CSS/JS) so it runs on **GitHub Pages at zero cost** — no server, no database, nothing to maintain.

**Live domain:** http://aabhajoshi.com.np/

---

## What's inside

| File / folder | Purpose |
|---|---|
| `index.html` | Home page — hero, featured paintings, latest blog posts |
| `gallery.html` | All paintings with filters (oil / acrylic / watercolour, available / sold) and Buy buttons |
| `blog.html` + `post.html` | Blog list and single-post pages |
| `exhibitions.html` | Upcoming & past exhibitions/auctions, with which paintings are on auction |
| `about.html` | About the artist + contact info |
| `admin.html` | 🔑 **Your private manager** — add / edit / delete paintings, mark sold, no coding needed |
| `data/paintings.json` | Your paintings "database" |
| `data/posts.json` | Your blog posts |
| `data/exhibitions.json` | Your exhibitions & auctions |
| `js/config.js` | ⚙️ Your email, phone, Formspree ID, socials — **edit this first!** |
| `images/paintings/` | Painting photos (samples included — replace with real photos) |

---

## 🚀 Setup (one time, ~20 minutes)

### 1. Put your details in `js/config.js`
Open `js/config.js` in any text editor and fill in:
- `email` — your personal email (shown to buyers)
- `phone` — your phone number
- `formspreeId` — see step 2
- `instagram` / `facebook` — optional links

### 2. Set up the Buy form (Formspree — free)
1. Go to **https://formspree.io** and sign up free with your email.
2. Click **New form**, name it "Painting enquiries", set the recipient to your email.
3. Copy the form ID from its endpoint URL — `https://formspree.io/f/`**`mqkrznab`** ← that last part.
4. Paste it into `formspreeId` in `js/config.js`.

*(If you skip this, the Buy button still works — it opens the buyer's email app instead.)*

### 3. Upload to GitHub
1. Create a free account at **https://github.com**.
2. Click **＋ → New repository**, name it e.g. `aabhajoshi-art`, keep it **Public**, create.
3. Click **uploading an existing file**, drag **all** files & folders from this project in, and **Commit changes**.

### 4. Turn on GitHub Pages (the free hosting)
1. In your repo: **Settings → Pages**.
2. Under *Source*, choose **Deploy from a branch**, branch **main**, folder **/ (root)**, Save.
3. After ~2 minutes your site is live at `https://YOUR-USERNAME.github.io/aabhajoshi-art/`.

### 5. Connect your domain (aabhajoshi.com.np)
1. Still in **Settings → Pages**, under *Custom domain*, enter `aabhajoshi.com.np` and Save. (The `CNAME` file in this project already contains it.)
2. At your **domain registrar** (where you registered aabhajoshi.com.np — for `.com.np` this is managed via https://register.com.np), set these DNS records:

   | Type | Host | Value |
   |---|---|---|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |
   | CNAME | www | YOUR-USERNAME.github.io |

3. Wait for DNS to update (minutes to a few hours), then tick **Enforce HTTPS** in Settings → Pages.

---

## 🖼️ Everyday tasks

### Add a new painting
1. Take a good photo (JPG, ideally under 1 MB).
2. On GitHub: open `images/paintings` → **Add file → Upload files** → commit.
3. Open **yoursite.com/admin.html** → **＋ Add New Painting** → fill the form (use the same image filename) → Save → **⬇ Download paintings.json**.
4. On GitHub: open `data/paintings.json` → ✏️ pencil icon → select-all, paste the downloaded file's contents → **Commit changes**.
5. Refresh your site — done!

### Mark a painting as sold / delete one
Same as above: open `admin.html`, click **Mark Sold** or **Delete**, download the JSON, replace it on GitHub.

### Write a blog post
Edit `data/posts.json` on GitHub (✏️ pencil). Copy an existing post block and change it:
```json
{
  "id": "my-new-post",
  "title": "My Post Title",
  "category": "Painting Tips",
  "date": "2026-08-01",
  "excerpt": "One or two sentences shown on the blog list.",
  "content": "First paragraph.\n\nSecond paragraph.\n\nThird paragraph."
}
```
Use `\n\n` between paragraphs. Commit — the post appears immediately.

### Announce an exhibition / auction
Edit `data/exhibitions.json` the same way:
```json
{
  "id": "e3",
  "name": "Exhibition Name",
  "venue": "Gallery Name",
  "city": "Kathmandu",
  "date": "2026-12-05",
  "description": "A few sentences about the event.",
  "paintings": ["p1", "p6"]
}
```
The `paintings` list uses painting IDs from `paintings.json` — those pieces get a gold **Auction** badge in the gallery automatically. You can also type the auction name into a painting's "Auction" field in `admin.html`.

---

## 🔍 Testing locally (optional)
Browsers block `fetch()` from files opened by double-click. To preview on your computer:
```
cd aabhajoshi-art
python -m http.server 8000
```
Then open http://localhost:8000

## Notes
- `admin.html` is not linked from the site and is marked `noindex`, but it is technically public. It contains no secrets — it only edits a file you already publish — so this is safe. Bookmark it for yourself.
- The sample painting images are computer-generated placeholders. Replace them with photos of your real work (keep the same filenames, or update them in the admin page).
