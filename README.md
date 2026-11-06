<p align="center"><img src="icons/logo.png" alt="KeyCut3D" width="420"></p>

# KeyCut3D

Turn photos of a key into a 3D-printable STL. It's a hobby tool for lock sport and key casting.

KeyCut3D runs entirely in the phone's browser. Photos are processed on the device and never uploaded anywhere. Once it has been opened, it works offline and can be added to the home screen like an app.

## How it works

1. **Card:** print the reference card (`card/keycut3d_card_85.6x53.98.stl`), or generate one in the app to your own measurements. It is bank-card sized (85.6 × 53.98 mm), with a recess for the key.
2. **Side A / Side B:** photograph the key lying in the recess, then flip it and photograph the other side. The app finds the card's corners, flattens the photo and traces the key's outline. Side B is mirrored and lined up with side A automatically.
3. **Keyway:** add the blade's cross-section (its grooves) in one of four ways:
   - **Gauge photo (recommended):** print the small L-shaped profile gauge, sized in the app to your key's blade (`card/keycut3d_gauge_9x2.4.stl` is a 9 × 2.4 mm example). Lay the key on its base with side A up and the cut edge on your right, slide the tip 3–5 mm through the hole, and photograph the front face head-on. The face hides the bow, so only the tip's outline shows, and its four corners set the scale.
   - **Slot photo:** the older method. Stand the key upright in a slot in the card (tick *Include the old keyway slot* when generating the card).
   - **Lock face photo:** hold the card against the lock and trace the keyway opening, with a clearance setting.
   - **Library:** pick from built-in profiles. *Suggest from my photos* ranks them against your traced profile.
   - **Manual grooves:** enter each groove's face, position, width, depth and shape, or press **Auto-detect** to fill in groove positions and widths from the side photos. Depth can't be seen from above, so it starts at an assumed depth that you adjust.
4. **Tidy up:** fix any tracing mistakes with the straight-line **lasso**. Choose *Lasso +* (add), *Lasso −* (remove) or *Keep inside*, tap the corners of a shape, then tap the first point or press *Done*. *Undo* steps back one lasso at a time.
5. **Build:** the app finds the blade, the tip, the cut edge and the shoulder, runs the keyway profile along the blade, and exports a watertight STL.

## Printing the card

- Use **light, matte** filament. Light blue or aqua is best, then matte white. Avoid silk or glossy filament, grey, and yellow or gold.
- Print with the recess facing up and **ironing off**.
- Measure the printed card with calipers and enter the real width and height in the app.

## Taking photos

- Shoot straight down from 30–40 cm, using 2× zoom if available, in soft, even light.
- Put the card on a dark surface.
- For the gauge photo, hold the phone at about the height of the hole, about 30 cm away, with the whole front face in the picture. Soft light from the front lights the key's end best.

## Hosting on GitHub Pages

1. Create a new repository and upload **everything in this folder** (including the hidden `.nojekyll` file) to the root of the repository.
2. In the repository, go to **Settings → Pages**. Under *Build and deployment*, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
3. After a minute or two the app is live at `https://<your-username>.github.io/<repository-name>/`.
4. On your phone, open that address and use **Add to Home Screen**.

**Force an update on a phone:** tap the KeyCut3D logo 5 times quickly. The app clears its offline copy and reloads the latest version.

When you publish an update, change `CACHE` in `sw.js` (for example to `keycut3d-v5`) so phones load the new version.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole app (HTML, CSS and JavaScript in one file) |
| `manifest.webmanifest` | Lets the app be installed on a phone |
| `sw.js` | Offline support |
| `icons/` | App icon, favicon and logo |
| `card/` | Reference card STL and an example profile gauge STL |
| `THIRD_PARTY_NOTICES.md` | Licences for the included open-source parts |

## Limitations

- The built-in keyway profiles are US keyways (Kwikset, Schlage, Best, Master and Medeco). Common South African keyways such as Union and Yale SA aren't published, so trace them with a slot or lock-face photo and save them to your library.
- Saved profiles and settings (card size, gauge size) are stored in the browser on that device.
- Grooved keys are exported as a stack of thin layers. Each layer is a closed solid, and slicers merge them normally.
- Always check a printed key against the original with calipers before making a mould.

## Responsible use

Only copy keys you own or have permission to copy.

## Credits

- Keyway profiles from [keygen](https://github.com/ervanalb/keygen) by ervanalb and contributors (CC0 1.0).
- Polygon triangulation by [earcut](https://github.com/mapbox/earcut) (ISC licence, © Mapbox).

See `THIRD_PARTY_NOTICES.md` for details.
