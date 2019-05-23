# Dual Signal Delayer (2D)
---
Author: John Hornik

Last Updated: 2019/05/23

Last Patch: 0.6.33


## Antonio Says


```
0.4.0d

dual delay from 0 to 2000 msecs

both delays are CV controllable
```

---
## Basics

![DualSignalDelayer](./2d.png)

Type: Delay

Size: 2 HP

Signal is plugged into IN. The amount of delay is adjusted with TIME, from 0 to 2000 msecs - default is 1000 msecs. CV modulates the TIME knob. OUT outputs the delayed signal.

![Sine wave with 100 msec delay](./2d_sin_delay.png)

*2 Hz sine wave with 100 msec delay*

Using non-square waves to modulate the TIME parameter turns 2D into a complex waveshaper.

![Complex wave output](./2d_complex.png)

*2 Hz sine wave with 200 msec delay, modulated by 2 Hz triangle wave*





---


## Sample Patch

[2d_sample.vcv](./2d_sample.vcv) 

![2d sample - groove](./2d_sample.png)

In this patch, the first 2D is being used to offset the hihat, and drag the snare slightly behind the beat. The second 2D offsets a copy of the kick pattern and is being modulated with a sine wave to give it a little funk.


