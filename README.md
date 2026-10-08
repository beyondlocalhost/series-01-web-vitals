# series-01-web-vitals
Cracking Web Vitals with Telemetry (INP, CLS, LCP)


# Episode 01: Debugging High INP with the Chrome Performance Profiler

[![Watch Breakdown](https://img.shields.io/badge/Watch%20Reel-Instagram-E4405F?style=flat-square&logo=instagram)](https://www.instagram.com/beyondlocalhost.dev)
[![Full Video](https://img.shields.io/badge/Full%20Deep%20Dive-YouTube-red?style=flat-square&logo=youtube)](https://www.youtube.com/@beyondlocalhost-dev)

### The Problem
A user clicks a filtering checkbox, but the browser main thread is locked for 450ms by synchronous data transformations, resulting in a failing Interaction to Next Paint (INP) score in Google Analytics.

### The Naive vs. Enterprise Difference
* **Naive:** Heavy synchronous computations inside the click handler blocking paint frames.
* **Production Grade:** Offloading transformations via Web Workers or chunking work with `scheduler.yield()`.

### How to Run Locally
```bash
git clone [https://github.com/beyondlocalhost/series-01-web-vitals.git](https://github.com/beyondlocalhost/series-01-web-vitals.git)
cd series-01-web-vitals/episodes/01-inp-profiler-telemetry
npm install
npm run dev
