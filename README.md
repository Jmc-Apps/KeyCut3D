<p align="center"><img src="icons/logo.png" alt="KeyCut3D" width="420"></p>

# KeyCut3D

Turn photos of a key into a 3D-printable STL. It's a hobby tool for lock sport and key casting.

KeyCut3D runs entirely in the phone's browser. Photos are processed on the device and never uploaded anywhere. Once it has been opened, it works offline and can be added to the home screen like an app.

## How it works

1. **Card:** print the reference card (`card/keycut3d_card_85.6x53.98.stl`), or generate one in the app to your own measurements. It is bank-card sized (85.6 × 53.98 mm), with a recess for the key.
2. **Side A / Side B:** photograph the key lying in the recess, then flip it and photograph the other side. The app finds the card's corners, flattens the photo and traces the key's outline. Side B is mirrored and lined up with side A automatically.
3. **Keyway:** add the blade's cross-section (its grooves) in one of four ways:
   - **Edge photo (recommended):** lay the key on the card, side A up, cut edge on your right, with the tip level with the card's front edge. Photograph it head-on with the phone level with the card. You tap the four corners of the card's edge strip, which sets the scale (card length × card thickness), then tap the end of the key.
   - **Combined (most accurate):** groove positions and widths from the side photos, and groove depths (and V or square shape) from the edge photo. Grooves seen in only one of the photos are flagged so you can check them, and the result can be edited in Manual grooves or saved to the library.
   - **Keyhole photo:** hold the card flat against the lock and trace the keyhole, with a clearance setting.
   - **Library:** pick from built-in profiles. *Suggest from my photos* ranks them against your traced profile.
   - **Manual grooves:** enter each groove's face, position, width, depth and shape, or press **Auto-detect** to fill in groove positions and widths from the side photos. Depth can't be seen from above, so it starts at an assumed depth that you adjust.
4. **Tidy up:** fix any tracing mistakes with the straight-line **lasso**. Choose *Lasso +* (add), *Lasso −* (remove) or *Keep inside*, tap the corners of a shape, then tap the first point or press *Done*. *Undo* steps back one lasso at a time.
5. **Build:** the app finds the blade, the tip, the cut edge and the shoulder, runs the keyway profile along the blade, and exports a watertight STL.

## Printing the card

- Use **light, matte** filament. Light blue or aqua is best, then matte white. Avoid silk or glossy filament, grey, and yellow or gold.
- Print with the recess facing up and **ironing off**.
- Measure the printed card with calipers and enter the real width, height and thickness (floor + recess depth) in the app. The edge photo uses the thickness for scale.

## Taking photos

- Shoot straight down from 30–40 cm, using 2× zoom if available, in soft, even light.
- Put the card on a dark surface.
- For the edge photo, get close (or use 2× zoom) so the card fills the width of the photo, tap the key to focus, put something plain and dark behind it, and light it from the front. Don't hold the key down with a finger.

## Hosting on GitHub Pages

1. Create a new repository and upload **everything in this folder** (including the hidden `.nojekyll` file) to the root of the repository.
2. In the repository, go to **Settings → Pages**. Under *Build and deployment*, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
3. After a minute or two the app is live at `https://<your-username>.github.io/<repository-name>/`.
4. On your phone, open that address and use **Add to Home Screen**.

**Force an update on a phone:** tap the KeyCut3D logo 5 times quickly. The app clears its offline copy and reloads the latest version.

When you publish an update, change `CACHE` in `sw.js` (for example to `keycut3d-v7`) so phones load the new version.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole app (HTML, CSS and JavaScript in one file) |
| `manifest.webmanifest` | Lets the app be installed on a phone |
| `sw.js` | Offline support |
| `icons/` | App icon, favicon and logo |
| `card/` | Reference card STL (default size) |
| `THIRD_PARTY_NOTICES.md` | Licences for the included open-source parts |

## Limitations

- The built-in keyway profiles are US keyways (Kwikset, Schlage, Best, Master and Medeco). Common South African keyways such as Union and Yale SA aren't published, so capture them with an edge or keyhole photo and save them to your library.
- Saved profiles and settings (card size, which edge faces the camera) are stored in the browser on that device.
- Grooved keys are exported as a stack of thin layers. Each layer is a closed solid, and slicers merge them normally.
- Always check a printed key against the original with calipers before making a mould.

## Responsible use

Only copy keys you own or have permission to copy.

## Credits

- Keyway profiles from [keygen](https://github.com/ervanalb/keygen) by ervanalb and contributors (CC0 1.0).
- Polygon triangulation by [earcut](https://github.com/mapbox/earcut) (ISC licence, © Mapbox).

See `THIRD_PARTY_NOTICES.md` for details.
