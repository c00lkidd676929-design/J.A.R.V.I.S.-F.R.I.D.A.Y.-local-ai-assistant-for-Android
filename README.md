# JARVIS & FRIDAY — Android local AI app

This repository is the native Android wrapper/runtime project for the supplied JARVIS–FRIDAY HTML interface.

## What is included

- Existing HTML interface copied to `app/src/main/assets/index.html`.
- Android WebView shell with a JavaScript bridge.
- Native `llama.cpp` integration built from the pinned upstream source tag `b4517`.
- GGUF download/import manager.
- One-model-at-a-time loading: general and coding models are stored separately, but only one is loaded in memory at once.
- Basic automatic routing from coding-related prompts to the coding model, otherwise to the general model.
- Separate JARVIS/FRIDAY prompts, histories, and memories remain in the HTML UI's existing storage logic.
- GitHub Actions workflow to build a debug APK.

## Build

The GitHub Actions workflow builds `app-debug.apk` when pushed to `main`, or when manually run from Actions.

## Model setup

Install the app, tap **LOCAL AI MODELS**, and paste a direct HTTPS `.gguf` download URL or import a model file.

The app does not bundle model weights. GGUF files are large and should not be committed to GitHub.

## Important hardware note

The selected quantization and model size determine whether a phone can load a model. A Q8 17B model needs substantially more than 17 GB of memory once runtime/context overhead is included; a phone advertising 16 GB including virtual RAM may not be able to run it. This project does not promise that the requested 17B Q8 model will fit.

## Current status

This is an initial integration build, not a verified release APK. The Android native interface and C++ API need a successful CI compile and on-device testing before the app can be called working. The first compile may expose upstream API/build adjustments.
