# AI-Powered Sign Language Translator — Prototype

A browser-based, two-way ASL ⇄ English translator built for our capstone.

**Team:** Zamijah Shakeur-Tompkins · Kafilat Sarki-Umar · Kwaku Asare · Reihanna Marrett · Ezichi Chimezie

## Try it
Open the GitHub Pages link for this repository in **Chrome or Edge**, click **Start camera**, and allow camera access.
No install is needed. Hand, face and pose tracking run on your device with MediaPipe, and video is never uploaded.

No camera? Open the **Demo signs** tab and press **▶ Play sample conversation**.

## What it does
| Feature | How |
|---|---|
| F1 Camera & landmarks | MediaPipe Hand (21 pts × 2 hands), Face (with blendshapes) and Pose landmarkers |
| F2 Preprocessing & segmentation | Palm-frame normalization, frame smoothing, automatic phrase end when hands drop, low-light / occlusion warnings |
| F3 Recognition | Built-in alphabet (21 static letters + I-LOVE-YOU), per-user alphabet calibration, trainable word signs (kNN), rule-based gloss → English, confidence filter (< 70% → "Sign unclear") |
| F4 Speech & text | Web Speech API speech-to-text with noise suppression; typed fallback |
| F5 Conversation UI | Colour-coded two-way thread, text-to-speech, adjustable text size, high-contrast mode |
| F6 Edge runtime | All vision inference in-browser (WASM / GPU); debug overlay for FPS, latency and memory |

Click **Requirements** in the app to see coverage of R1–R20 from our traceability matrix.

## Measuring accuracy
In **Teach a sign** → **Calibrate all letters** (or just A E M N S T), then **Test accuracy**. The test reports the score against our 85% target and lists which letters were confused.

## Notes
- Needs an internet connection the first time (MediaPipe library and models, ~10 MB), after which the browser caches them.
- If a network blocks `storage.googleapis.com`, download the `.task` model files linked in the error message and use **Load model files**.
- In Chrome, speech recognition audio is processed by Google's speech service. Video stays on the device.
- Recognition is a prototype: continuous sentence translation (ST-GCN / Transformer) and a WLASL-trained word model are still to come.

## Run locally
Open `index.html` in Chrome, or run `python3 -m http.server` in this folder and open http://localhost:8000.
