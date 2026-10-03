---
title: Bridge
links:
  - title: The bridge box
    description: planned hardware and software that turns the Mikro MK3 into a MIDI device
menu:
    main:
        weight: 20
        params:
            icon: circuit-switch-open

comments: false
toc: true
---
# The bridge box

**Status: planning.** Nothing here is built yet; this page describes the direction.

## Idea

```text {linenos=false}
  Maschine Mikro MK3
          │
          │ USB (NI protocol)
          ▼
     ┌──────────┐
     │  Bridge  │
     └──────────┘
       │      │
       │      └── DIN MIDI ──▶ hardware synths
       │
       │ USB-MIDI (class compliant)
       ▼
  Computer / DAW
```

The bridge is the only component that talks to the Mikro directly. Everything else sees a
normal, class-compliant MIDI device -- no drivers on any computer, and it works with
hardware synths too.

## Software

- **One protocol core, written once** in portable C++, with no dependency on any operating
  system or framework. It already decodes everything the Mikro sends and is tested against
  real recordings from the device.
- The same core runs **on the bridge** and in **desktop tools**, so new ideas can be tried
  on a computer before they go into firmware.
- A **cross-platform desktop editor** mirrors the surface on screen and configures the
  bridge through documented MIDI/SysEx.

## Hardware (open)

The bridge has to be a USB **host** for the Mikro and a USB **device** towards the
computer at the same time -- many small microcontrollers can only do one of the two.
Candidates are being compared; the choice comes once the protocol side is complete.

A 5-pin DIN MIDI port is planned in any case: it is what makes **standalone playback**
possible, when there is no computer at the other end of the USB cable.
