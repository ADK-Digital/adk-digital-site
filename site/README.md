# Everleaf Law Static Site

This project is a single‑page, responsive website for a hypothetical boutique law firm.  It is designed to be clean, approachable and thorough, with careful attention to accessibility and performance.  Content is organized into clearly defined sections and styled with a neutral palette accented by warm tones.

## Changing the Brand and Content

* **Firm name & tagline:**  The brand name _Everleaf Law_ and tagline _“We turn every leaf.”_ appear in several places: the SVG logo (`/assets/logo.svg`), the header, hero section, footer and the HTML `<title>` tag.  To customize, search for the string “Everleaf Law” in `index.html` and replace it with your firm name.  Edit the tagline similarly.
* **Logo:**  The current logo is a simple SVG combining a leaf mark and the firm name.  Replace `/assets/logo.svg` with your own SVG lockup, or adjust the `logo.svg` file directly.  Ensure the `viewBox` and colours align with your brand.  Favicons are generated from the leaf mark and stored at `favicon.ico`, `favicon-32.png` and `favicon-64.png`.  If you change the logo, regenerate these as needed.
* **Colour palette:**  Colours are defined as CSS variables in `/css/styles.css` at the top of the file.  Adjust `--color-forest`, `--color-slate`, `--color-ivory`, `--color-moss` and `--color-copper` to fit your brand.  The CSS uses these variables throughout, so global changes will update the entire site.
* **Typography:**  The site uses the [Playfair Display](https://fonts.google.com/specimen/Playfair+Display) typeface for headings and [Inter](https://fonts.google.com/specimen/Inter) for body copy.  To swap fonts, update the `<link>` tag in `index.html` and adjust the `--font-display` and `--font-body` variables in `styles.css`.
* **Practice areas & copy:**  Practice areas, process steps, case summaries, testimonials, bios and FAQs are all editable directly in `index.html`.  Use clear, plain‑language copy and keep bullet lists concise.  Each practice card includes a short description and a list of services.
* **Formspree endpoint:**  The contact form posts to Formspree.  Replace `YOUR_FORMSPREE_ID` in the form’s `action` attribute with your actual Formspree form ID.  To add server‑side validation or integrate with another provider, update the `action` URL accordingly.

## Replacing Images

All custom images live in the `/images` directory.  Each `<img>` element specifies explicit `width` and `height` attributes to prevent layout shifts.

* **Hero (`images/hero.jpg`):**  A warm, documentary desk scene sourced from Pexels (ID 8353764).  Replace this with your own high‑quality photograph of case files, binders or documents that conveys diligence and calm.  For the best results, choose a landscape image at least 2000 px wide and update the `background-image` URL in `.hero__background` within `styles.css` if you rename the file.
* **Team (`images/attorney1.jpg`, `images/attorney2.jpg`):**  These are cropped portraits taken from a Pexels group photo (ID 4427430 by August de Richelieu).  Replace them with professional headshots of your attorneys.  Maintain similar dimensions (≈400×500 px) and update the `src` attributes in the team section.  Portraits should have sufficient whitespace around the subject and neutral backgrounds for consistency.
* **Icons (`/assets`):**  Practice area icons are inline SVGs downloaded from the [Heroicons](https://heroicons.com/) set.  To change an icon, swap the corresponding file in `/assets` (e.g. `scale.svg`, `users.svg`, etc.) or drop in your own SVGs.  The leaf motif used throughout the site is defined in `leaf.svg`.
* **Additional imagery:**  If you wish to add photos for the results or practice sections, place them in `/images` and reference them in `index.html`.  Consider using royalty‑free resources such as [Unsplash](https://unsplash.com) or [Pexels](https://www.pexels.com) and provide attribution where required.

## Structure

```
site/
├── index.html          # Single‑page website
├── css/
│   └── styles.css      # All custom styles (BEM naming)
├── js/
│   └── main.js         # Interactivity: nav, accordion, form, etc.
├── images/
│   ├── hero.jpg        # Hero background image (documents on desk)
│   ├── attorney1.jpg   # Cropped portrait 1
│   ├── attorney2.jpg   # Cropped portrait 2
│   └── group.jpg       # Original group photo (unused placeholder)
└── assets/
    ├── logo.svg        # SVG logo lockup
    ├── leaf.svg        # Leaf motif used for decoration
    ├── favicon.ico     # Favicon (multiple sizes)
    ├── favicon-32.png  # 32×32 PNG favicon
    ├── favicon-64.png  # 64×64 PNG favicon
    ├── scale.svg       # Icon for Litigation
    ├── users.svg       # Icon for Employment
    ├── light-bulb.svg  # Icon for Startup Counsel
    ├── home.svg        # Icon for Real Estate
    ├── document-text.svg # Icon for Contracts
    └── key.svg         # Icon for IP & Licensing
```

## Performance & Accessibility Notes

* Images specify `width` and `height` attributes and are lazy‑loaded by default with the `loading` attribute (except the hero, which preloads).  Replace any large images with appropriately sized WebP/AVIF files for additional gains.
* The header becomes sticky on scroll and uses `backdrop-filter` to achieve a frosted glass effect.  It remains below the back‑to‑portfolio button thanks to z‑index management.
* Accordions use proper ARIA roles (`button`, `region`) and `aria-expanded` attributes.  Only the panels associated with expanded toggles are visible; pressing Enter or Space toggles them.  The mobile navigation traps focus when open and closes on `Escape`.
* All interactive elements are keyboard accessible with visible focus states.  The site respects the `prefers-reduced-motion` media query by disabling animated transitions when necessary.

## Credits

* Hero photo (documents on desk): downloaded from Pexels, image ID 8353764.  The photo is provided under the [Pexels License](https://www.pexels.com/license/) which allows commercial and non‑commercial use without attribution.  You may replace it with your own image.
* Team portraits cropped from “Lawyers posing for a photo” by **August de Richelieu**, Pexels ID 4427430, also covered by the Pexels License.
* Icons: [Heroicons](https://heroicons.com/) MIT‑licensed icons.  Leaf motif created in‑house.

---

This project is ready to deploy on static hosting services such as Vercel or Netlify.  Simply zip the `site` directory and upload it to your hosting provider.  No build steps are required.