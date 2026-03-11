# 🗺️ VideoToTab Development Roadmap

This roadmap outlines the phased development of the VideoToTab engine. Progress is balanced with university studies and other active projects.

---

## 🟢 Phase 1: Audio Core & Pitch Extraction (Current Focus)
**Goal:** Handle the base audio data

### Sprint 1: Signal Processing MVP
- [ ] **Task 1.1:** Audio extraction pipeline using `MoviePy` (MP4 to WAV).
- [ ] **Task 1.2:** Note Onset Detection using `Librosa` (Identifying exactly *when* a string is plucked).
- [ ] **Task 1.3:** Fundamental Frequency ($f_0$) detection via FFT.
- [ ] **Task 1.4:** Implementation of Harmonic Product Spectrum (HPS) to identify notes within chords.

---

## 🟡 Phase 2: Computer Vision & Fretboard Mapping
**Goal:** Create a virtual 2D model of the guitar neck to map hand movements.

### Sprint 2: The Virtual Neck
- [ ] **Task 2.1:** Fretboard edge and Nut/Bridge detection using OpenCV (Hough Line Transform).
- [ ] **Task 2.2:** **Perspective Transform:** "Flatten" the angled guitar neck into a 2D rectangular grid.
- [ ] **Task 2.3:** Track hand pose (MediaPipe) to get hand landmarks
- [ ] **Task 2.4:** Map hand landmarks (MediaPipe) onto the 2D grid coordinates.
- [ ] **Task 2.5:** JSON Instrument Profiles (Define string count, tuning, and fret scaling).

---

## 🔴 Phase 3: Sensor Fusion & Confidence Logic
**Goal:** Take a weighted average to determine a best guess for tab data.

### Sprint 3: The Decision Engine
- [ ] **Task 3.1:** String Vibration Detection
- [ ] **Task 3.2:** **Confidence Weighting Algorithm:** Resolve conflicts (e.g., if Audio hears A4 but Hand is at Fret 2).
- [ ] **Task 3.3:** Handle Occlusion: Infer finger position when the hand blocks the camera's view of the fret.

---

## 🔵 Phase 4: Tablature Generation & Export
**Goal:** Turn raw data into a readable musician-ready format.

### Sprint 4: The Final Output
- [ ] **Task 4.1:** Rhythmic Quantization: Snap notes to a BPM grid/time signature.
- [ ] **Task 4.2:** ASCII Tab Generator: Basic text output of the fret/string data.
- [ ] **Task 4.3:** **MIDI Export:** Produce `.mid` files for use in Guitar Pro/Sibelius.
- [ ] **Task 4.4:** "Cowboy Chord" Mode: Detect and label common open chords (G, C, D, etc.).

---

## 🚀 Long-Term Goals (Post-MVP)
- [ ] Support for Capos (Dynamic pitch shifting).
- [ ] Detection of techniques: Slides, Hammer-ons, Pull-offs, and Vibrato.
- [ ] Support for non-standard instruments: Banjo, Mandolin, and Ukulele.
- [ ] Web-based SaaS interface for automated uploads.
