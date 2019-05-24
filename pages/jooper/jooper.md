# Jooper

***NB. Joop \[joːp\] is a Dutch name, and his namesake module is pronounced "Yoaper" \['joːpɚ\]***

Author: Joop van der Linden / @joopvdl

Editor: Pat McIlveen / @patman023

Last Updated: 2019/01/27

Last Patch: 0.6.39

**INDEX**

1. [Antonio Says](#antonio-says)
2. [Basics](#basics)
3. [Functions by Section](#functions-by-section)
   - [Section A](#section-a)
4. [Usage](#usage)
5. [Sample Patches](#sample-patches)

---

## Antonio Says

<details>
  <summary>Click to see the Changelog</summary>

```
	0.6.15
its an 8 channel, UNITYMIXER, MULTIPLEXER, IN-OUT SWITCH, with local and global controls. With a scene managar
- there was a request (Joop van der Linden) to have a complex and seletable on the fly multipath router for complex temporal structures

CONTROLS

there are 8 lines replicated of 4 INPUTS (ABCD) and 4 OUTPUTS (ABCD)

the JOOPER status could be:

- EXCLUSIVE: just one of the A B C D channels is selected on both INPUT and OUTPUT
  - in exclusive mode every one of the 8 lines is a 4 channels MULTISWITCH (IN and OUT)

- MULTIPLEXER mode
  - any combination of the A B C D INPUTs can be selected. All the activated will be summed
  - any combination of the A B C D OUTPUTs can be selected. All the activated will receive the SUMMED INPUT

- DUAL EXCLUSIVE A-B mode
  - it's like the EXCLUSIVE but there are A B and C D paired IN and OUT

all the channel can be activated with TAP TRIG local, Or all the channel can be activated with GLOBAL TAP TRIG

the RESET will move all to initial condition

SCENE MANAGER

Let you save status in a memory and reuse during the execution of the sequence

COMMANDS and DISPLAYs are:

- GREEN display, total of available scenes
- RED display, draggable to select current scene
- LOAD will load curren scene into memory
- ADD will add a scene to the end of the scenes list
- DELETE will remove current RED displayed scene from memory
- DELETE ALL will clear the scenes list
- SELect CV: will select and LOAD a scene using a CV command: 
  - cv is a grid of 10V divided by the number of availabel scenes
- PREV TAP TRIG, will go back one scene and LOAD it
- NEXT TAP TRIG, will advance one scene and LOAD it

	0.6.23
mode is reset only if OPTION/WINDOWS Key is donw

	0.6.28
- solve requests #62
- add command "TO FIRST" by TRIG and by TAP: will reset scene sequencer to step 1
- add LOAD by TRIG (was only by TAP)
- add SAVE by TRIG (was only by TAP)
- add DELETE by TRIG (was only by TAP)
- add DELETE ALL by TRIG (was only by TAP)
- add UPDATE current SCENE with current SCREEN (TAP and TRIG)
- add INSERT current SCREEN before current SCENE (TAP and TRIG)

	0.6.31
- bug: reset was not correctly resetting if in DUAL EXCLUSIVE MODE
- Add titles for scenes
```

</details>

---

## Basics

![placeholder](./moduleimage.png)

Type: Complex Switch / Multiplexer / Unity Mixer (Summing)

Size: 18HP x 3U

Description: Jooper is a flexible signal router/matrix switch with scene memory

Module Requested by: Joop van der Linden

---

## Functions by Section

### Section A



### Section B



### Section C



### Section D



---

## Usage



---

## Sample Patches




------
------
------

Joop's 4.0 revision

JOOPER is a flexible signal router/matrix switch with scene memory.



SWITCHING
Jooper can route various input signals to various outputs. It has eight independent lines (the horizontal
lines), each with four inputs and four outputs.
The inputs (cleverly labeled “INPUTS”) are on the left side of the module, and the outputs are on the
right. Next to each input and output jack is a lamp, which can be either yellow (lighted) or gray (dark).
When a lamp is lighted, the jack is active. When the lamp is dark, the jack is inactive.
There are no internal connections between the lines, but you can obviously patch an output or outputs
from any line to the inputs of any other line.
Each line can be switched individually by using its switching button (the one near the middle) or by
using the trigger input. There's also a trigger output, that can be used (among others) to chain lines (so
you can have different signals be switched simultaneously). There's a switch for the inputs, and for the
outputs.
All lines can be switched together using the GLOBAL switch underneath the lines.
MODES
There are three modes: EXCLUSIVE (the red one) where all lines have 4 inputs and 4 outputs,
MULTIPLEXER (the green one) where you can switch between any possible combination of
inputs/outputs, and DUAL EXCL A-B (the blue one) which will turn Jooper into a 16-ch dual A/B
switch (that sounds complicated, but it's just 16 standard two input-two output switches).
One thing to remember: in EXCLUSIVE and DUAL EXCL, Jooper is just a switch. In MULTIPEXER
mode, you can also sum (combine) signals.RESET
The reset button and jack (to the right side just above the Scenes section) resets all inputs and outputs
so that only the A jacks are active. It will not change the MODE. It will also not affect the SCENES
that are in memory.
SCENES
A SCENE can be considered a snapshot of the current state of the switching matrix (the 8 rows). You
can store as many SCENES as you like. It will also remember the state of the MODE button.
To the left, the green number will show the amount of stored SCENES, and the red number shows the
currently selected SCENE. You can select SCENES by using the SEL CV trigger input, but the scene
will not be loaded until you press or trigger LOAD.
ADD will add a scene to memory. There's also a trigger input for this, next to the button. You will
notice the green COUNT number will be increased by 1. The red “current” number does not change,
although you think it should, and this can be quite confusing. I'll explain that a bit later.
You can delete (DEL) a scene, or. delete all scenes (DEL ALL). If you want a scene to be inserted
between two existing scenes, use INSERT. You can navigate between scenes using PREV (Previous),
NEXT (Next), TO FIRST (go back to the first scene, this can be considered a reset function, just as
when a sequencer is reset to the first step)
UPDATE will update a scene with any change you may have made to that scene.
And now for the possibly confusing part:
In initial state, when you just fired up Jooper and have made no changes, there are no SCENES. You
can switch all you like, but nothing will be stored. COUNT and CURRENT both are at 0.
If you add a SCENE, there's 1 SCENE. This SCENE is added to the end of the row. You will now be
“tranported” to SCENE1, you will think. But that's not the case.
THE SCENE MEMORY CHANGES FROM AN EMPTY STATE TO AN ACTIVE STATE. So
SCENE 0 that you were working in (you thought), disappears. Now you are in SCENE 1, the first
SCENE in the row (that, for now, only has 1 SCENE in it). But, in fact, you are not really in SCENE 1.
Any time you ADD a scene, the current settings will be added as a SCENE in the end of the row, but
you will not be taken to that SCENE. You will stay in a state that we might call PROGRAMMING
STATE (don't you love computers) which is independent of SCENE selection. The CURRENT number
says 1, because SCENE 0 (that never really existed) has disappeared, but best way to think of it is that
you are still in the SCENE that is no SCENE, the one SCENE that rules them all, the VOID-SCENE.
Only if you start navigating between SCENES, you will actually “be” in a SCENE. Now you can
change settings, UPDATE if you like the new settings better, or jump to another SCENE (PREV,
NEXT, TO FIRST) and all the changes you made will disappear. If you press ADD, a new SCENE will
be added to the end of the line.
So remember : ADD will add a scene to the end of the line of SCENES.
NAMING SCENESIn the black display on the top of the SCENES section you can enter a name for each of the scenes.
Patching Suggestions.
1. Connect the trig outputs from a drum (trig) sequencer to Jooper, and the outputs from Jooper to
drum players. Now you can create buildups, dropdowns, etc.
2. Connect the outputs of a drum sequencer to different drumkits.
3. Connect a sequencer to different VCO's for different bass or lead sounds.
4. Connect different sequencers to a lead or bass sound.
5. Jooper can also be a simple 16ch on/off switch.
6. Connect different outputs of 4 hands, different voltages, to Jooper and route those to the
sequence number selection input of a sequencer.
7. Use Jooper to start counters at a certain time.
Well, you get the idea.
Note: Jooper has been named, much to his surprise, after Joop van der Linden, who suggested this
module to Antonio (although most of the cleverness should be credited to Antonio). Joop is Dutch, so
the proper pronounciation would be somewhat like Yoaper.