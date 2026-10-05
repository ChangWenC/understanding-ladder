# Assets

- `hero-en.png` / `social-preview.png`: English before/after (README first screen; GitHub social preview, 1280×640). Source: `hero-en.html`.
- `hero.png`: Chinese before/after for `README.zh-CN.md`. Source: `hero.html`.
- `ladder-demo-en.gif` / `ladder-demo.gif`: rung 0–4 frames of `../demo/index.html` (`?lang=en` / `?lang=zh`).

Re-render (macOS, Chrome, ImageMagick):

```bash
CH="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
"$CH" --headless=new --hide-scrollbars --force-device-scale-factor=2 --window-size=1200,600 --screenshot=hero-en.png "file://$PWD/hero-en.html"
magick hero-en.png -resize 1280x640 social-preview.png
```
