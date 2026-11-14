# Architecture decisions

## Initial shape

- Native Android application using Kotlin and Jetpack Compose.
- minSdk 26; Java 17; Android SDK 35.
- Offline-first data flow: photo -> on-device vision inference -> structured food candidates -> portion confirmation -> nutrition database lookup -> local meal record.
- Model runtime and model weights are separate decisions. Model files will not be committed to Git.
- AI estimates must be labelled as estimates. Database matches, user-entered weights and inferred portions must remain distinguishable.

## Device constraint

The first target is a Snapdragon 685 phone with 6 GB physical RAM. The OS, camera pipeline and Compose UI also need memory. Benchmark peak memory, cold-start time, photo inference time, thermal behavior and battery use before selecting a default model. Provide text/manual logging if photo inference is too slow or unavailable.

## Integration policy

No upstream code is copied in the bootstrap. Each future integration must record its source commit, file-level changes, license, required notices and model/data terms in THIRD_PARTY.md.
