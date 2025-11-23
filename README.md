# Android Boot Animation Previewer 📱

A lightweight, browser-based tool to preview Android custom boot animations (`bootanimation.zip`) instantly.
This tool runs entirely on the client-side using JavaScript, meaning your files are processed locally in your browser and are never uploaded to a server.

## ✨ Features

* **Instant Preview:** Drag and drop your `bootanimation.zip` to see it in action.
* **Accurate Parsing:** Reads `desc.txt` to strictly follow Android's playback logic (resolution, FPS, loops, and pauses).
* **Privacy First:** Uses JSZip to unzip and render files in memory. No data leaves your device.
* **Playback Controls:** Play, pause, and reset the animation sequence.
* **Responsive UI:** Built with Tailwind CSS, featuring a dark mode interface and a simulated phone frame.
* **Single File:** The entire application is contained within a single HTML file for easy portability.

## 🚀 How to Use

### Hosted Version
*(If you are using GitHub Pages, replace the link below with your actual URL)*

[Click here to use the live previewer](#)

### Local Usage
1.  Download the `index.html` (or `boot_preview.html`) file from this repository.
2.  Open the file in any modern web browser (Chrome, Firefox, Edge, Safari).
3.  Click the upload area or drag a `bootanimation.zip` file onto the window.

## 🛠️ Technical Details

The tool simulates the Android `bootanim` binary logic:

* **Unzipping:** Uses JSZip to extract the archive in browser memory.
* **Configuration:** Parses the `desc.txt` file to determine:
    * Screen resolution (Width/Height)
    * Frame rate (FPS)
    * Parts configuration (p/c, count, pause, folder path)
* **Rendering:** Frames are converted to `ImageBitmap` objects for high-performance rendering on an HTML5 `<canvas>`.
* **Timing:** Uses `requestAnimationFrame` with delta time calculations to maintain the target FPS specified in the zip file.

### Supported desc.txt Format
The tool supports the standard Android format:

```text
<width> <height> <fps>
p <count> <pause> <folder>
c <count> <pause> <folder>
