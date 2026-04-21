<p align="center">
  <img src="https://github.com/REMvisual/td-CurveTool/releases/download/v2.0/banner.svg" alt="CurveTool Free v2.0" width="100%">
</p>

[![Download Latest](https://img.shields.io/github/v/release/REMvisual/td-CurveTool?style=for-the-badge&label=Download&color=blue)](https://github.com/REMvisual/td-CurveTool/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/REMvisual/td-CurveTool/total?style=for-the-badge)](https://github.com/REMvisual/td-CurveTool/releases)
![Views](https://komarev.com/ghpvc/?username=REMvisual-td-CurveTool&label=Views&color=brightgreen&style=for-the-badge)
[![Upgrade to Pro](https://img.shields.io/badge/Upgrade-CurveTool%20Pro-ff7733?style=for-the-badge)](https://remrepo.com/buy/curvetool/)

Interactive curve editor + LFO for TouchDesigner 2025.x. Draw custom envelopes and waveform shapes on an HTML Canvas UI, output as a CHOP driven by any timing source — LFO, beat, timeline, or external signal.

## What It Does

Forget Animation COMPs and keyframe editors. Drop the `.tox` into any project, draw the shape you want with bezier or linear control points, and the curve flows out as a CHOP ready to drive anything — envelopes, audio-reactive visuals, parameter automation, animated camera pulls.

- **HTML Canvas UI** inside TouchDesigner via WebRender TOP — full-res, system-fonted
- **Custom curve CHOP output** — 256-sample Script CHOP ready to wire into a Lookup CHOP
- **Per-point bezier / linear toggle** — click a control point to switch interpolation
- **13 built-in presets** — linear, sine, triangle, sawtooth, sawtooth reverse, square, ease in/out/in-out, exp attack/decay, S-curve, noise (random)
- **Save and recall** — save the current curve with a generated name, recall any saved preset
- **Speed slider** — leftmost position freezes the LFO (speed 0); logarithmic 0.01–20 Hz; BPM-sync mode (30–300 BPM)
- **Forward playback** — ramp 0→1 continuously
- **State persists** across re-init and `.toe` save/load
- **Replicable `.tox`** — drop copies into any project; each instance is fully isolated

## Install

**Requires TouchDesigner 2025+**

1. **[Download `CURVETOOL_FREE_v2.tox`](https://github.com/REMvisual/td-CurveTool/releases/latest)** from Releases
2. Drag it into your TouchDesigner project
3. The component self-initialises on load — nothing else to set up

## Wire the Output

The component exposes two Out CHOPs:

| Out | Content |
|---|---|
| `out1` | raw curve samples (from `curve_output`) |
| `out2` | LFO-modulated output — the curve sampled at the internal LFO's phase every frame |

Typical patterns:

- **Built-in LFO** — read `out2` and you're done.
- **Drive it yourself** — ignore the LFO, read `out1`, feed it into your own Lookup CHOP with your own timing source.

## Interaction

| Action | Result |
|---|---|
| **Double-click** empty area | Add a control point |
| **Click** a point (no drag) | Toggle bezier / linear for that segment |
| **Drag** a point | Move it (endpoints are x-locked) |
| **Right-click** a point | Delete it (minimum 2 points enforced) |

## Upgrade to Pro

**[CurveTool Pro →](https://remrepo.com/buy/curvetool/)**

| | Free | Pro |
|---|:---:|:---:|
| Curve layers | 1 | 4 |
| Built-in presets | 13 | 13 + multi-layer |
| Save / recall presets | ✓ | ✓ |
| LFO playback modes | Forward | Forward, Reverse, Ping-Pong, One-Shot, Step, Random, Drunk |
| Morph between presets | — | ✓ (6 easing curves, loopable) |
| Transform panel | — | Quantize, Ease, Punch, Noise, Mirror, Flip-Y |
| Audio-reactive modulation | — | Envelope, Spectral, Beat |
| State persistence | ✓ | ✓ |

## Licence

MIT — see [LICENSE](LICENSE).
