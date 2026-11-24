# EyeTrack Explorer

An interactive explainer of eye tracking and of how web page design shapes where people look. Built as the individual blog for the DIET course at ETH Zürich (spring 2026).

**Live:** https://belown.github.io/EyeTrack_Explorer/

## What is in it

- **What is Eye Tracking?** Fixations, saccades and scanpaths, a short history of the field (from the first eye-movement studies and the corneal-reflection method to mobile and AI-assisted tracking), and where eye tracking is applied today.
- **How Eyes Scan a Page.** The F-pattern, Z-pattern, Gutenberg diagram and layer-cake pattern, each with an interactive demo.
- **What Shapes a Scanpath?** The design factors that pull attention, such as headline size, image size, colour and advertising, shown on simulated scanpaths.
- **Scanpath Challenge.** Adjust a page's design and watch a simulated viewer's scanpath change. A dynamic time warping (DTW) score shows how close your scanpath is to a target one.
- **Interactive Sandbox.** A webcam eye-tracking experiment built on WebGazer: calibrate, validate, then view a few page variants (headline size, cold or warm call to action, image size, with or without ads). Each one ends with a heatmap of your gaze and a comparison of your real scanpath with the simulated one.
- A light and a dark theme.

The scanpath simulator (`src/utils/scenewalkSimulator.js`) follows the SceneWalk model:

- Engbert, R., Trukenbrod, H. A., Barthelmé, S., & Wichmann, F. A. (2015). Spatial statistics and attentional dynamics in scene perception. *Journal of Vision*, 15(1):14. https://doi.org/10.1167/15.1.14
- Schwetlick, L., Rothkegel, L. O. M., Trukenbrod, H. A., & Engbert, R. (2023). A dynamical scan-path model for task-dependence during scene viewing. *Psychological Review*, 130(3), 799–821. https://doi.org/10.1037/rev0000379
- Tatler, B. W. (2007). The central fixation bias in scene viewing. *Journal of Vision*, 7(14):4. https://doi.org/10.1167/7.14.4

## Run it locally

```bash
npm install
npm run dev
```

Then open the address Vite prints. The webcam experiment needs camera permission, and browsers only grant it on `localhost` or over HTTPS.

## Tech

React 19 and Vite, Framer Motion for animation, Zustand for state, and WebGazer (with MediaPipe face mesh, served from `public/`) for webcam gaze estimation.

## Deploy

Every push to `main` builds the site and publishes it to GitHub Pages (`.github/workflows/deploy.yml`). The `base` in `vite.config.js` must match the repository name (`/EyeTrack_Explorer/`); if the repository is renamed, change it too, or the published page loads blank.
