<p align="center"><img src="icons/logo.png" alt="KeyCut3D" width="420"></p>

# KeyCut3D

Turn photos of a key into a 3D-printable STL. It's a hobby tool for lock sport and key casting.

KeyCut3D runs entirely in the phone's browser. Photos are processed on the device and never uploaded anywhere. Once it has been opened, it works offline and can be added to the home screen like an app.

## How it works

1. **Card:** print the reference card (`card/keycut3d_card_85.6x53.98_slot.stl`), or generate one in the app to your own measurements. It is bank-card sized (85.6 × 53.98 mm), with a recess for the key and a slot for the keyway photo.
2. **Side A / Side B:** photograph the key lying in the recess, then flip it and photograph the other side. The app finds the card's corners, flattens the photo and traces the key's outline. Side B is mirrored and lined up with side A automatically.
3. **Keyway:** add the blade's cross-section (its grooves) in one of four ways:
   - **Slot photo:** stand the key upright in the card's slot and photograph the tip end-on.
   - **Lock face photo:** hold the card against the lock and trace the keyway opening, with a clearance setting.
   - **Library:** pick from built-in profiles. *Suggest from my photos* ranks them against your traced profile.
   - **Manual grooves:** enter each groove's face, position, width, depth and shape, or press **Auto-detect** to fill in groove positions and widths from the side photos. Depth can't be seen from above, so it starts at an assumed depth that you adjust.
4. **Build:** the app finds the blade, the tip, the cut edge and the shoulder, runs the keyway profile along the blade, and exports a watertight STL.

## Printing the card

- Use **light, matte** filament. Light blue or aqua is best, then matte white. Avoid silk or glossy filament, grey, and yellow or gold.
- Print with the recess facing up and **ironing off**.
- Measure the printed card with calipers and enter the real width and height in the app.

## Taking photos

- Shoot straight down from 30–40 cm, using 2× zoom if available, in soft, even light.
- Put the card on a dark surface with the slot on the right.
- For the slot photo, push the key up through the slot from below, tip first, with the cut edge toward the arrow and side A facing the recess. About 8 mm should stick out. Pack Prestik or Blu Tack around it.

## Hosting on GitHub Pages

1. Create a new repository and upload **everything in this folder** (including the hidden `.nojekyll` file) to the root of the repository.
2. In the repository, go to **Settings → Pages**. Under *Build and deployment*, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
3. After a minute or two the app is live at `https://<your-username>.github.io/<repository-name>/`.
4. On your phone, open that address and use **Add to Home Screen**.

When you publish an update, change `CACHE` in `sw.js` (for example to `keycut3d-v4`) so phones load the new version.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole app (HTML, CSS and JavaScript in one file) |
| `manifest.webmanifest` | Lets the app be installed on a phone |
| `sw.js` | Offline support |
| `icons/` | App icon, favicon and logo |
| `card/` | Reference card STL (default size, with slot) |
| `THIRD_PARTY_NOTICES.md` | Licences for the included open-source parts |

## Limitations

- The built-in keyway profiles are US keyways (Kwikset, Schlage, Best, Master and Medeco). Common South African keyways such as Union and Yale SA aren't published, so trace them with a slot or lock-face photo and save them to your library.
- Saved profiles are stored in the browser on that device.
- Grooved keys are exported as a stack of thin layers. Each layer is a closed solid, and slicers merge them normally.
- Always check a printed key against the original with calipers before making a mould.

## Responsible use

Only copy keys you own or have permission to copy.

## Credits

- Keyway profiles from [keygen](https://github.com/ervanalb/keygen) by ervanalb and contributors (CC0 1.0).
- Polygon triangulation by [earcut](https://github.com/mapbox/earcut) (ISC licence, © Mapbox).

See `THIRD_PARTY_NOTICES.md` for details.
