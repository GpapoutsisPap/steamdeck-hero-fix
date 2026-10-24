# Hero Fix — Steam Deck CSS Loader theme

Brings back the **hero image behind the Game Mode home carousel** after a Steam client update left it black.

A recent Steam update moved the home hero into two new wrapper elements that Steam's own stylesheet hides with `opacity: 0`. Older themes that unhid the hero still target the previous class name, so they no longer match anything and the area behind the carousel is just black. This theme targets the new wrappers.

## What it does

- Makes the hero art visible again behind the home carousel
- Scales the art to the top **62%** of the screen, so less of the image is cropped than at full screen
- Fades the bottom of the art into black behind the game cards
- Removes the white background some themes (e.g. Obsidian) put behind the hero

## Requirements

- [Decky Loader](https://github.com/SteamDeckHomebrew/decky-loader)
- [CSS Loader](https://github.com/DeckThemes/SDH-CssLoader) (install it from the Decky store)

## Installation

1. Download this repository (**Code → Download ZIP**) or a release.
2. Copy the `Hero Fix` folder to:
   ```
   /home/deck/homebrew/themes/Hero Fix/
   ```
   The folder should contain `theme.json` and `shared.css`, not another `Hero Fix` folder.
3. Go back to Game Mode, open **Decky → CSS Loader**, and turn on **Hero Fix**.

## Customizing

Open `shared.css` and change **both** `62vh` values:

| Value   | Result |
|---------|--------|
| `52vh`  | Whole image width visible, more black below it |
| `62vh`  | Default, a balance between filling the screen and cropping |
| `100vh` | Fills the whole screen, crops the sides heavily |

The first line, `--met-hero-art-size`, only matters if you also use a theme that defines that variable. It does nothing otherwise.

## If it stops working

Steam renames its internal CSS classes in some updates. If the hero goes black again, the three class names in `shared.css` have probably changed:

- `.QNkOtW3xS-yj6LviWHvnd` and `._30D-80Lg-Luy-KxOumBlaY` (hero wrappers)
- `img._3Mp8R2wnoCl6ko0HAX8IHE` (the hero image)

You can find the new names with CEF remote debugging (Decky → Settings → Developer → Allow Remote CEF Debugging, then open `http://<deck-ip>:8081` on your PC). Issues and pull requests are welcome.

## Compatibility

Tested on SteamOS Stable, October 2026, alongside Obsidian and other CSS Loader themes.

## License

[MIT](LICENSE)
