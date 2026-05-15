# In Good Company — Shopify Theme Setup Guide

## Quick Start

### 1. Upload the Theme to Shopify

1. Zip the entire `ingoodcompany-theme` folder
2. Go to **Shopify Admin → Online Store → Themes**
3. Click **Add theme → Upload zip file**
4. Upload your zip and click **Publish**

---

## 2. Create These Pages in Shopify Admin

Go to **Online Store → Pages → Add page** for each:

| Page Title | Handle (URL slug) | Template |
|---|---|---|
| Websites | `websites` | `page.websites` |
| Social Media | `social-media` | `page.social-media` |
| Printed Products | `printed-products` | `page.printed-products` |
| Digital Products | `digital-products` | `page.digital-products` |
| Handcrafted | `handcrafted` | `page.handcrafted` |
| Our Brands | `brands` | `page.brands` |
| About | `about` | `page.about` |
| Contact | `contact` | `page.contact` |

> **How to set the template:** When creating/editing a page, look for "Theme template" in the right sidebar and select the matching template from the dropdown.

---

## 3. Add Your Photo (About Page)

1. Upload your photo to **Settings → Files** in Shopify Admin
2. Open `templates/page.about.liquid`
3. Find the placeholder `📸` comment and replace with:
   ```html
   <img src="{{ 'your-photo-filename.jpg' | asset_url }}" alt="Julie" style="width:100%;height:100%;object-fit:cover;">
   ```

---

## 4. Update Brand Links

On the **Brands** page, all brand cards currently link to `#`. When each brand has a URL:
- Open `templates/page.brands.liquid`  
- Replace `href="#"` with the actual brand URL for each card

---

## 5. Configure Settings

Go to **Online Store → Themes → Customize**:
- Update the **Announcement Bar** text and link
- Add your **social media URLs** (Instagram, Facebook, Pinterest, TikTok)
- Update the **footer about text**

---

## 6. Add a Hero Background Image

1. Upload a lifestyle/brand photo to **Settings → Files**
2. In `templates/index.liquid`, find the hero section
3. Add your image: the `hero__bg` div has `background-image: url('{{ 'hero-bg.jpg' | asset_url }}')` — upload a file named `hero-bg.jpg`

---

## 7. Update Contact Email

In `templates/page.contact.liquid`, find:
```
hello@ingoodcompanycreative.com
```
Replace with your actual email address.

---

## Color Palette Reference

| Color | Hex | Usage |
|---|---|---|
| Dark Brown | `#1C1812` | Text, backgrounds |
| Forest Green | `#3A5040` | Accents, CTAs, nav highlights |
| Warm Gold | `#B8975A` | Featured badges, highlights |
| Cream | `#F7F3EE` | Section backgrounds |
| Warm Sand | `#D4C4A8` | Secondary text on dark |

---

## Fonts

- **Logo & Headings:** Optima (system font on Mac/iOS, falls back to Palatino on Windows/Android)
- **Body:** System sans-serif stack

---

## File Structure

```
ingoodcompany-theme/
├── assets/
│   ├── theme.css          ← All styles
│   ├── theme.js           ← Nav toggle, form handling
│   └── logo.svg           ← SVG text logo
├── config/
│   ├── settings_data.json ← Default setting values
│   └── settings_schema.json ← Theme settings definition
├── layout/
│   └── theme.liquid       ← Master layout (head, header, footer)
├── locales/
│   └── en.default.json    ← Text strings
├── sections/
│   ├── announcement-bar.liquid
│   ├── header.liquid      ← Logo + nav
│   ├── footer.liquid      ← Footer with social links
│   └── newsletter.liquid  ← Email signup
└── templates/
    ├── index.liquid        ← Home page
    ├── page.liquid         ← Default page fallback
    ├── page.websites.liquid
    ├── page.social-media.liquid
    ├── page.printed-products.liquid
    ├── page.digital-products.liquid
    ├── page.handcrafted.liquid
    ├── page.brands.liquid
    ├── page.about.liquid
    └── page.contact.liquid
```
