# Denton Fire Camp 2026 Sponsor Page

A single-page sponsor and donation site for the Denton Fire Department's annual Fire Camp. The page tells prospective sponsors what Fire Camp is, shows them how to feed the camp, lists the restaurants that have catered it before, and explains how to give financially through Denton Fire Traditions.

Built and maintained by the Community Risk Reduction Office, Support Services Division, Denton Fire Department.

## Live site

The page deploys through GitHub Pages from this repository. The URL follows the department's standard GitHub Pages pattern for the `DentonFire` / `dentonfiredept` organization. Once Pages is enabled on the `main` branch, the site is live at the repository's GitHub Pages address.

## What is in this repository

```
index.html      The entire site. Self-contained.
README.md       This file.
```

That is the whole project. `index.html` holds the markup, all CSS, all JavaScript, and the three Fire Camp photos encoded directly into the file. There is no build step, no dependency install, and no separate image folder to manage.

## Deploying

1. Commit `index.html` to the `main` branch.
2. In the repository settings, under Pages, set the source to the `main` branch and the root folder.
3. GitHub publishes the page within a minute or two.

To update the live page later, edit `index.html`, commit, and push. GitHub Pages redeploys automatically.

Pushing requires a Personal Access Token with repo scope, following the same pattern used for the department's other GitHub Pages sites:

```
git remote set-url origin https://[TOKEN]@github.com/[ORG]/[REPO].git
git push origin main
```

## Updating content

All edits happen in `index.html`. The sections are laid out top to bottom in the order they appear on the page, so searching the file for the text you see on screen takes you straight to the right spot.

### Camp dates, location, and camper count

These appear in the hero section near the top of the file inside the `datebar` block, and again in the "What Is Fire Camp" stat cards. Update both places so the page stays consistent.

### Restaurant cards

The restaurant grid is in the section that begins with "Restaurants That Have Fed Fire Camp." Each card is a `resto-card` block with a name, an area, a short description, and a links row. The links row holds a Website button and an Email button. To change a contact, edit the `href` on the matching `<a>` tag. To add a restaurant, copy an existing `resto-card` block and fill in the four fields. To remove one, delete its block. The grid reflows on its own.

The Website button is always the first link in the row and the Email button is the second. If a card has only one link, it renders in the neutral style automatically.

### Photos

The three photos are embedded as base64 strings inside `index.html`:

- The fire station bay photo sits behind the hero.
- The hose line photo is the feature image in the "What Is Fire Camp" section.
- The Juicy Pig BBQ banner photo is the proof image in the "Sponsor a Meal" section.

Replacing a photo means swapping its base64 string. Optimize the new image first (resize to roughly 1400 to 1500 pixels wide and compress as a progressive JPEG so the file stays small), encode it to base64, and replace the existing string between `data:image/jpeg;base64,` and the closing quote on the matching `<img>` tag.

### Sponsorship tiers and the donation address

The Bronze, Silver, and Gold rows and the mailed-check details are in the "Make a Monetary Donation" section. Checks are payable to Denton Fire Traditions, a local 501(c)(3), mailed to 332 E. Hickory Street, Denton, TX 76201, attention Stacy Fruge. Questions go to dentonfiretraditions@gmail.com.

### Contact block

Captain Hunter Lott's contact information is in the closing call-to-action section. Update it there if the point of contact changes.

## Design and brand notes

The page uses the department's brand colors and the Knox Box web palette: navy `#152a40`, red `#bf2726`, and gold `#f9c031`. Display type is Bitter and body type is Source Sans 3, both loaded from Google Fonts. The DFD patch loads from the department's Constant Contact CDN. The header carries the cubes texture used across DFD web properties.

The page scrolls with staggered fade-in animations and the cards lift on hover. A `prefers-reduced-motion` media query disables all motion for visitors whose system or browser requests reduced motion, so the page stays accessible to anyone with vestibular sensitivity.

## Maintainer

Captain Hunter Lott
Community Risk Reduction Officer
Support Services Division
Denton Fire Department
Hunter.Lott@cityofdenton.com
