# 🎧 AuraRhythm

**Real-Time Acoustic Harassment, Flicker & Sleep Disruption Detector**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Web Audio API](https://img.shields.io/badge/Web%20Audio-API-blue.svg)]()
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-None-green.svg)]()

---

## 📖 Overview

**AuraRhythm** is a browser-based, single-file acoustic analysis tool designed to detect anomalous, non-musical sound patterns. While traditional audio meters measure *volume* (decibels), AuraRhythm measures *pattern, rhythm, and frequency*. 

It was specifically engineered to identify signatures associated with **acoustic harassment**, **anxiety-inducing fast flickers**, and **sleep-interfering pulses**. By utilizing the Web Audio API to perform real-time Fast Fourier Transform (FFT) analysis, AuraRhythm isolates specific frequency bands to detect irregular bursts, sustained high-frequency electronic whines, and sub-audible low-frequency thumps that standard noise meters easily miss.

Because it runs entirely client-side in a single HTML file, **no audio data ever leaves your device**, ensuring complete privacy and security for sensitive environmental monitoring.

---

## ✨ Key Features

*   **Multi-Band Spectral Analysis**: Splits the audio spectrum into Bass (deep thumps/vibrations), Mid (taps/pulses), and High (electronic flickers/whines) to isolate specific acoustic weapons or disturbances.
*   **Dynamic Thresholding**: Adapts to your room's ambient noise floor. It ignores steady-state noise (like HVAC or traffic) and triggers only on sudden, anomalous *spikes* relative to the local baseline.
*   **Burst Detection & Alerting**: Identifies rapid clusters of sound (e.g., >5 events in 3 seconds) designed to prevent habituation and trigger anxiety. Triggers visual and haptic (mobile vibration) alerts.
*   **Evidence Logging & CSV Export**: Timestamps every detected event with exact energy levels, thresholds, and frequency bands. Exportable to CSV for documentation, pattern analysis, or legal evidence.
*   **Sleep / Low-Distraction Mode**: Dims the UI and suppresses jarring visual flashes, allowing the tool to run silently overnight to monitor for sleep-disruption frequencies.
*   **Live Disruption Chart**: Visualizes acoustic stress over a rolling 60-second window using Chart.js.
*   **Zero-Dependency / Portable**: No build step, no backend, no installation. Just open `index.html` in a modern browser.

---

## 📊 The Disruption Index (DI)

At the core of AuraRhythm v2 is the **Disruption Index**, a proprietary metric that quantifies the "hostility" or "disruptiveness" of the acoustic environment in real-time.

### Why not just use Decibels (dB)?
A loud passing truck or a slamming door registers high on a decibel meter but is usually a harmless, organic environmental event. Conversely, a faint, 8kHz electronic flicker pulsing at 4Hz might register very low in decibels, but is highly effective at disrupting sleep cycles and inducing psychological distress. 

### How the DI is Calculated:
1.  **Frequency Weighting**: Events are scored based on their frequency band. High-frequency flickers (often used to cause anxiety) are weighted heavily (+3 points). Mid-band pulses (+2 points). Bass thumps (+1 point).
2.  **Rolling Window**: The score is plotted on a live, 60-second rolling chart.
3.  **Temporal Decay**: The score naturally decays over time (e.g., `score * 0.7` per second) unless continuously fed by new acoustic events.
4.  **Burst Multipliers**: Rapid Inter-Pulse Intervals (IPI) that indicate machine-generated rhythms trigger exponential spikes in the index.

**Result**: The Disruption Index easily differentiates between a noisy apartment (Low DI) and a targeted, rhythmic acoustic disturbance (High DI).

---

## 🚀 Getting Started

1.  **Download** the `index.html` file from this repository.
2.  **Open** the file in any modern web browser (Chrome or Edge recommended for best Web Audio API performance).
3.  **Click** "Start Microphone" and allow browser permissions.
4.  **Calibrate**: Adjust the **Noise Gate** slider until false positives from your computer fan or room HVAC stop triggering the indicators.
5.  **Monitor**: Leave the tab open. Toggle **Sleep Mode** if monitoring overnight.

---

## 🗺️ Roadmap

AuraRhythm is actively being developed to better serve those experiencing environmental disturbances. 

### Phase 1: Robustness & Background Operation (In Progress)
*   [ ] **AudioWorklet Migration**: Move audio processing off the main thread to a Web Worker to prevent browser tab throttling when the window is minimized.
*   [ ] **Desktop Wrapper**: Package the app using Electron or Tauri to allow true 24/7 background system monitoring without browser memory leaks or sleep policies.

### Phase 2: Advanced Acoustic Signatures
*   [ ] **Spectral Flatness Analysis**: Differentiate between broadband noise (white noise/fans) and narrowband harassment tones (sweeps, whines, and digital artifacts).
*   [ ] **Infrasound Monitoring**: Extend FFT bin analysis to capture sub-20Hz vibrations (Note: requires external USB mic hardware, as laptop mics roll off below 80Hz).
*   [ ] **Inter-Pulse Interval (IPI) Histogram**: Visualize the time between pulses to easily spot artificial, machine-generated rhythms vs. organic sounds.

### Phase 3: AI & Pattern Recognition
*   [ ] **Local TensorFlow.js Classification**: Train a lightweight model to classify "Harassment Signatures" vs "Environmental Noise" (HVAC, traffic, neighbors).
*   [ ] **Sustained Tone Detection**: Add Goertzel algorithm targeting to detect continuous, low-level sine waves designed to mask as tinnitus or cause nausea.

### Phase 4: Evidence Chain
*   [ ] **Ring-Buffer Audio Snippets**: Implement a localized memory ring-buffer that saves 10 seconds of actual audio *only* when a high Disruption Index threshold is crossed. This provides hard proof of anomalies while respecting privacy and storage limits.

---

## ⚖️ Ethical & Legal Disclaimer

*   **Privacy & Consent**: AuraRhythm processes audio entirely in-browser and does not record or transmit audio by default. If you utilize future features that cache audio snippets for evidence, please ensure you are complying with your local jurisdiction's wiretapping and recording consent laws.
*   **Hardware Limitations**: Built-in laptop and phone microphones feature aggressive hardware-level noise cancellation and automatic gain control (AGC), which can mask low-level acoustic harassment. For accurate forensic monitoring, an external USB condenser microphone with AGC disabled is highly recommended.
*   **Psychological Safety**: Monitoring for harassment can be stressful. AuraRhythm includes a "Sleep Mode" and UI dimming to help reduce visual anxiety during long-term monitoring sessions.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! If you have experience with Web Audio API, DSP (Digital Signal Processing), or Electron packaging, your expertise is highly valued.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

*Built with the Web Audio API, Chart.js, and vanilla JavaScript.*
