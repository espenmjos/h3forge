# HotA Portrait Forge

A single-page tool that turns any picture into hero portraits for
**Heroes of Might and Magic III: Horn of the Abyss**. You frame the image, check it at real
game size, and download PCX files that the game can load.

Everything runs in the browser. Nothing is uploaded anywhere; the only network request is for
the Google Fonts used by the page (it works without them, just with fallback fonts).

## Opening it

- **PC:** download `index.html` and double-click it, or open it in any modern browser
  (Chrome, Edge, Firefox).
- **Phone:** open the file in the phone's browser. On a phone you also get a
  **Take a selfie** button that opens the camera.

No install, server or build step is needed.

## Making a portrait

### 1. Frame your hero

1. Load an image in one of these ways:
   - click **Upload an image**,
   - drag and drop a file onto the box,
   - paste an image from the clipboard (Ctrl+V, or the paste box on phones),
   - on a phone, use **Take a selfie**.

   PNG, JPG, WebP, GIF and BMP are supported. The page opens with a sample image so you can
   try the controls first.
2. Pick the tab for the size you are framing:
   - **Large 58×64**: the portrait on the hero screen,
   - **Small 48×32**: the portrait in the adventure-map hero bar.

   Each size is framed separately, so set **both** tabs.
3. Move and zoom:
   - drag to move,
   - scroll, pinch or use the **Zoom** slider to zoom (`+` / `-` also work),
   - arrow keys nudge by one game pixel,
   - **Reset framing** goes back to the default crop.
4. **Use the same image for both sizes** is on by default. Turn it off if you want a different
   picture for the small portrait (for example a tighter crop of the face).

Want a selfie on a PC? The page cannot use a webcam directly. Take a photo with the Windows
Camera app and upload it, or open the page on your phone instead.

### 2. Check the in-game preview

The right-hand panel shows both portraits as they will look in the game: reduced to 256
colours, at 1× and 2×.

**Dithering** mixes neighbouring colours so gradients look smoother instead of blotchy. Try
it on photos with soft lighting. It only affects the 8-bit PCX output.

### 3. Generate and download

1. **Hero to replace:** search for and pick the hero whose portrait you want to replace. The
   file names (for example `HPL000KN.pcx` and `HPS000KN.pcx`) fill in automatically. You can
   edit them by hand if needed.
2. **Formats** (PCX 8-bit and PNG are ticked by default):
   - **PCX 8-bit, 256 colours**: the one to use, tested in game,
   - **PNG**: in case you want to convert the images yourself,
   - **Experimental: H3 native 24-bit**: untested, keep a backup.
3. **1 px black border on the small portrait** matches the look of the original small
   portraits. It is on by default.
4. Click **Generate files**, then **Download ZIP**.

## Installing the portraits in the game

1. Unzip the download.
2. Copy the `.pcx` files into the game's `Data` folder, for example
   `C:\Games\Heroes3\Data`. Back up any files with the same names first.
3. Start the game. The chosen hero now uses your portrait.

Instead of loose files you can also pack them into a `.lod` archive with a tool such as
[MMArchive](https://sites.google.com/site/sergroj/mm/mmarchive).

To remove the custom portrait, delete the files from `Data` again.

## Good to know

- Large portraits are 58×64 px (`HPL…`), small ones 48×32 px (`HPS…`). Both are PCX with at
  most 256 colours.
- Use the **8-bit PCX**. A standard 24-bit PCX shows up as random colours, because the game
  reads portraits as 256-colour images.
- The 8-bit files never use palette entry 0. The game can treat that colour specially, so
  leaving it unused avoids graphic glitches.
- The hero list follows HotA 1.8.1 (including Cove, Factory and Bulwark). File names for the
  156 original heroes are confirmed. For HotA heroes the large file name is confirmed but the
  small name is derived from it, and Bulwark names are not published yet. If a portrait does
  not show up, check the real names in `HotA.lod` with MMArchive and edit the name fields.
- Custom portraits are local to your install. If you share a map that relies on them, the
  other players need the same files in their `Data` folder.
