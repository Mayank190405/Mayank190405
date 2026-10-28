# ⚡ Selection Sort & Array Algorithm Visualizer

An interactive algorithm visualization engine designed for **Mayank Bajaj's** GitHub profile, styled with warm terracotta `#D97757`, amber, and dark stone tones.

## Features

- **Custom Number Array Input**: Users can enter their own array of numbers (e.g. `[64, 25, 12, 22, 11]`) or load presets (Random, Reversed, Nearly Sorted, Duplicates).
- **Step-by-Step Selection Sort**: Shows the scanning pointer (`SCAN`), minimum candidate (`MIN`), and target index (`i`), followed by the swap animation.
- **Audio Feedback**: Built-in sound synthesis via Web Audio API generating distinct frequencies on comparisons and swaps without external audio files.
- **Live Explanation Log**: Human-readable descriptions explaining why each element is selected and swapped in real-time.
- **Complexity Metrics**: Displays active comparison counts, swap counts, and algorithmic asymptotic complexity ($O(n^2)$ time, $O(1)$ auxiliary space).

## 1-Click Play on GitHub Pages

1. In your GitHub repository (`Mayank190405/Mayank190405`):
2. Go to **Settings** > **Pages**.
3. Under **Build and deployment** > **Branch**:
   - Select `main` branch.
   - Folder: `/ (root)` or `/visualizer`.
4. Your visualizer will be live at:
   `https://mayank190405.github.io/visualizer/`
