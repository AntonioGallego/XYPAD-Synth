# XYPAD-Synth

A browser-based modular synthesizer. No dependencies, no build step — open synth.html and play.

XY Pad is a browser-based modular synthesizer built with vanilla JS and the Web Audio API.

Control pitch and amplitude by dragging a ball around an XY pad. Stack up to 3 oscillators with independent tuning, octave and waveform. 

Shape the sound with a resonant filter, LFO, convolution reverb and a noise generator (white/pink/brown). Sequence melodies with a step arpeggiator, tap tempo and scale selection.

All modules are floating panels — drag them anywhere on screen, collapse them, or toggle visibility from the dock at the bottom. Connect a 

MIDI keyboard for note and velocity input with CC-learn for knob mapping. Plug in a gamepad to control parameters with the analog sticks and trigger play/stop, arp, octave shifts and waveform changes from the buttons.

Runs entirely in the browser, no dependencies, no build step — open the HTML file and play.

Web Audio API · Web MIDI API · Gamepad API · single HTML file


Features
XY Pad
Drag a ball around the pad to control pitch (Y axis, logarithmic 40 Hz–20 kHz) and amplitude (X axis). Works with mouse and touch.
Oscillator
Four waveforms — sine, square, sawtooth, triangle — with an animated oscilloscope that reacts to frequency and amplitude in real time.
Stacker
Three additional oscillators layered on top of the main one, each with independent waveform, octave offset (±2), fine detune (±50 cents) and volume. Enable any combination for unison, chords or sub layers. A live frequency spectrum shows the combined output.
Filter
Resonant biquad filter with four modes — lowpass, highpass, bandpass, notch — and continuous cutoff (40 Hz–18 kHz) and resonance controls.
LFO
Low-frequency oscillator with four waveforms and three modulation targets: pitch, amplitude, or filter cutoff.
Reverb
Convolution reverb with a synthetic impulse response. Mix and decay time controls. Impulse is rebuilt on decay change.
Noise
White, pink and brown noise generator with its own lowpass filter, resonance, and volume. Pink noise uses the Paul Kellett algorithm. Live oscilloscope display.
Arpeggiator
Step sequencer with 8 programmable steps. Each step can be toggled on/off and given an individual octave offset (±2 octaves via dot grid). Controls: BPM slider, tap tempo, scale (major / minor / pentatonic / blues / chromatic), direction (up / down / up-down / random), octave range and gate length.
MIDI
Connect any MIDI keyboard via the Web MIDI API (Chrome/Edge). Notes map to pitch, velocity maps to amplitude. Pitch bend, mod wheel (→ LFO depth) and CC-learn for four parameters: filter cutoff, BPM, reverb mix, noise volume.
Gamepad
Connect any standard gamepad (USB or Bluetooth). Both analog sticks are fully remappable to: frequency, amplitude, filter cutoff, resonance, LFO rate, LFO depth, reverb mix, noise volume, BPM or stacker detune. Face buttons control play/stop, arp toggle, octave shifts and waveform cycling. Shoulder buttons adjust BPM. D-pad controls LFO depth.

Interface
All modules are floating panels — drag them anywhere by their title bar.
A dock at the bottom of the screen shows a button for every module. Click to show or hide. The dock itself is also draggable. Modules that are always shown by default: PAD, OSC, PLAY. All others start hidden.
Dock buttonModulePADXY PadOSCOscillator + waveformPLAYTransportFTRFilterLFOLow-frequency oscillatorREVReverbSTKStacker (multi-oscillator)NSENoise generatorARPArpeggiatorMIDIMIDI keyboard inputGPGamepad controller

Browser support
FeatureChromeEdgeFirefoxSafariWeb Audio API✓✓✓✓Web MIDI API✓✓✗✗Gamepad API✓✓✓✓
MIDI requires Chrome or Edge. Everything else works in any modern browser.

Usage
# No install required
open synth.html
Or serve locally if your browser blocks file:// MIDI access:
bashnpx serve .
# then open http://localhost:3000/synth.html

Signal flow
XY Pad ──► Oscillator ──┐
Stacker ────────────────┼──► Filter ──► Dry ──────────────► Output
Noise ──────────────────┘         └──► Convolver (Reverb) ──► Output
LFO modulates: oscillator frequency · amplitude · filter cutoff
MIDI / Gamepad override: pad position · filter · reverb · noise · BPM
