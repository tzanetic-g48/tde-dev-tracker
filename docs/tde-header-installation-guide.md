# TDE Mega Menu Header — Installation Guide

## Overview
This is a standalone Shopify liquid section that replaces your existing theme header.
Compatible with Dawn, Debut, Brooklyn, and most Shopify themes.
No external dependencies — pure Liquid, CSS, and vanilla JS.

---

## Step 1 — Upload the section file

1. In Shopify Admin, go to **Online Store → Themes**
2. Next to your active theme, click **Actions → Edit code**
3. In the left sidebar, click the **Sections** folder
4. Click **Add a new section**
5. Name it exactly: `tde-header-mega-menu`
6. Delete the placeholder content and **paste the entire contents of `sections/tde-header-mega-menu.liquid`**
7. Click **Save**

---

## Step 2 — Add to your theme layout

1. In the code editor, open **Layout → theme.liquid**
2. Find the existing header render tag:
   ```
   {% section 'header' %}
   ```
3. Replace with:
   ```liquid
   {% section 'tde-header-mega-menu' %}
   ```
4. Remove any separate announcement-bar section — the TDE header has its own.
5. Click **Save**

> **Dawn theme note:** You may also need to update `sections/header-group.json` to reference the new section name.

---

## Step 3 — Configure in theme customizer

1. Go to **Online Store → Themes → Customize**
2. Find **TDE Mega Menu Header** in the sidebar
3. Recommended settings:

| Setting | Value |
|---|---|
| Logo image | Upload TDE logo PNG/SVG |
| Header background | #ffffff |
| Nav text color | #1a1a1a |
| Nav hover color | #b8a898 |
| Font family | Helvetica Neue |
| Announcement text | Free monogramming · Complimentary shipping over $100 · Signature dust bag included |

### Adding nav blocks

Each block = one top-level link + optional 3-column dropdown + hero image.

Link format in textarea fields:
```
Totes | /collections/totes
Shoulder | /collections/shoulder-bags
Clutches | /collections/clutches
```

Leave all column fields blank for a direct link with no dropdown (e.g. Sale).

---

## Step 4 — Sale accent colour (optional)

Add to your theme's `base.css`:
```css
.tde-nav__item:last-child .tde-nav__link { color: #c0392b; }
.tde-nav__item:last-child:hover .tde-nav__link { color: #c0392b; opacity: 0.75; }
```

---

## Testing checklist

### Desktop
- [ ] Header renders with correct colours
- [ ] Dropdown opens on hover, closes on mouse-leave
- [ ] All 3 columns + hero image display correctly
- [ ] Overlay dims page behind open dropdown
- [ ] Search overlay opens/closes
- [ ] Cart badge shows item count

### Mobile
- [ ] Hamburger opens slide-out menu
- [ ] Sub-menu slides in on item tap
- [ ] Back button returns to root
- [ ] Hero/promo image shows at bottom of sub-menu
- [ ] Overlay tap closes menu
- [ ] Escape key closes menu

### Accessibility
- [ ] Keyboard navigation works (Tab, Enter, Escape)
- [ ] Screen reader announces dialog on mobile menu open

---

## Dependencies

None. Pure Shopify Liquid + vanilla JS. No apps, no npm, no external libraries.
Only external call: `/cart.js` (native Shopify AJAX Cart API) for badge updates.
