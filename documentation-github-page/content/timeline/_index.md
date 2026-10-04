---
title: Timeline
links:
  - title: Build log
    description: milestones in the Maschine Mikro build, roughly in order
menu:
    main:
        weight: 30
        params:
            icon: calendar-stats

comments: false
toc: false
timeline:
  - label: "2026-10-02"
    title: "Project start"
    weight: 10
    body: "
Goal set: bring an NI Maschine Mikro MK3 online as a plain MIDI controller via a
small bridge box, with a desktop editor and standalone playback. See
[Overview](/overview)."
  - label: "2026-10-03"
    title: "It is HID, and needs no init"
    weight: 20
    body: "
First look at the device on macOS: a standard USB HID device with vendor
reports, no custom driver required, and it talks without any initialisation."
  - label: "2026-10-03"
    title: "Every input mapped"
    weight: 30
    body: "
Pads (velocity, pressure, release), all 39 buttons, the encoder with push and
touch, and the two-finger touch strip -- each verified one control at a time.
A portable C++ decoder is tested against the real recordings. See
[Protocol](/protocol)."
  - label: "2026-10-03"
    title: "Every light mapped"
    weight: 40
    body: "
All 80 lights: button brightness, and a 16-hue + white palette with 4
brightness levels for the pads and the touch strip LEDs. Confirmed again after a
cold start without any NI software."
  - label: "2026-10-03"
    title: "First host program"
    weight: 50
    body: "
A desktop program now detects the Mikro when it is plugged in, lights all LEDs
as a visible signal, shows every event, and turns the lights off on exit --
including unplug and replug. See [Bridge](/bridge)."
  - label: "2026-10-03"
    title: "Display mapped"
    weight: 60
    body: "
The 128 x 32 display can be drawn pixel by pixel. With that, every control,
every light and the screen are mapped. See [Protocol](/protocol)."
---
# Timeline

A running log of build milestones, roughly in order.

{{< timeline >}}

---

MORE TO COME
