<p align="center"><img src="icons/logo.png" alt="KeyCut3D" width="420"></p>

# KeyCut3D

Turn photos of a key into a 3D-printable STL. It's a hobby tool for lock sport and key casting.

KeyCut3D runs entirely in the phone's browser. Photos are processed on the device and never uploaded anywhere. Once it has been opened, it works offline and can be added to the home screen like an app.

## How it works

1. **Card (⚙︎ cog, top right):** the app opens on the card page the first time, then on Side A after that. Print the reference card (`card/keycut3d_card_85.6x53.98.stl`), or generate one in the app to your own measurements. It is bank-card sized (85.6 × 53.98 mm), with a recess for the key and a row of **thickness notches** (1.6–3.0 mm in 0.1 mm steps, with raised numbers) along the bottom edge. Push the blade edge-on into the notches, and the narrowest one it fits is its thickness. A 14 mm **keyhole window** at the left of the recess is for keyhole photos. For side photos, lay the key with its bow over the window and its tip pointing the way of the raised arrow.
2. **Side A / Side B:** photograph the key lying in the recess, then flip it and photograph the other side. The app finds the card's corners, flattens the photo and traces the key's outline. Side B is mirrored and lined up with side A automatically, using the blade only (the bow is replaced anyway, and shiny bows often trace badly). The Build step shows a **Side A vs side B** overlay with how well the blades agree, and warns you if they don't match. If the phone saved a photo sideways, use **↺ / ↻ Rotate** before flattening (this works on keyway photos too).
3. **Keyway:** add the blade's cross-section (its grooves):
   - **Auto grooves (default):** grooves are found in the side A and B photos and cut to a set share of the key's thickness (halfway by default), which makes the copy slightly smaller in those spots so it slides in easily. Grooves facing each other on opposite faces always keep a minimum wall between them. Each groove shows as a shaded band between two lines on a strip of the blade from each photo. Drag the lines to fit the groove exactly, or add and delete bands. The blade is straightened automatically along its bottom (uncut) edge. Two white handles on the side A strip show that line: drag them onto the edge if they're off, or press *Reset straightening*.
   - **Edge photo:** lay the key on the card, side A up, cut edge on your right, with the tip level with the card's front edge. Photograph it head-on with the phone level with the card. You tap the four corners of the card's edge strip, which sets the scale (card length × card thickness), then tap the end of the key.
   - **Combined (most accurate):** groove positions and widths from the side photos, and groove depths (and V or square shape) from the edge photo. Grooves seen in only one of the photos are flagged so you can check them, and the result can be edited in Manual grooves or saved to the library.
   - **Keyhole photo:** hold the card flat against the lock with the keyhole showing through the card's round window. The app zooms straight to the window and traces the keyhole, with a clearance setting.
   - **Library:** pick from built-in profiles. *Suggest from my photos* ranks them against your traced profile.
   - **Manual grooves:** enter each groove's face, position, width, depth and shape, or press **Auto-detect** to fill in groove positions and widths from the side photos. Depth can't be seen from above, so it starts at an assumed depth that you adjust.
4. **Tidy up:** pinch to zoom into any trace (double-tap to fit). Fix mistakes with squares and circles: **■ +** / **● +** add and **■ −** / **● −** remove. Drag corner to corner for a square, or from the centre outwards for a circle. *Undo* steps back one shape at a time.
5. **Shoulder:** found automatically where the outline rises well above the blade and stays up (glare spikes and nicks are ignored), and re-detected when the trace, Combine or straightening changes. Type your own value to override it.
5b. **Cut edge cleanup** (Build step, default Light): removes nicks and bumps that come from photo noise, rebuilds the cut edge from straight flanks meeting at sharp cut roots, makes the bottom edge perfectly straight and tidies the tip. The Blade check shows what was trimmed (faint red) and filled (faint green). Set it to Off to use the raw trace.
6. **Bow:** the photographed bow is always replaced with a clean designed one, placed at the original shoulder so the key still stops at the right depth. Choose **Camera** (default; a KeyCut3D camera silhouette with a lens hole that takes a keyring), **Circle** or **Octagon** (both with a 5 mm keyring hole). *Bow size* sets the camera width or the circle/octagon diameter.
6. **Build:** the app finds the blade, the tip, the cut edge and the shoulder, runs the keyway profile along the blade, and exports a watertight STL.

## Printing the card

- Use **light, matte** filament. Light blue or aqua is best, then matte white. Avoid silk or glossy filament, grey, and yellow or gold.
- Print with the recess facing up, **ironing off**, and a fine layer height (0.12–0.16 mm) so the raised numbers stay crisp.
- Measure the printed card with calipers and enter the real width, height and thickness (floor + recess depth) in the app. The edge photo uses the thickness for scale.

## Taking photos

- Shoot straight down from 30–40 cm, using 2× zoom if available, in soft, even light.
- Put the card on a dark surface.
- The app blocks page zoom and text selection so taps and drags don't get in the way. Pinch-zoom still works inside the photo viewers.
- For the edge photo, get close (or use 2× zoom) so the card fills the width of the photo, tap the key to focus, put something plain and dark behind it, and light it from the front. Don't hold the key down with a finger.

## Hosting on GitHub Pages

1. Create a new repository and upload **everything in this folder** (including the hidden `.nojekyll` file) to the root of the repository.
2. In the repository, go to **Settings → Pages**. Under *Build and deployment*, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
3. After a minute or two the app is live at `https://<your-username>.github.io/<repository-name>/`.
4. On your phone, open that address and use **Add to Home Screen**.

