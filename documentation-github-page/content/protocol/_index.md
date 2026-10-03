---
title: Protocol
links:
  - title: The Mikro MK3 over USB
    description: what the device sends and accepts, at a glance
menu:
    main:
        weight: 10
        params:
            icon: cpu

comments: false
toc: true
---
# The Mikro MK3 over USB

An overview of what we have verified so far on a real unit. Everything here was checked
with purpose-built tests on our own device (firmware 0.52) -- nothing is copied from
elsewhere or assumed.

## A HID device, not "raw USB"

The Mikro MK3 enumerates as a **standard USB HID device** (Full Speed) with
vendor-defined reports. That is good news: every major operating system can talk to it
through its built-in HID support, and so can a microcontroller with a USB host port --
no custom driver needed.

A second interface on the device is for **firmware updates**. We never touch it.

**No initialisation is needed.** Straight after plugging in -- with no NI software ever
running -- the device reports every touch and accepts lighting commands. Nothing is sent
while nobody touches it.

## What comes in

| Control | What the device reports |
|---|---|
| 16 pads | press with a strike value (usable as velocity), a continuous pressure stream while held, release |
| 39 buttons | pressed / released, one per button |
| Encoder | relative turns (no end stops), push, and touch (capacitive) |
| Touch strip | position of up to **two fingers**, plus lift |

The pads are fast and fine-grained: a soft press and a hard hit are clearly apart, and
pressure is reported many times per second -- enough for polyphonic aftertouch.

## What goes out

**80 individually addressable lights** in a single update:

| Lights | Control |
|---|---|
| 39 button LEDs | brightness; each button has its own fixed colour |
| 16 RGB pads | a colour palette of **16 hues plus white**, each at **4 brightness levels** |
| 25 touch strip LEDs | the same palette as the pads |

The **display** is next on the list and not mapped yet.

## How it was verified

One control at a time: a short recording of the raw USB traffic while a single, stated
action is performed ("press the bottom-left pad three times, soft to hard"), then a
comparison of the bytes against that action. For the lights it runs the other way round:
light exactly one thing, and note what the device shows. Wherever two observations
disagreed, a dedicated follow-up test settled it -- several early readings were corrected
this way.

The detailed byte-level reference, the recordings and the test tools live in the
project's source repository.
