# 图片素材

- `hero.png`：README 第一屏的前后对照图。源文件是 `hero.html`。
- `ladder-demo.gif`：演示页 0–4 级逐帧截图。源文件是 `../demo/index.html`。

重新生成（macOS + Chrome + ImageMagick）：

```bash
CH="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
"$CH" --headless=new --hide-scrollbars --force-device-scale-factor=2 --window-size=1200,500 --screenshot=hero.png "file://$PWD/hero.html"
```
