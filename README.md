# BUTUSIC – Illustration Exhibition Landing Page

A dark, card-based ("bento grid") landing page for a fictional online illustration exhibition called **BUTUSIC**. It is built with plain **HTML5 and CSS3** only: no frameworks, no JavaScript.

The design uses a black background with purple (`#9E54F4`) and lime (`#D6F156`) accents, rounded cards, and a two-column layout.

---

## Project Structure

```
project/
├── index.html          # Page markup (your HTML file)
├── landingpage.css     # All styling
└── image/
    ├── main-img-one.png
    ├── bitcoin-logo.png
    ├── Qr-code.png
    ├── side-img.png
    ├── location-img.png
    ├── star-tag.png
    ├── scan_me_qr_code.jpg
    ├── category.png
    ├── atm-card.png
    ├── user.png
    ├── growth.png
    ├── star.png
    ├── mail.png
    ├── happy-face.png
    ├── package-box.png
    ├── second-main-img.jpg
    └── star-img.png
```

> The HTML links to `landingpage.css`, so keep both files in the same folder and put the images in an `image/` folder next to them.

---

## How to Run

1. Put `index.html`, `landingpage.css` and the `image/` folder together.
2. Open `index.html` in a browser, or use VS Code's **Live Server** extension.
3. Use Live Server (or any local server) because the images use paths starting with `/image/...`, which only resolve correctly from a server root.

---

## Layout Overview

The whole page sits inside `<main>`, a CSS Grid with **two columns**:

| Section | Class | Contents |
|---|---|---|
| Left half | `.section-left` | Two inner columns (`.left` and `.right`) |
| Right half | `.section-right` | Top area (`.upper`) and bottom review card (`.lower`) |

### Left half
- **`.left` column**: hero image, then a bordered card with the BUTUSIC title, a divider line, a Bitcoin logo with the text "We accept more than just bitcoins", and a QR code.
- **`.right` column**: a circle illustration, a location and event info card, a row of four star tags, and a lime App Store card with a QR code and a discount message.

### Right half
- **`.upper`**: a grid of its own. The navigation menu (Categories, Payment, Authors, Sales, Reviews, Contacts) spans two rows on the left. A purple info card ("Only exclusive illustration / We do not sell works on stock") sits at the top right, with a large image below it.
- **`.lower`**: a white card with "ONLY THE BEST AUTHORS", the 4.97 rating, and a purple "BEST REVIEWS" button with a CSS-drawn arrow.

---

## Key Techniques Used

- **CSS Grid** for the main layout, with `grid-template-columns`, `grid-template-rows`, `gap`, and `grid-row: 1 / 3` for spanning.
- **Flexbox** for aligning icons with text, centring images, and the nav list.
- **Semantic HTML**: `<main>`, `<section>`, `<aside>`, `<article>`, `<nav>`, `<ul>`.
- **Rounded card design** using `border-radius` and `overflow: hidden`.
- **`object-fit`** (`contain` and `cover`) to control how images fill their boxes.
- **Linear gradients** on the purple card and button.
- **Pure-CSS arrow icon** made from a bordered 10×10 `span` rotated 45°.
- **CSS shapes**: a divider line made from a `span` with height, width and `border-radius`.
- **Contextual selectors** such as `.left-card .upper h1` and `.section-left .left .img img` to style repeated class names in different places.

---

## What I Learned

### 1. Thinking in grids
- A page can be a **grid inside a grid**: `main` is a grid, `.section-left` is a grid inside it, and `.section-right .upper` is another.
- `grid-template-rows: 40% 58%` and `grid-template-columns: 1fr 1.25fr` give precise control over how space is split.
- `grid-row: 1 / 3` lets one element (the nav) span two rows while others stack beside it.

### 2. Flexbox for small alignment jobs
- `display: flex; align-items: center; gap: ...` is the quickest way to put an icon next to text (nav items, location row, logo row).
- `justify-content: space-between` pushes items to opposite edges (the review card and the button label with its arrow).

### 3. Semantic HTML structure
- Using `section`, `aside`, `article` and `nav` makes the page easier to read than a pile of `div`s.
- Each visual "card" is naturally an `article`, and the sidebar menu is a `nav`.

### 4. Making images behave
- `object-fit: contain` keeps the whole image visible; `cover` fills the box and crops the overflow.
- Wrapping an image in a `div` with `overflow: hidden` and `border-radius` is the standard way to get rounded images.

### 5. Visual styling skills
- A limited palette (black, purple, lime, grey, white) makes the design look consistent.
- Gradients add depth to flat colours.
- Small text sizes (10–12px) with grey colour create a clear hierarchy against bold headings.

### 6. Building shapes without images
- Lines and arrows can be drawn with CSS (`border`, `transform: rotate()`, `height`, `background`) instead of extra image files.

### 7. Class name scope
- Reusing names like `.left`, `.right`, `.upper` and `.lower` in several places caused overlap, so I had to use **parent selectors** (`.section-left .left`) to target the right one.
- Lesson: use more unique names or a naming system like **BEM** (`card__title`, `card--purple`).

### 8. Mistakes I found (and how to fix them)

| Issue | Where | Fix |
|---|---|---|
| `width: 100;` has no unit, so it is ignored | `.appstore .app img` | Use `width: 100%;` |
| `<span class="line">` inside a `<ul>` is invalid HTML | Nav list | Use `<li class="divider" aria-hidden="true"></li>` or a `border-bottom` on an `li` |
| Typos in class names: `img-cirle`, `img-cicrle` | HTML and CSS | Rename to `img-circle` |
| `Poppins` is set but never loaded | CSS | Add the Google Fonts link in `<head>` |
| Mixed image paths: `/image/...` and `image/happy-face.png` | HTML | Use one consistent relative path (`image/...`) |
| Empty `alt=""` on meaningful images | HTML | Write descriptive alt text for accessibility |
| Page `<title>` is "Document" | `<head>` | Change to "BUTUSIC – Illustration Exhibition" |
| Several `<h1>` tags on one page | Hero and review card | Keep one `h1`; use `h2` or `h3` for the others |
| `.right .location` rule targets nothing useful | CSS | Remove unused rules |
| `margin: 0%` / `padding: 0%` | Reset | Use `0` (cleaner) |

### 9. Responsive design is a next step
- Fixed values like `width: 320px`, `height: 90px` and `main { width: 75% }` work on a desktop but will break on small screens.
- Next time I should add `@media` queries, for example stacking the two columns on tablets and phones, and use `min()`, `clamp()` and `rem` units.

---

## Ideas for Improvement

- [ ] Add media queries so it works on mobile and tablet
- [ ] Use CSS variables for colours (`--purple`, `--lime`, `--card-bg`)
- [ ] Add hover effects on nav items, cards and the review button
- [ ] Turn the nav items into real links (`<a>`)
- [ ] Add `loading="lazy"` to images and compress large files
- [ ] Add a visible focus style for keyboard users
- [ ] Add subtle entry animations or transitions

---

## Tech Stack

- HTML5
- CSS3 (Grid, Flexbox, gradients, transforms)
- Google Font: Poppins (needs to be linked)

---

## Credits

Layout inspired by modern "bento box" landing page designs. Built as a front-end practice project.
