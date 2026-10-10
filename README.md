# series-01-web-vitals

> **Cracking Web Vitals with Telemetry (INP, CLS, LCP)**  
> *"Your code works on `localhost:3000`. Here is how it survives 10 million users."*

[![Instagram](https://img.shields.io/badge/Instagram-@beyondlocalhost.dev-E4405F?style=flat-square&logo=instagram)](https://instagram.com/beyondlocalhost.dev)
[![Series](https://img.shields.io/badge/Series-01_of_06-10B981?style=flat-square)](#)

Enterprise UI engineering is not measured by how an app behaves on an M-series MacBook. It is defined by **P99 Core Web Vitals under CPU contention, device thermal throttling, and real-world event loop pressure**.

This repository contains the reproduction benchmarks, profiler traces, and production implementations for all 5 episodes of **Series 01**.

---

## 📺 Series 01 Episodes & Resource Index

### Episode 01: Debugging High INP with Chrome Performance Profiler
- **The Problem**: A user clicks a filter checkbox, but the main thread locks for 450ms due to synchronous data transformations, failing INP in production.
- **The Difference**:
  - `Naive`: Synchronous computation inside the click handler blocking paint frames.
  - `Enterprise`: Offloading transformations via Web Workers or chunking work via `scheduler.yield()`.
- **Resources**:
  - 🎬 [Watch Breakdown on Instagram](https://instagram.com/beyondlocalhost.dev)

---

### Episode 02: Eliminating CLS in Dynamic Media Grids
- **The Problem**: Images and dynamic ad slots load asynchronously without reserved geometry, causing violent layout shifts (CLS > 0.25).
- **The Difference**:
  - `Naive`: Unbounded `<img>` tags waiting for network headers to calculate aspect ratio.
  - `Enterprise`: Modern CSS `aspect-ratio` bounding containers, placeholder skeleton anchoring, and containment context (`contain: layout`).
- **Resources**:
  - 🎬 [Watch Breakdown on Instagram](https://instagram.com/beyondlocalhost.dev)

---

### Episode 03: Cracking LCP Discovery with Priority Hints
- **The Problem**: Above-the-fold hero images hidden behind script waterfalls and CSS background rules, delaying LCP past 3.5s on mobile networks.
- **The Difference**:
  - `Naive`: Late-discovered background images or vanilla `<img>` tags without browser priority hints.
  - `Enterprise`: Native `fetchpriority="high"`, `<link rel="preload">`, and HTTP 103 Early Hints.
- **Resources**:
  - 🎬 [Watch Breakdown on Instagram](https://instagram.com/beyondlocalhost.dev)

---

### Episode 04: Zero-Loss GA4 Web Vitals Streaming
- **The Problem**: In-flight performance beacons get discarded when users close the tab or navigate away, leading to survivor-bias telemetry.
- **The Difference**:
  - `Naive`: Firing `fetch()` / `XMLHttpRequest` inside `beforeunload` or component unmount hooks.
  - `Enterprise`: Transport via `navigator.sendBeacon` with `fetch(..., { keepalive: true })` fallback and RUM session queueing.
- **Resources**:
  - 🎬 [Watch Breakdown on Instagram](https://instagram.com/beyondlocalhost.dev)

---

### Episode 05: Cooperative Scheduling & Main-Thread Yielding
- **The Problem**: Heavy client-side jobs using `setTimeout(fn, 0)` encounter 4ms browser clamping penalties and starve high-priority user interactions.
- **The Difference**:
  - `Naive`: Recursive `setTimeout` loops assuming the main thread yields cleanly.
  - `Enterprise`: Cooperative scheduling using `navigator.scheduling.isInputPending()` and native `scheduler.yield()`.
- **Resources**:
  - 🎬 [Watch Breakdown on Instagram](https://instagram.com/beyondlocalhost.dev)

---

## 🎯 The Tier-1 Machine Coding Trap

In machine coding rounds at Tier-1 companies (**Walmart, Uber, Atlassian, Google, Stripe**), interviewers rarely fail candidates on syntax or basic state management.

They fail candidates on **runtime realities**:
1. **The Mock Data Trap**: Candidates build a UI with 10 dummy items and assume it works. The interviewer tests it with 25,000 items under 4x CPU throttling, and the tab locks up.
2. **Ignoring Frame Budgets**: Candidates write synchronous data transforms inside click handlers, unaware that every frame over 16.6ms drops UI responsiveness.
3. **No Telemetry Mindset**: Candidates cannot explain how they would measure or defend their component's INP, CLS, or memory footprint in production.

If you cannot defend your code against browser internals, frame budgets, and garbage collection pauses, you will get down-leveled or rejected at the Staff/Senior bar.

---

## 💼 Level Up Your System Design & Machine Coding

Navigating the transition from service firms to top-tier product tech requires proof of runtime depth, architectural rigor, and interview execution.

> **The Trajectory**: Navigated the exact transition from **Infosys ➔ Lowe's ➔ Walmart**. I work 1:1 with engineers looking to clear the Tier-1 bar.

### 🎯 [Book a 60-Minute Tier-1 Machine Coding Mock Round][Comming Soon ....]
- Live 1:1 coding session simulating actual machine coding rounds at Walmart, Uber, and Atlassian.
- Stress-tested against runtime performance, frame budgets, edge cases, and architectural modularity.
- Direct, unvarnished Staff-level feedback, code review, and scoring rubric.

### 🚀 [Book a 60-Minute Service-to-Product Resume & Strategy Audit][Comming Soon ....]
- A tactical blueprint for developers transitioning from service firms (Infosys, TCS, Wipro, Cognizant) to Tier-1 product tech.
- Line-by-line resume rewrite: converting basic CRUD bullet points into high-signal architectural impact.
- Personalized preparation roadmap for clearing Tier-1 screens.

---

*Part of the **Beyond Localhost** engineering ecosystem.*  
*Instagram: [@beyondlocalhost.dev](https://instagram.com/beyondlocalhost.dev)*
