---
title: Overview
links:
  - title: A blog about freeing a Maschine Mikro MK3
    description: protocol, bridge hardware and software notes for turning an NI Maschine Mikro MK3 into a plain MIDI controller
menu:
    main:
        weight: 1
        params:
            icon: home

comments: false
toc: false
---
# DIY NI Maschine Mikro

Welcome to the build log for bringing a **Native Instruments Maschine Mikro MK3** online
as a plain, class-compliant MIDI controller -- without any Native Instruments software,
drivers or background services.

## The problem

The Mikro MK3 is a lovely piece of hardware: 16 velocity- and pressure-sensitive RGB pads,
39 buttons, a touch-sensitive push encoder, a two-finger touch strip with its own LED row,
and a small display. But it does not speak MIDI. Over USB it uses its own vendor protocol,
and without NI's software running in the background it is just a dark box.

## The plan

- **A small bridge box** sits between the Mikro and the rest of the world. It is the only
  thing that ever talks the NI protocol. Towards a computer or a hardware synth it is a
  plain MIDI device: pads become notes with velocity and pressure, buttons and the encoder
  become controllers, and incoming MIDI drives the pad colours, button lights and display.
- **A cross-platform desktop editor** (C++) mirrors the hardware surface on screen and
  configures the bridge -- purely through documented MIDI/SysEx, never the NI protocol.
- **Standalone playback**: sequences prepared in the editor are stored on the bridge and
  can be played later without any computer attached.

## How

Same method as the sibling projects
([DIY-MIDI-METRONOME](https://jens-goes-mad.github.io/DIY-MIDI-METRONOME.public/) and the
[Korg Kronos editor](https://jens-goes-mad.github.io/DIY-KORG-KRONOS-EDITOR/)): **no
guessing**. Every detail of the protocol is pinned down with a purpose-built test --
press one control, record what the device sends, compare against what was actually done
-- before it is written down as fact.

This project is the hardware/software side of scratching that itch,<br>
for fun,<br>
thus: [jens-goes-mad](/me).

## Where to look next

- [Protocol](/protocol) -- what the Mikro MK3 sends and accepts over USB, at a glance.
- [Bridge](/bridge) -- the planned bridge hardware and software.
- [Timeline](/timeline) -- the build log.

## Disclaimer

An independent interoperability project, not affiliated with or endorsed by Native
Instruments. "Native Instruments" and "Maschine" are trademarks of Native Instruments GmbH.
No NI software, firmware or code is used or redistributed.
