Squonk (6.30)
Author: Jim Aikin

Description

Squonk is a step sequencer. It has 12 steps, five CV outputs, a trigger input and output for each step, and other features. Two or more Squonk modules can be chained to create patterns longer than 12 steps.

Features

Each of the 12 horizontal rows contains the input, output, and controls for a single step. Other features are in the lower area of the module.

In the leftmost column are the trigger inputs. When a trigger is received at one of these jacks, Squonk will immediately jump to that step. Next to the trigger inputs are the stage lamps/buttons. Clicking on a stage button has the same result as sending a trigger to the triger input jack. The button for the currently active step is always lighted. (As in most step sequencers, only one step can be active at any given time.)

The five knobs in the A, B, C, D, and E columns control the voltages that will be sent to the output jacks (also labeled A, B, C, D, and E) immediately below the columns. The knobs in columns A, B, and C have a range of 0 to +2 volts; columns D and E have a range from -1 to +1 volts. When the x5 button for a row is lighted (green), the output values are multiplied by 5. The knobs' outputs are not quantized to equal-tempered half-steps, so a quantizer module (or several of them) will be a useful accessory for processing Squonk's output.

At the right end of each row is a trigger output jack. This will fire when the step is active. It will operate in one of four modes, depending on the setting of the lamp in the mode column for that row.

There are four possible settings for each mode lamp: yellow, blue, red, and dark gray. Yellow is normal; the trigger output will operate as described above. When the lamp is blue, no trigger will be sent, but in other respects the step will operate normally. The other two modes are significant only when Squonk is being stepped from the clock input (see below). When the mode lamp is dark gray, Squonk will skip that step. When it's red, Squonk will reset to the first step (or to the last step, if it's being clocked in the upward direction) instead of playing the red step. Red blocks the stepping process.

The rep (repeat) knob is active only when Squonk is receiving an external clock signal. The knob can be set to values from 1 to 8. This setting subdivides the trigger being sent to the corresponding output jack. If Squonk is being clocked in quarter-notes, for instance, the mode lamp is yellow, and the knob is set to 4, when that step is reached the trigger output will send four pulses at a sixteenth-note rate instead of a single pulse.

The Lower Area

At the lower left are the inputs and controls for automating which step will be active. The clock (CLK) input does what you would expect: Each time a clock signal is received, Squonk will advance to the next step. the output jack immediately to the right of the clock input sends the clock signal on; this is useful when two or more Squonks are being chained. The UP jack and button switch Squonk from stepping downward to stepping upward in response to the clock signal. The RND (random) button, when active, causes Squonk to choose a next step at random.

The SEL (select) knob can be used instead of a clock signal in order to manually select the active step. The CV input below the select knob automates this process. Sweeping the select CV input from an LFO is one possibility. If you're feeling perverse, you could use an input from a second step sequencer here. The input is unattenuated, and values from 0 to 1 volt are probably the most useful.

The ROT (rotate) knob can be set to values from -3 to +3; the center value is 0. When the rotate value is non-zero, each time Squonk receives a clock signal it will rotate the mode settings (in the column above the knob) up or down. This is useful, obviously, only when the mode settings of the 12 steps are not all identical. If the rotate value is 1 (or if it's -1 and the UP button is active), the mode column will move at the same rate and in the same direction as the active step. As a result, there will never be a mode change for the active step. More complex patterns can be achieved with other settings.

Note that it's possible for the red (stop) mode and the active stage to pass one another. If at a given moment the active step is 3, for example, and Squonk is stepping downward, while the rotate value is -1 and step 4 is red, on the next clock input the active step will be 4 and the red mode step will be 3. The red mode won't cause the stepping to jump back to the start, because the two settings will have passed one another. Here's an obscure tip, though: When there are two red mode steps separated by exactly two yellow or blue steps, the active step will hit one of them as it moves downward and the mode rotates upward.

The LAST output is active only when Squonk is receiving a clock signal, not when the select knob or CV is being used. This jack sends a trigger each time Squonk finishes its pattern. (If one of the mode lamps is red, the last trigger will be activated when the active step hits the red-mode step and jumps back to the start step.) This is useful when chaining two or more Squonks (see below).

The TRIG (trigger) output sends a trigger whenever a trigger is sent from any of the outputs in the column above it. This is useful for creating rhythm patterns.

The inputs in the CHAIN row are for chaining multiple Squonks.

In the row below the chain row are the start, stop, and reset trigger inputs. Resetting sends Squonk to the 12th step (or to the first step, if the clock is set to UP mode), so that the next clock received will start the sequence at step 1 (or 12).

The randomize all jack turns Squonk into a machine with zero predictability. A trigger at this input is probably too extreme to be very useful musically, as the x5, mode, and repeat settings are all randomized along with the knobs. In version 6.30, the randomize all button (next to the jack) doesn't work.

Chaining

When chaining two Squonks together for longer sequences, for convenience we'll call one the host and the other the client. The outputs of the host should be sent, as usual, to whatever devices (oscillators, envelope generators, etc.) are being sequenced. The outputs of the client module will be sent to the host's chain inputs. The connections are as follows:

Connect the A, B, C, D, and E outputs of the client to the five corresponding chain inputs of the host. Connect the TRIG output of the client to the CHAIN TRIG input of the host. Connect the clock thru jack of the host to the clock input of the client.

Now here's the tricky part: Connect the LAST output of the host to the start input of the client, and also to the stop input of the host itself. In the same way, connect the LAST output of the client to its own stop input and to the start input of the host. These connections will cause the two modules to run alternately: When the host reaches its last step, it will stop itself and start the client, and vice versa.

By using the red (stop) mode button on the client -- or, for that matter, on the host -- you can control the length of the combined sequence.

Usage Suggestion

Instead of using either the clock or the select CV input, try patching the various outputs of a clock divider to a number of the trigger inputs of various steps. (The SynthKit Shifting Clock Divider might be a good choice.) When multiple trigger inputs are receiving triggers, Squonk will choose the highest numbered step. Depending on the settings of the clock divider, complex sequence patterns can be achieved.

