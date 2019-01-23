# BIGBUTTON

Author: Pat McIlveen

Last Updated: 2019/01/10

Last Patch: 0.6.38

**INDEX** 

1. [Antonio Says](#antonio-says)
2. [Basics](#basics)
3. [Functions by Section](#functions-by-section)
   - [Section A](#section-a)
   - [Section B](#section-b)
   - [Section C](#section-c)
   - [Section D](#section-d)
4. [Usage](#usage)
5. [Sample Patches](#sample-patches)

## Antonio Says

```
	0.6.22
utility with 2 BIG buttons to send TRIG and GATES
the BUTTONs are PULSER or GATER, they can be set using contextual menu
TRIG IN, PULSE OUT, GATE OUT and GATE PASSAGE of signal
from TOP
TRIG IN accept an externa PULSE as button PRESSED
PULSE OUT (when the button is pressed)
AUDIO CV IN combined with AUDIO CV OUT it's gate activated when the button is in GATE mode
GATE OUT: when the BTN is in GATE MODE and BTN is pressed outputs 10v
```

---

## Basics

`![](./moduleimage.png)` *[saved in the same directory.]*

Type: VCA / PB&J Sandwich / ABCDE *[Don't worry if you don't get every last usage case.]*

Size: X HP *[If you don't like squinting, use aP-Modules HP Meter :-D ]*

Modeled After/Inspired by: *[If Antonio included references to hardware/software in the changelog, the module browser in Rack (like he did the Complex DAHD), or on a FB post, put those here. The same goes for requests from people for a module that does XYZ; put their name in here.]*

---

## Functions by Section

### Section A

*[The sections should be in reference to the image - see MetaAardvark for a great example.]*

Try and describe what the control **does**, what voltage range a CV Input accepts, the kind of signal an output generates, etc. Usage has its own section, so please try and limit descriptions to specific controls here.

FUNCTION NAMES should be in ALL CAPS.

If you need to add a specification in a text block, try to be as clear as possible, e.g. "-666.00 V to +666.00 V ***(Default: 0.00 V)*** ". If you can't fit the phrase inline, separate it out like these:

***Default Clock Rate: 10.00 Hz***

***Min Clock Rate: 0.01 Hz***

***(Anything between 3 \*s will be in bold -and- italic)***

### Section B

If you need to write in point form:
- Type [dash], [space], then type your first-level items.
  - [space] [space] [dash] [space] to start your second-level items.
- Don't add extra lines between list items.

Start writing normally again (no extra dashes and spaces, an extra ) once you have finished writing your list.

### Section C

Useful modules for testing:

- Visualizing Signals
  - Fundamental Scope
  - Gratrix Scope-G1
  - Submarine Free EO-102 (Envelope Oscilloscope)
  - Submarine Free LA-108 (Logic Analyzer)
  - Bogaudio Analyzer-XL

- Quantifying Signals/Knob Values
  - Computerscare Debug
  - alikins Hovered Value
  - alikins Specific Value
  
- CV/Trigger Generation/Manipulation
  - Submarine Free SS-221 (21 Output Voltage Sources)
  - LOGinstruments Precise DC Gen
  - ML Modules Sum8
  - Impromptu Clocked
  - AS Flow
  
- General
  - aP-Modules HP Meter

### Section D

*[As many sections as make sense. You're not required to use 4!]*

---

## Usage

Describe how to **use** the module. 

---

## Sample Patches

\[typethefullpatchname.vcv] \(\./typethefullpatchname.vcv) 

- Save the patch in the same folder. Please don't link to external services, since they're not owned by Microsoft (like Github), and who knows if/when they'll go down?

If your patch isn't self-evident based on how you've described the module above, try and include some kind of basic write-up.