**Force an update on a phone:** tap the KeyCut3D logo 5 times quickly. The app clears its offline copy and reloads the latest version.

When you publish an update, change `CACHE` in `sw.js` (for example to `keycut3d-v9`) so phones load the new version.

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
- Always check a printed key against the original with calipers.
- Print keys flat (faces on the bed) so the layers run along the blade. That's much stronger when turning. PETG or a tough PLA is recommended.

## Responsible use

Only copy keys you own or have permission to copy.

## Credits

- Keyway profiles from [keygen](https://github.com/ervanalb/keygen) by ervanalb and contributors (CC0 1.0).
- Polygon triangulation by [earcut](https://github.com/mapbox/earcut) (ISC licence, © Mapbox).

See `THIRD_PARTY_NOTICES.md` for details.

## 🔑 Key decoder (no photos)

Decode a key on your phone screen and build it from its code.

1. On the ⚙︎ page, choose your **phone model** (this sets the screen to life-size). Press **Check size**, lay the printed card on the outline and use Smaller/Bigger until it fits exactly.
2. Open **🔑 Decoder** (Side A step or Build step) and choose the key system: Kwikset KW1, Schlage classic (5 or 6 cuts), Master padlock, or **Custom**: in the on-screen decoder add cuts one at a time with **+ Cut**, slide each one ▲▼ (or drag its number) onto the cut and set its depth. **Save as system** works out the first-cut position, spacing and depth step and saves it as your own key system for that brand.
3. **Open decoder on screen.** Lay the key flat: shoulder on the red line, bottom (uncut) edge on the green line. Tap each cut's number and press Deeper/Shallower until the outline hugs the key. Blade and Tip set the uncut width and the length.
   **Narrower / Wider** change the flat at the bottom of the cut (per cut on Custom keys, all cuts on built-in systems, with Reset width).
4. **Grooves A / B:** on side B the outline is shown flipped, the way the key lies once turned over (⇋ Flip key switches it). with side A up, add bands and drag them over the grooves (the bands carry on past the tip). Turn the key over for side B.
5. **Done** builds the key from the code: exact cut positions, depths and clean V-cuts, your grooves, and your chosen bow. *Build from* on the Build step switches between the decoder and the side photos.

The screen stays awake while the decoder is open (iOS 16.4+ / Chrome). Turn the screen brightness up yourself if the key is hard to see.

### Decode from photos
On the Build step, **🔑 Decode from photos** reads the traced key (blade height and length, every cut's position, depth and width, and the Auto grooves on both sides) and loads it into the decoder. With a key system chosen, each cut is snapped to that system's depths and you get the code; with Custom, the cuts keep their measured positions, depths and widths. Every decoder adjustment then works on it, and Done builds it exactly.

### Code plate bow
For keys built from the decoder: a plate as wide as *Bow size*, with a full-width flat shoulder, a 5 mm keyring hole at the far end and the key's code recessed 0.6 mm into side A (prints well either way up).

## v17: home screen and controller
- **Home screen:** 🔑 Decode a key or 📷 Create from camera (🏠 in the top bar returns here). Continue last key picks up where you left off.
- **Bow defaults:** Camera for camera keys, Code plate for decoded keys (your own choice is remembered per path).
- **D-pad controller** in the decoder: ▲▼ move the cut, ◀▶ depth, centre = next cut, corners = + Cut / − Cut / Narrower / Wider. Blade and Tip below. *Width to all* sets every cut to the selected width, and new cuts follow it until you change one.
- **Grooves:** each groove has its own shape (Square, V, V with flat), flat width and depth (Deeper / Shallower / Reset). *Shape + depth to all* copies the selected groove to the rest. Same pad on the Keyway step's Auto grooves.
- **Live keyway profile:** an end-on view that redraws as you edit grooves (selected groove in orange, thin walls in red).
- **Cleaner screens:** 3D buttons, long help folded into ⓘ, build settings folded into Advanced.

## v18
- **🖼 Decode from photo** (home screen): photograph the key on the card (side B optional), flatten, then **🔑 Decode this photo**. The decoder opens with the photo lined up behind the outline and the cuts pre-filled; pinch to zoom, drag to pan, **✥ Nudge photo** to move or turn it. Grooves B shows the side B photo.
- **Keyway library in the decoder:** 📚 Library picks a keyway (saved decoder keyways load as editable grooves; built-in shapes are converted to grooves, with an *Exact library shape* option). 💾 Save stores the current grooves in the library.
- **Grooves may run off the top or bottom edge** as long as 0.2 mm of the groove is still on the key (only the part on the key is cut).

## v19
- **↺ Start again** on every step (Side A, Side B, Keyway, Build, the decoder page and the on-screen decoder). It asks first, then clears the current photos, traces, cuts, grooves and build, keeps your settings, phone model, key systems, library and bow choices, and returns to the start of the path you're on.

## v20: new look
- New KeyCut3D logo and app icon.
- **Dark mode:** ⚙︎ → Appearance → Theme: Auto (follows your phone), Dark or Light. *Decoder screen* can be Dark or White.
- Red accents for main actions, gunmetal grey for selected items, silver guide lines, amber warnings.
- Arrows are drawn as matching triangles (no emoji boxes on iPhone).

## v21: build from code
- **🔢 Build from code** (home screen): pick a keyway from the library, pick the key system, type the code (checked as you type, with a live outline), then Build. Uses the exact library keyway shape and the Code plate bow.
- **💾 Save as key type** stores keyway + system + blade length together, so next time you just pick the type and type the code.
- Decoded keys show their code on the Build step with **Copy code** and **🔢 Edit code**.
