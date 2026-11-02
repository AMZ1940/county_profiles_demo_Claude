# County Emergency Management Profile (demo)

A fictional county profile for **Briarwood County, State of Westhaven**. All the data is made up. Users must sign in with ArcGIS (OAuth 2.0) before the profile is shown.

Live URL: https://amz1940.github.io/county_profiles_demo_Claude/

## Files
| File | What it does |
|---|---|
| `index.html` | Page layout (sign-in gate and profile sections) |
| `styles.css` | Styling, plus the fixed-width layout used for the PDF |
| `data.js` | **All profile data.** Edit this file to change numbers or swap in a real county |
| `app.js` | ArcGIS sign-in, charts, heat map and PDF export. Client ID and portal URL are at the top |

## One-time ArcGIS setup (required)
1. In ArcGIS Online, open the OAuth 2.0 credentials item with client ID `w9VaoRCHch2gIU1d` and go to **Settings → Redirect URLs**.
2. Add these redirect URLs exactly as written (the third one is needed when the page is embedded in Experience Builder):
   - `https://amz1940.github.io/county_profiles_demo_Claude/`
   - `https://amz1940.github.io/county_profiles_demo_Claude/index.html`
   - `https://amz1940.github.io/county_profiles_demo_Claude/oauth-callback.html`
3. Save.

If your organization signs in through its own URL (for example `https://yourorg.maps.arcgis.com`) or through ArcGIS Enterprise, change `PORTAL_URL` at the top of `app.js`.

## Publish to GitHub Pages
1. Upload `index.html`, `oauth-callback.html`, `styles.css`, `data.js`, `app.js` and this README to the root (not inside a subfolder) of the `county_profiles_demo_Claude` repo.
2. Go to **Settings → Pages**, set the source to *Deploy from a branch*, and choose `main` / root.
3. Wait about a minute, then open the URL above. You should see the sign-in screen.

## Notes
- **What the sign-in does and doesn't protect:** it stops people from seeing the page unless they sign in. Because the repo and the GitHub Pages site are public, anyone could still read `data.js` directly. That's fine for fictional data. Real or sensitive data would need to be stored as a secured ArcGIS layer or table that the page loads with the user's token after sign-in.
- **PDF:** *Download PDF* takes a snapshot of the map and uses a fixed desktop-width layout. Each major section starts on a new page. Page numbers are added at the bottom.
- **Heat map:** the points are synthetic census blocks, generated from a fixed seed, and the county boundary is made up. The map uses no basemap so it doesn't look like a real place.
- **Local preview:** run `python3 -m http.server` in this folder and open `http://localhost:8000/?preview` to skip sign-in. This works only on localhost.
