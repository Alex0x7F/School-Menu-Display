# 🍽️ Example School — Menu Management System

A fully self-contained, web-based school lunch menu management system built with pure HTML, CSS and JavaScript. No server, no database, no install required — just three HTML files.

---

## 🌐 Live Demo

> Upload to GitHub Pages and your URL will be:
> `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`

---

## 📋 What It Does

This system solves a common problem in school catering: the kitchen manager types up the menu, it goes to someone to format, then someone else to export or publish — and any single change triggers the whole chain again.

**This eliminates that entirely.**

The kitchen manager edits the menu directly in a browser. Changes are live immediately. No approvals, no exports, no PDFs, no chain of people.

### The three-week rotating cycle

Menus are organised into a three-week cycle (Week 1, Week 2, Week 3) that repeats continuously throughout the school year. The system automatically works out which week of the cycle any given date falls on — nobody has to manually say "this is week 2". The cycle start date is configurable by an admin.

---

## 📁 Files

| File | Purpose |
|------|---------|
| `index.html` | Landing page — links to the display and editor |
| `display.html` | Public-facing menu display — for screens, signage, parents |
| `admin.html` | Kitchen manager login and menu editor |
| `README.md` | This file |

---

## 🚀 How to Deploy on GitHub Pages

1. **Download** all files from this repository (or click the green *Code* button → *Download ZIP*)
2. **Create a new GitHub repository** (public)
3. **Upload** `index.html`, `display.html`, `admin.html`, and `README.md` to the root of the repository
4. Go to **Settings → Pages**
5. Under *Source*, select **Deploy from a branch** → choose `main` → folder `/root`
6. Click **Save**
7. After a minute or two, your site will be live at `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`

That's it. No build step, no npm install, no configuration.

---

## 🖥️ How to Self-Host on a Local / Intranet Server

Because this is plain HTML, it runs on any web server:

**Option A — Windows IIS**
1. Copy the three HTML files into `C:\inetpub\wwwroot\menu\`
2. Browse to `http://localhost/menu/`

**Option B — Any machine with Python installed**
```bash
# Navigate to the folder containing the files, then:
python -m http.server 8080
# Open http://localhost:8080 in a browser
```

**Option C — XAMPP / WAMP / LAMP**
Copy the files into the `htdocs` (or `www`) folder and browse to `http://localhost/menu/`

**Option D — Raspberry Pi or similar**
Install nginx or Apache, copy files to the web root, and access via the Pi's IP address on your local network — ideal for a permanent TV screen in the canteen.

---

## 🔐 Login Credentials

### Kitchen Manager
| Username | Password |
|----------|----------|
| `kitchen` | `menu2026` |

Can edit all menus across the three-week cycle. Changes are saved and go live on the display page immediately.

### Administrator
| Username | Password |
|----------|----------|
| `admin` | `admin2026` |

Same as above, plus access to the **Settings** tab:
- Configure the cycle start date
- Reset all menus to sample data
- Export all menu data as a JSON file

> **Note:** These are demonstration credentials stored in the HTML file itself. For a real deployment, open `admin.html` in a text editor and change the passwords in the `USERS` object near the top of the `<script>` section.

---

## 📅 Menu Pages Explained

### `index.html` — Landing Page
The starting point. Shows which week of the cycle today falls on, with buttons to go to the display or the editor.

### `display.html` — Today's Menu Display
- Automatically shows the correct menu for today
- Navigate to yesterday, tomorrow, or any date using the controls
- Colour-coded dietary tags: **V** (Vegetarian), **Vg** (Vegan), **H** (Halal), **GF** (Gluten Free)
- Child-friendly design with a decorative animated food border — suitable for classroom or canteen TV screens
- **Auto-refreshes every 5 minutes** — ideal for digital signage, just open the page full-screen on a TV
- Correctly shows "No school lunch" on weekends

### `admin.html` — Menu Editor
- Login screen with role-based access
- Three tabs, one per week of the cycle
- Each day shows fields for: two hot meal options, two cold/jacket options, pudding, and dietary/allergen notes
- Every meal option has a dietary tag selector (None / V / Vg / Halal / GF)
- Save individual days or use "Save All Changes" to save everything at once
- All changes are reflected on `display.html` immediately — no export step

---

## 🍱 Sample Menu Data

The system comes pre-loaded with a full three-week spring/summer primary school menu cycle, including:

- Hot and cold meal choices for every day
- Vegetarian and vegan options clearly labelled
- Dessert/pudding for each day
- Allergen and halal notes throughout

This data can be edited freely via the admin interface, or reset to defaults at any time from the Settings tab.

---

## 💾 How Data Is Stored

All menu data is stored in the browser's `localStorage`. This means:

- **No database required** — everything lives in the browser
- **Changes persist** across page refreshes and browser restarts
- **On a shared intranet PC** (e.g. the kitchen manager's computer), changes made in `admin.html` will appear on `display.html` when that page next loads or auto-refreshes
- **On GitHub Pages**, the display and admin pages run in the same browser origin, so data saved in admin is visible in display on the same device

> For a multi-device intranet setup (e.g. the kitchen manager edits on one PC, and a TV screen elsewhere shows the display), both pages need to be served from the same local web server and opened on the **same machine**, or you need a shared network drive solution. For most small school use cases, a single PC or a Raspberry Pi serving both is sufficient.

---

## 🎨 Design

- Colour scheme: school green (`#4a7c3f`) and warm orange (`#e8821a`)
- Fonts: Fredoka One (headings) + Nunito (body) — loaded from Google Fonts
- Child-friendly animated food emoji border on the display page
- Fully responsive — works on desktop, tablet, and mobile
- Calm, practical interface for the admin side — no clutter

---

## 🛠️ Customisation

Everything is in plain HTML/CSS/JS — open any file in a text editor to change it.

| What to change | Where to find it |
|----------------|-----------------|
| School name | Search for `Example School` in all three files |
| Colours | CSS `:root` variables at the top of each file |
| Login passwords | `USERS` object in `admin.html` `<script>` section |
| Cycle start date | Settings tab in `admin.html` (admin login), or `CYCLE_START` constant in `display.html` |
| Default menu content | `DEFAULT_MENU` object in both `display.html` and `admin.html` |
| Auto-refresh interval | `setInterval` near the bottom of `display.html` (currently 5 minutes) |

---

## 📄 Licence

MIT — free to use, modify, and redistribute for any purpose.

---

*Built with pure HTML, CSS, and JavaScript. No frameworks, no dependencies, no build tools.*
