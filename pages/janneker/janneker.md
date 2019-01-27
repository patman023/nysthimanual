# Janneker/Janneker Timed

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
JANNEKER
	0.6.28
---- the pulse sequencer/coordinator
---- companion for JOOPER and for 4HANDS
---- with JANNEKER you can set KEYFRAMES/SCENES of different pulses duration
---- Every scene has its own duration in pulses
---- there is PULSE out every time a SCENE is changed
---- there is a PULSE out every time the complete sequence is executed
---- PARAMENTERS:
---- ACTIVE TAP/TRIG JANNEKER will advance on PULSES
---- LOOP TAP if ON the sequence is always repeated
---- EOL (End of Loop) will output a PULSE when the sequence is finished
---- EOP (END OF PULSES) will output a pulse when a single SCENE is finished
---- PULSES display/editable is the count of pulses for curent SCENE
---- CURRENT PULSE display of the current count of pulses for the current SCENE
---- DECR -1 decrement the current count of pulses (sequence can go backward too)
---- INCR +1 increment the current count of pulses
---- SCENE display is the curren count of scenes
---- CURRENT SCENE (editable) is the current in action scene
---- RESET TAP/TRIG will reset CURRENT SCENE to 1 (if there are scenes)
---- PREV TAP/TRIG will go and load CURRENT SCENE - 1
---- NEXT TAP/TRIG will go and load CURRENT SCENE + 1
---- ADD TAP/TRIG will add a scene at the end of scenes with current set PULSES
---- LOAD TAP/TRIG will load the current scene to the screen (PULSE are updated)
---- UPDATE TAP/TRIG will update current store scene from the screen
---- DELETE TAP/TRIG will delete current scene
---- DELETE ALL TAP/TRIG will delete all scenes

	0.6.30
---- ADD REC mode
---- the idea is to help during composition
---- if REC mode ON and ACTIVE ON incoming pulse will increment (or decrement)
    current PULSES for scene
---- when ADD scene if in REC mode, target PULSES becomes 1 again
---- solved a crash

	0.6.31
---- bug: pulse count at startup not inited
---- feature request: if in RECORDING mode, when press ADD, the ADD is happening on the next PULSE in
---- feature request: add input by keypad
---- ADDING a CHEAT SHEET to use it with the KEYBOARD
---- TO use the keyboard your mouse must be placed on top of the JANNEKER
------ "PAGE DOWN" go to the next scene
------ "PAGE UP" go to previous scene
------ "ESCAPE" reload current scene removing current alterations
------ "OPTION/WINDOWKEY P" will reset current scene, all scenes will be deleted
------ "OPTION/WINDOWKEY A" will add current scene to the scenes list
------ "ENTER (keypad)" add a stage with current values at the end of the sequence
------ "RETURN" (or "OPTION/WINDOWKEY ENTER (keypad)") update current stage with current onscreen values
------ "I" insert a stage with current values before the current stage of the sequence
------ "DECIMAL POINT (keypad)" reset current pulse count entering value to 1
------ "+" adds 1 to the current pulses value
------ "-" subtract 1 to the current pulses value
------ "OPTION/WINDOWKEY -" will delete current scene, and remove it from list
------ "OPTION/WINDOWKEY +" add a stage with current values at the end of the scenes (same as "ENTER (keypad)")
------ 0 1 2 3 4 5 6 7 8 9 are used to entering data
-------- values for modes are:
-------- PULSECOUNTmode from 1 to 9999

	0.6.34
---- changed pulse out time from 0.1 msecs to 1 msec
-------------------------------
JANNEKER TIMED
	0.6.28
---- it's a time director/scene coordinator PULSE sequencer
---- it's the same as the JANNEKER, but uses real time as duration of the scene
---- instead of END OF PULSES there is an END OF SCENE
    there is a pulse OUT when the time for the current scene
    is finished, advancing to the next scene

	0.6.30
---- ADD REC mode
---- the idea is to help during composition
---- if REC mode is ON and ACTIVE is  target time will advance automatically
---- when hitting ADD (scene), the target time is sotred and a new time is inited to 0.0
---- solved a crash

	0.6.31
