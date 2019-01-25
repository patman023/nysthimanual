# NYECHOecoeco

Author: Santiago L. Peraza (@Funk-Burasuta)

Editor: Pat McIlveen (@patman023)

Last Updated: 2019/01/24

Last Patch: 0.6.38

---

**INDEX**

1. [Antonio Says](#antonio-says)
2. [Basics](#basics)
3. [Functions by Section](#functions-by-section)
   - [Section A: The Teensy Tiny Speed Controls](#section-a--the-teensy-tiny-speed-controls)
   - [Section B: The Spinning Reel and its Playheads](#section-b--the-spinning-reel-and-its-playheads)
   - [Section C: Playhead Controls](#section-c--playhead-controls)
   - [Section D: Mix](#section-d--mix)
   - [Section E: Signal Interface](#section-e--signal-interface)
4. [Usage](#usage)
5. [Sample Patches](#sample-patches)
   
---

## Antonio Says:
```
	0.5.10.0
a virtual BINSON Echorec homage, with 6 play HEADS

PARAMETERS:
- SPEED to trim the speed of the disc (the speed is expressed in CM per second)
- a SPEED of about 12 cm/s is exactly 1 round per second
- EVERY PLAY HEAD can be activated by BUTTON (on the HEAD) or by TRIG
- EVERY PLAY HEAD has a trimming function (to virtual move the headform -20% to +20% around the disc)
- EVERY HEAD has a display for the current delay
- EVERY HEAD has a volume (for the delay mixed)
- EVERY HEAD has a TAP out TAP in (so you can process a delayed signal and insert it back in the chain)
- THE SWELL is activated deactivating the ERASE HEAD
- THE SWELL pot controls from ECHO to infinite feedback (beware)
- DRY - WET is a mix from original input signal and the processed signal
- INPUT and OUTPUT have both a gain control
- INPUT has a simulated OCCHIO magico: if the 2 wings connect in the center, signal is clipping

	0.5.11.0
more flexibilty to time: we are virtual we can do what we want :)
- DISC time from SPEED POT is now from 1 cm/s to 100 cm/s
- added inertial response
- EVERY PLAY HEAD can move till next previous head influence area (+-49% of the current position)
- added TAP and TRIG to tempo (you can trig till 4000 cm/s )
- when in SYNC
- added PANIC button (to clear the buffer immediatly :D :D )
- added MAGNETIZATION coefficient: represents the inability of the ERASE HEAD to do a complete ERASE
 if MAGNETIZATION is high you'll get faint repetition also when the ERASE HEAD is active

	0.6.6
ADD time multiplier, now the minimum speed is 0.1 cm/sec
- ADD CV control for the disc speed
- ADD VCA for the CV control for the disc speed
- ADD DUAL Echo for STEREO outputs

	0.6.37
- solve a crash on win
- corrected some timing when switching to slow mode

```

---

## Basics

![Image of NYEcho](./nyeco.png) | ![Image of Binson Echorec](./echorec.jpg)

Type: Delay Effect / Looping / Hardware Model

Size: 18 HP x 3U

Delay Range (Normal Mode): 4 - 6583 ms

Delay Range (Time x 0.1 Mode): 41 - 54899 ms

- These times may be entirely blown out of the water with creative patching of Tap Tempo, but are outside the confines of this manual.

Modeled After/Inspired by: BINSON Echorec ***ADD LINK TO WIKIPEDIA OR SOMETHING***

Description: NYECHOecoeco is an effect module based on the most overengineered delay in the vintage world: the BINSON Echorec. 

The Echorec consists of a single constantly-spinning Reel which records its input and is then played by a plethora of playheads in succession, thus making a delay effect. 

The Echorec's's flexibility over each playhead/tap likely inspired the Intellijel Rainmaker. In the same manner, one could use the NYECHOecoeco as a CPU-friendly variant of Frozen Wasteland's "Portland Weather" module.

---

## Functions by Section

***SECTION BREAKOUT IMAGE REQUIRED*** ![SECTION BREAKOUT IMAGE]()

### Section A: The Teensy Tiny Speed Controls

This one is fairly simple to understand: You move the top knob to adjust the speed of the Spinning Reel. True to the hardware, the default "12 cm/s" equals a full spin.

The speed can also be modulated via the CV IN Jack (and it's attenuator), which accepts 0 - +10.00 V.

There is a Tap Tempo button you can click on to mark its tempo, like how most non-modular synthesizers do it. Additionally, there is an Input Jack to its right, which accepts both GATE and TRIG signals to sync the module to a clock.

Finally, the TIME x 0.1 function slows the disk down to a crawl, which allows for much greater flexibility as a looping effect.


### Section B: The Spinning Reel and Heads.

This section is an interactive, graphical and functional depiction of the unit it emulates. 

While the unit functions similar to a tape delay, think of typical operation as the signal being recorded to a continuous tape loop on the outside of the Reel, being read in sequence by one to six Playback heads, before being erased by the Erase head.

The playback heads are located at the 1/12th, 1/6th, 1/4, 1/3rd, 5/12ths, and 1/2 points around the Reel *(default times: 83 ms, 166 ms, 250 ms, 333 ms, 416 ms, and 500 ms)*. The relative position of each of the six Playback heads can be adjusted +/- 20%, although this is not reflected graphically. The Erase head is fixed after the final Playback head.

All 6 Playback heads (in addition to the Erasehead) have a clickable button to toggle their On/Off state *(Playback Defaults: Off, Erase Default: On)*. These can also be controlled by GATE/TRIG (see Section C).

If the Erase head is turned Off, you will encounter a sound-on-sound effect, with earlier loops becoming more subdued each time they are recorded over.

The red PANIC button will instantly delete the entirety of what exists on the Reel, in case an undesirable feedback loop or other sound is encountered.

The Reel itself can be clicked and held (but not dragged around as you would to scratch a vinyl record). This effect simulates pressing down on the Reel, with the motor eventually giving up and coming to a stop.

*The Reel will occasionally change from the standard "Green NYECHOecoeco" platter style to various 90's references (The Simpsons, Netscape Navigator, and a Vinyl Record, among others), Kurzgesagt-like objects (Ice-cream cone, another Vinyl Record made in this style, and more) and VCV module makers, such as Jeremy Wentworth (known in the Plugin Manager as JW-modules)*

***SHOULD WE INCLUDE A GUIDE ON REPLACING THESE IMAGES?***


### Section C: Playhead Controls.

In this section, each of the HEADS have various controls, inputs, and outputs to allow for more complex modulation of the effect's elements.

For each Playback Head, there is a:

- GATE input, which toggles the On/Off state for every GATE/TRIG sent through it.
- VOLume control, which ranges from muting the Head, to boosting it louder than the dry signal. This affects both the TAP OUT and Global OUTPUT volumes for each Head.
- TAP OUT/IN, working as a mono effects send-return for each HEAD. TAP OUT does not work as intended at the time of writing (patch 0.6.37).

***TAP OUT CURRENTLY WORKS, TAP IN DOES NOT, AND WHEN PATCHED WILL CAUSE THE CHANNEL TO FALL SILENT - FILE AN ISSUE WITH ANTONIO ON GITHUB***

The Erase Head has only a GATE input, which toggles the On/Off state for every GATE/TRIG sent through it.


### Section D: Mix

These three knobs offer control over the module's Output signal.

MAGNETIZATION controls how "strongly" the Input is recorded onto the Reel. The higher the value, the greater the likelyhood that the Erase Head will not scrub the entirety of the signal in one pass - the "Feedback" effect common to so many Delays.

SWELL is toggled On when the Erase Head is toggled Off. It works more like a traditional Feedback knob, in that it can go from zero repeats (beyond an initial Playback Head instance) to infinite repeats, which can cause highly unstable sounds.

DRY/WET controls how much of each signal (Dry vs Effected) is heard. At the extreme ends of the scale, you will hear none of the other signal.


### Section E: Signal Interface.

The standard INPUT and OUTPUT jacks are located here, along with 0 to 2.00x Gain knobs *(Default: 1.00x)*

This section also contains an [emulation of what is commonly known as a magic eye tube](https://audioexmachina.wordpress.com/the-audioexmachinas-echorec-bible/#magiceyes), which is a method for measuring incoming signals used in the mid-1960's instead of the more expensive VU meters. It consists of two opposing light sources (described as "wings") that display the signal's loudness, and when they overlap, it means signal clipping.

![EM81 Magic Eye Tube](https://www.effectrode.com/wp-content/uploads/2018/07/em81_magic_eye_tube_animation.gif)

Credit: [Effectrode Thermionic](https://www.effectrode.com/knowledge-base/the-magic-eye/)

---

## Usage

Simply start by connecting an audio signal to the [INPUT jack](#section-e-signal-interface) section), and connecting one or both OUTPUT jacks to your destination of choice.

Following this, tap some of the [PLAYHEAD buttons](#section-b-the-spinning-reel-and-its-playheads) to switch them on, in order to make the effect work. 

*At this point, fundamental use of the module is covered in its entirety, and everything else from this point is optional.*

Try to add swing to some of the [PLAYHEADs](#section-b-the-spinning-reel-and-its-playheads) by wiggling the small knobs next to them until you find a rhythm you like.

You can change the tempo of this rhythm by turning the [SPEED knob](#section-a-the-teensy-tiny-speed-controls) until it matches a feeling you're looking for.

Additionally, you could turn the [DRY-WET knob](#section-d--mix) to accent the first tap (also known as the dry signal) to make the repeats sound muffled and atmospheric.

You can also subtly accentuate some of the PLAYHEADs by [changing their volumes](#section-c--playhead-controls), as well as sending individual signals to effects, and returning them back.

To add a little mastering to the effect, in order to make the most out of the module, you can lower the INPUT and OUTPUT level knobs according to needs or to prevent clipping.

---

## Sample Patches

```
coming soon :)
```
