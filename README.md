# CalorieAI Offline

An open-source Android nutrition tracker focused on private, on-device food-photo understanding and offline-first food logging.

## Project status

**Bootstrap stage — not yet a functional Cal AI replacement.** The first commit establishes the native Android/Jetpack Compose foundation and a public GitHub Actions debug-APK workflow. The local vision model, food database, portion estimation, meal history and nutrition dashboard are not integrated yet.

## Product direction

- Take a meal photo and identify likely foods.
- Estimate portions with explicit uncertainty and user correction.
- Calculate calories, protein, carbohydrates and fat using a grounded nutrition database where possible.
- Keep meal history and personal data on-device.
- Work offline after model and food data have been downloaded.
- Offer optional online providers only as an opt-in enhancement, never as a requirement.

## Target device

Initial performance target: Xiaomi Redmi Note 13 4G, Snapdragon 685, 6 GB RAM. Model selection will be based on real device tests; 6 GB RAM is a constraint, not a guarantee that a particular vision model will run smoothly.

## Build

The GitHub Actions workflow builds a debug APK on pushes, pull requests and manual dispatches. It uses a standard GitHub-hosted Linux runner and does not require a paid API key.

For a local build, install JDK 17, Android SDK platform 35 and Gradle 8.9, then run:

```bash
gradle --no-daemon :app:assembleDebug
```

## Upstream research

Projects under evaluation (not copied into this repository yet):

- [Chompass](https://codeberg.org/fitguyfitguy/chompass) — Android nutrition app and on-device model work; GPL-3.0.
- [NomAI](https://github.com/breejesh/nom.ai) — offline-first Android meal extraction and nutrition estimation; MIT.
- [Fud AI](https://github.com/apoorvdarshan/fud-ai) — broader nutrition and fitness feature set; MIT.

Before reusing implementation code, each component will be reviewed for its license, attribution requirements, model license and compatibility. Chompass-derived code requires preserving GPL-3.0 obligations.

## Roadmap

1. [x] Create native Android project foundation.
2. [x] Add public CI workflow for debug APK builds.
3. [ ] Verify first CI build and download artifact.
4. [ ] Audit local inference engines and model redistribution terms.
5. [ ] Benchmark supported vision models on the Redmi Note 13 4G.
6. [ ] Integrate offline food recognition and structured output.
7. [ ] Add grounded nutrition database and portion correction.
8. [ ] Build meal history, goals and nutrition dashboard.
9. [ ] Test fully offline behavior and APK size/performance.

## Privacy principle

Meal photos and nutrition history should remain on the device by default. Any network feature must be optional, visible and documented.