---- BUG: can't move target time! (sorry forgot to set editable the DISPLAY!)
---- BUG: saved times were all aligned to seconds (now is really 0.001 seconds resolution)
---- ADD SCENE works only if in (RECORD & ACTIVE) or not in RECORD mode (to help automated recorders)
---- increased time resolution now from 0.001 to 999.999 seconds
---- add time scale
---- some UI changes

	0.6.34
---- changed pulse out time from 0.1 msecs to 1 msec
```

</details>

---

## Basics

![placeholder](./moduleimage.png)

Type: Utilities

Size: 5HP x 3U / 8HP x 3U

Description: Pulse Director / Timed Pulse Director

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

JANNEKER
The creation of Jooper, with its SCENES, begged for a companion that would be able to switch
between scenes at timed intervals. So we came up with the idea of Janneker (Janneke is the name of
Joop's wife). Originally it was conceived as part of Jooper, but for various reasons, notably space, it
became a separate module. Still Jooper and Janneker can be best explained in how they work together.
JANNEKER is a timed pulse director. You can ask it, so to speak, to “push” a button after counting to
8. Or 4. Or first count to 8, push a button, count to 6, push the button again, etc.
It works very well with Jooper, 4Hands, or Impromptu's sequencers to control settings in a song, and to
advance from one section of a song to the next. In fact, with Janneker you have a tool to program the
entire song.
Consider this: You have created sequences. You have created song sections using Jooper. You might
have 4Hands send out different values, intended for different sections. Now Janneker will be the
“conductor” that will “tell” all the instruments, all the sections, to start or stop playing, and when.
The most important connection is the “END OF PULSES” trigger output. This has to be connected to
the “NEXT” scene selector button in Jooper, or the NEXT sequence button in an Impromptu sequencer
(you have to right click and set SEQ CV-in to “trig incr”.
Now connect a (clock) pulse to the INCR+1 trigger input. This pulse's tempo is the time grid to which
we can switch. If you set it to 1 bar, there's a switching possibility at every bar. This is, to me, the most
practical setting. But you can also set it to 4 or 8 bars, or whatever.
Now tell Janneker to count 8 bars by changing the red PULSES number. You can use drag, or the
numeric keyboard for that (mouse should be over the display).
Press ADD, and a new SCENE is created, which consists of this information: wait 8 bars, then output a
pulse at “END OF PULSES”.Start the clock, and see Janneker output a pulse after 8 bars. Add a few more scenes, preferably with
different lenghs, and see what happens.
OVERVIEW
ACTIVE: when active, Janneker responds to pulse inputs. When inactive, it ignores those, and will not
output a pulse.
LOOP: After the last scene, Janneker will re-start from scene 1.
EOL: End Of Loop. Will output a pulse at the end of the loop, so after the last Scene has played.
REC: record mode. Discussed later. Basically, if you Janneker is active, and a clock is inputting pulses
to the incr+1 input, you can program Janneker by adding scenes. Janneker will remember the PULSES
setting for each created scene.
END OF PULSES/CURRENT: when the green “CURRENT” display reaches the number in
“PULSES” , END OF PULSES outputs a pulse (trigger).
DECR-1: CURRENT is decreased by 1. You can do all kinds of nice stuff with this input. Discussed
later.
INCR+1: CURRENT is increased by 1. This is the main clock input.
SCENES: the amount of created Scenes.
CURRENT: the currently active Scene.
(See the Jooper section for some thoughts about Scene creation, in the SCENES section.)
RESET: reset Janneker to Scene 1. Same as resetting your sequencer to beat 1.
PREV: go to previous Scene.
NEXT: go to next scene.
ADD: create a Scene.
Load: Load the current Scene immediately.
Update: update curent Scene.
DELETE: delete current Scene.
DEL ALL: delete all Scenes.
MANUALLY ENTERING VALUES
Change the PULSES value by dragging the mouse, or with the numeric keyboard (mouse should be
over Janneker). Right click resets to zero.
Num keyboard:
0 1 2 3 4 5 6 7 8 9 are used to entering data
"DECIMAL POINT (keypad)" reset current pulse count entering value to 1
"+" adds 1 to the current pulses value
"-" subtract 1 to the current pulses value
Other keyboard controls: (mouse should be over Janneker)"PAGE DOWN" go to the next scene
"PAGE UP" go to previous scene
"ESCAPE" reload current scene removing current alterations
"OPTION/WINDOWKEY P" will reset current scene, all scenes will be deleted
"OPTION/WINDOWKEY A" will add current scene to the scenes list
"ENTER (keypad)" add a stage with current values at the end of the sequence
"RETURN" (or "OPTION/WINDOWKEY ENTER (keypad)") update current stage with current
onscreen values
"I" insert a stage with current values before the current stage of the sequence
"OPTION/WINDOWKEY -" will delete current scene, and remove it from list
"OPTION/WINDOWKEY +" add a stage with current values at the end of the scenes (same as
"ENTER (keypad)")
-------- values for modes are:
-------- PULSECOUNT mode from 1 to 9999
RECORD MODE
When Janneker enters record mode, it will remember the amount of pulses between entering record
mode and ADDing the first Scene, and between subsequent ADD actions.
It will create a new Scene on the next incoming clock pulse in INCR+1. So, Scene creation is quantized
to the incoming clock.
One thing to remember is that a scene is created AFTER the musical event that you want to record.
This means it's easy to forget to ADD a scene for the final state of the song, which usually will be when
all is silent again. Just count four pulses, press ADD one more time, switch off RECORD and you'll be
ok.HOW (RECORD MODE)
Now, how to use this?
For this description, I assume you have one Jooper and one Janneker connected to each other. But you
can connect as many Joopers as necessary, or 4Hands, or sequencers, or whatever you can think of.
For clarity, I have not connected anything to the Jooper switching rows. But you can route sequencer
trigger outputs, clock signals, anything through it. I will give one example at the end.
Of course, we also need a clock.
We need a clock signal that will create our grid. Here, the grid is set to one bar (bmp /4). So there will
be a pulse incoming to Janneker every bar, and therefore every pulse in Janneker represents one bar.Then, it's necessary to synchronise those. For that reason, we need to add Trigger Buttons to, at least,
the ADD inputs on both Jooper and Janneker.END OF PULSES of Janneker should be connected to the NEXT input of Jooper.Also, we need a trigger button connected to the RESET input of Janneker, and the TO FIRST input of
Jooper. This is probably connected to the button that resets the entire song to its initial state.It can be practical to synchronise NEXT and PREV inputs. In this case a merger is needed to combine
the END OF PULSES and NEXT of Janneker to Jooper's NEXT.It can also be practical to connect a trigger to DEL ALL of all modules.Now, enter REC mode, create scenes on Jooper, and switch between them using Janneker, creating a
song on the fly! Make sure to switch Janneker to ACTIVE, and have the clock running. Switch REC on
after that, and start counting.Remember: a scene will be added on the next incoming clock pulse on Janneker. Scenes on Jooper will
be added immediately on the ADD trigger, but that's no problem when playing back, so don't worry
about that. But it's musically preferable to hear switches made on Jooper on the next Scene creation, so
I use ML's trigger buffer for that.
You can of course use hardware triggers to make switching easier, and to trigger that wonderful ADD
moment.
One final observation:
When Rack will be available as VST plugin, some of this functionality can be done by triggering from
the DAW. Still, there are advantages to the JOOPER/JANNEKER team. First, you don't have to use a
DAW to create song structure, so you will stay in the modular mindset.
Second, you can enter probability and chance by using, for instance, a bernoulli gate or Nysthi's Bivio
or Bridges.
Run the INCR+1 pulse through a bernoulli gate, and your song has a structure with unpredictable
lengths. Add some more randomness by connecting a random pulse to the DECR-1 input.

JANNEKER TIMED
Basically, Janneker Timed has all the functionalities of Janneker, but it will not count pulses, but time.
Therefore, on Janneker Timed the E-O-SCENE trig output will output the switching triggers, just like
Janneker's END OF PULSES trig output does. And that's the only difference.