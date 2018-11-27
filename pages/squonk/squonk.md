# Squonk 

Author: Jim Aikin

INDEX
1. [Antonio Says](squonk.md#antonio-says)
2. [Basics](squonk.md#basics)
3. [Features](squonk.md#features)
4. [The Lower Area](squonk.md#the-lower-area) 
5. [Chaining](squonk.md#chaining)  
6. [Usage Suggestion](squonk.md#usage-suggestion)

#### Antonio Says:

	0.5.4
		it's a PROGRAMMER, STAGE sequencer, Sampler TRIGGER, freely inspired to Serge TKB
		is 12 steps with 11 lines of programming

			line 1: TRIG IN: will select the stage triggered
			line 2: STAGE: is the stage selector by button. when in sequencer mode the current step will light up
			line 3: 5X: voltage multiplier for A B C D E channels
			line 4: A: CV channel from 0 to 2 volts
			line 5: B: CV channel from 0 to 2 volts
			line 6: C: CV channel from 0 to 2 volts
			line 7: D: CV channel from -1 to 1 volts
			line 8: E: CV channel from -1 to 1 volts
			line 9: MODE: TRIG mode; if bright yellow, CV and TRIG out, if dark yellow, only CV out, if black step is jumped
			line 10: REP: if the sequencer is clocked will retrig the step from 1 to 8 times (subdivisions) (ratcheting)
			line 11: TRIG OUT: single PULSE out when the stage is selected

		SEL knob: will select the current stage
		SEL CV input: selection of stage using CV (0 -> 10v)
		CLK IN CLK OUT: to clock the sequencer (and output the same clock to other devices)
		UP TRIG and BUTTON: if ON the sequence will go UP (normally is DOWN)
		RND btn: if light up the next stage is randomized

		OUTS A B C D E are the CV outs of the sequencer
		ROT knob, from -5 to +5, is the number of steps the yellow channel will rotate jump and rotate  if in sequencer mode
		LAST trig out: PULSE out when last step is reached
		TRIG (global): current stage TRIG out (with repetitions if any)
		
		CHAIN A B C D E  and CHAIN TRIG are useful when chaining many SQUONKs (to have just one connection for the CV and TRIGs)

		START STOP RESET: sequencer status controls by BUTTON or by TRIG
		RANDOMIZE ALL: must be pressed with COMMAND KEY (too dangerous!)

	0.5.6.0
		BUG for last chained step not triggering
		
		BUG reset now set to the correct position
		
		the CV now is scaled 1/12 V (with modf) to track steps like a keyboard using CV (0.08333 VOLT steps)
		
	0.5.7.0
		BUG: missing repetition first step if chained SOLVED
		
	0.5.13.0
		added RED mode: end of sequence marker
		
	0.6.4
		feature request: change color for the case ONLY CV : from dark yellow to BLUE

---
## Basics

![](./squonk.png)

Size: 18 HP

Type: Sequencer

Description: Squonk is a step sequencer. For each of the 12 steps, there are five channels of CV controls and a 5x voltage multiplier, a trigger input/output, ratcheting, and more. Multiple Squonk modules can also be chained to create patterns longer than 12 steps.

---

## Features

Each of the 12 rows contains the input, output, and controls for a single step. Other features are in the lower area of the module.

In the leftmost column are the trigger inputs. When a trigger is received at one of these jacks, Squonk will immediately jump to that step. Next to the trigger inputs are the stage lamps/buttons. Clicking on a stage button has the same result as sending a trigger to the trigger input jack. The button for the currently active step is always lighted. (As in most step sequencers, only one step can be active at any given time.)

The five knobs in the A, B, C, D, and E columns control the voltages that will be sent to the output jacks (also labeled A, B, C, D, and E) immediately below the columns. The knobs in columns A, B, and C have a range of 0 to +2 volts; columns D and E have a range from -1 to +1 volts. When the x5 button for a row is lighted (green), the output values are multiplied by 5. The knobs' outputs are not quantized to equal-tempered half-steps, so a quantizer module (or several of them) will be a useful accessory for processing Squonk's output.

At the right end of each row is a trigger output jack. This will fire when the step is active. It will operate in one of four modes, depending on the setting of the lamp in the mode column for that row.

There are four possible settings for each mode lamp: yellow, blue, red, and dark gray. Yellow is normal; the trigger output will operate as described above. When the lamp is blue, no trigger will be sent, but in other respects the step will operate normally. The other two modes are significant only when Squonk is being stepped from the clock input (see below). When the mode lamp is dark gray, Squonk will skip that step. When it's red, Squonk will reset to the first step (or to the last step, if it's being clocked in the upward direction) instead of playing the red step. Red blocks the stepping process.

The rep (repeat) knob is active only when Squonk is receiving an external clock signal. The knob can be set to values from 1 to 8. This setting subdivides the trigger being sent to the corresponding output jack. If Squonk is being clocked in quarter-notes, for instance, the mode lamp is yellow, and the knob is set to 4, when that step is reached the trigger output will send four pulses at a sixteenth-note rate instead of a single pulse.

---

## The Lower Area

At the lower left are the inputs and controls for automating which step will be active. The clock (CLK) input does what you would expect: Each time a clock signal is received, Squonk will advance to the next step. the output jack immediately to the right of the clock input sends the clock signal on; this is useful when two or more Squonks are being chained. The UP jack and button switch Squonk from stepping downward to stepping upward in response to the clock signal. The RND (random) button, when active, causes Squonk to choose a next step at random.

The SEL (select) knob can be used instead of a clock signal in order to manually select the active step. The CV input below the select knob automates this process. This input is quantized to accept a V/Oct signal, and was originally conceived as a way of programming an odd scale to be played by a MIDI controller.

The ROT (rotate) knob can be set to values from -3 to +3; the center value is 0. When the rotate value is non-zero, each time Squonk receives a clock signal it will rotate the mode settings (in the column above the knob) up or down. This is useful, obviously, only when the mode settings of the 12 steps are not all identical. If the rotate value is 1 (or if it's -1 and the UP button is active), the mode column will move at the same rate and in the same direction as the active step. As a result, there will never be a mode change for the active step. More complex patterns can be achieved with other settings.

Note that it's possible for the red (stop) mode and the active stage to pass one another. If at a given moment the active step is 3, for example, and Squonk is stepping downward, while the rotate value is -1 and step 4 is red, on the next clock input the active step will be 4 and the red mode step will be 3. The red mode won't cause the stepping to jump back to the start, because the two settings will have passed one another. Here's an obscure tip, though: When there are two red mode steps separated by exactly two yellow or blue steps, the active step will hit one of them as it moves downward and the mode rotates upward.

The LAST output is active only when Squonk is receiving a clock signal, not when the select knob or CV is being used. This jack sends a trigger each time Squonk finishes its pattern. (If one of the mode lamps is red, the last trigger will be activated when the active step hits the red-mode step and jumps back to the start step.) This is useful when chaining two or more Squonks (see below).

The TRIG (trigger) output sends a trigger whenever a trigger is sent from any of the outputs in the column above it. This is useful for creating rhythm patterns.

The inputs in the CHAIN row are for chaining multiple Squonks.

In the row below the chain row are the start, stop, and reset trigger inputs. Resetting sends Squonk to the 12th step (or to the first step, if the clock is set to UP mode), so that the next clock received will start the sequence at step 1 (or 12).

The randomize all jack turns Squonk into a machine with zero predictability. A trigger at this input is probably too extreme to be very useful musically, as the x5, mode, and repeat settings are all randomized along with the knobs. For the button to work, you MUST hold down Ctrl (Mac Cmd), but a trigger to the jack does not need this.

---

## Chaining

When chaining two Squonks together for longer sequences, for convenience we'll call one the host and the other the client. The outputs of the host should be sent, as usual, to whatever devices (oscillators, envelope generators, etc.) are being sequenced. The outputs of the client module will be sent to the host's chain inputs. The connections are as follows:

Connect the A, B, C, D, and E outputs of the client to the five corresponding chain inputs of the host. Connect the TRIG output of the client to the CHAIN TRIG input of the host. Connect the clock thru jack of the host to the clock input of the client.

Now here's the tricky part: Connect the LAST output of the host to the start input of the client, and also to the stop input of the host itself. In the same way, connect the LAST output of the client to its own stop input and to the start input of the host. These connections will cause the two modules to run alternately: When the host reaches its last step, it will stop itself and start the client, and vice versa.

By using the red (stop) mode button on the client -- or, for that matter, on the host -- you can control the length of the combined sequence.

---

## Usage Suggestion

Instead of using either the clock or the select CV input, try patching the various outputs of a clock divider to a number of the trigger inputs of various steps. (The SynthKit Shifting Clock Divider might be a good choice.) When multiple trigger inputs are receiving triggers, Squonk will choose the highest numbered step. Depending on the settings of the clock divider, complex sequence patterns can be achieved.
