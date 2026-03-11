# VideoToTab
Accept a video of a person playing guitar as input and use the visual &amp; auditory data to produce tablature of what that person played.

## Components
- Hand Pose Tracking
  - MediaPipe Hands (Hand tracking library) and/or YOLO for tracking hand/guitar
  - Use this data combined with fretboard data to determine what frets are being pressed

- Fretboard Detection
  - Detect the edge of the fretboard, the nut and/or capo, visible frets, and strings to build a virtual model of the fretboard and map hand tracking data to specific frets. Use a perspective transform to flatten neck to simplify determining fret. 

- String vibration detection
  - Visually identify when a string is vibrating and which string it is
 
- Pitch Detection
  - Fast Fourier Transform (FFT) to pull out key pitches being played. Combine with data about the harmonic series and interference to handle polyphonic sounds. 

- Rhythmic Mapping
  - Detect a likely time signature and map the time notes are played to their nearest grid points. Will require Onset Detection (librosa.onset is a potential library).
  - Latency Compensation to account for video/auditory differences.
 
- Tablature
  - Draw a tab using rhythm, pitch, and hand position data. Future features can be the detection of techniques such as slides, hammer-ons/pull-offs, dead notes, etc. 
 
- Confidence Weighting:
  - Each component can return a value and a confidence. We can then take a weighted average of each component to identify what is being played in the video and produce tablature. 

## Long Term Goal
- Create this pipeline in a way that it can easily be extended to similar instruments such as the Mandolin, Banjo, Bass, etc.
- Get instrument-specific info from a JSON configuration file that can be swapped out (string count, tuning, fret spacing, scale length, etc.)
- Have a mode for cowboy chords for simple strummed songs that don't require full tabs.
- Midi export feature

⚖️ Licensing
This project is licensed under the GNU GPLv3 for open-source use. If you are a company interested in using this technology in a proprietary or closed-source product, please contact me at sam.mallia101@gmail.com to discuss a commercial license.
