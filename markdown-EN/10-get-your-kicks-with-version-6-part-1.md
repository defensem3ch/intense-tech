**Intense Tech with Defense Mech -- Get your Kicks with Version 6: Part 1!**
- Posted October 29th, 2019 by [DEFENSE
MECHANISM](https://defensemech.com) *Note: [traducción al Español por Pixel Guy encontrado aquí.](../es/10-consigue-hacer-kicks-con-la-version-6-parte-uno.md.html)*

Hello and welcome to another edition of Intense Tech! This lesson will
be about some kick techniques which I have previously covered in a
[video tutorial](https://www.youtube.com/watch?v=8ihMjHn90zY) but will
also expand upon in greater depth here. After reading this lesson, you
should have a good handle on how to use DRUM or FAST tuning with
instrument P/L/V settings in version 6 to create any kick to suit your
needs. I've also included a save file at the end of this lesson so you
can play around in version 6.9.0 on your own. Let's dig in!

------------------------------------------------------------------------

Wave Kicks: The Basics
------------------------------------------------------------------------

Let's start with the wave channel, a very popular choice for kicks for
good reason: it generates the lowest pitch of any channel, so it's great
for pumping out the lowest of the low end. As we've seen previously,
[generating a sine wave in the wave
channel](01-lsdj-wave-synth-deep-dive-part-1.md.html) can produce a pure tone
around 65 Hz at the lowest note of C1.

The quickest way to get a good kick of course, is to simply use a kick
in a wave kit. Otherwise, set your wave instrument synth to a sine- or
square-like waveform and use a command like `PC0` to slide the pitch
downward. Experiment with placing the note anywhere from C5 to C6, C7 or
above depending on how high-pitched and punchy you want the attack to
be. But changing one key setting will make all the difference in even
the simplest kick! Read on to find out more.

Changing the Pitch with P/L/V
------------------------------------------------------------------------

When LSDj changed from version 4 to version 5.1.0, the pitch engine also
changed. Until version 6, there was no way to recreate the old
logarithmic pitch. Luckily, we now have an instrument setting called
"P/L/V" which is actually not entirely obvious about what it should
affect, but I will clarify that! P/L/V settings affect how **P**
commands, **L** commands, and/or **V** commands work. The default
setting of "FAST" plays pitch slides and vibrato at the fastest rate
possible (this was previously known as "HF"). Pressing A+Down changes to
"TICK" which plays pitch slides and vibrato at a much slower rate that
is also affected by the tempo of the song. Pressing A+Down again changes
to "STEP" which makes P command a pitch offset only, which is not very
useful for kicks, but makes P commands on wave drumkit snares a lot of
fun! What we want to change is actually found when we press A+Up from
"FAST" and we find a new option: DRUM!

![Pressing A+Up while P/L/V FAST is highlighted will select DRUM pitch!](../media/image2.png)

The secret to DRUM P/L/V is that P and L commands are now played using a
special pitch mode that emulates the logarithmic pitch slides of the
previous LSDj versions! However it does come with a caveat: using any
transpose column in phrases or tables will not work as intended.
Accordingly, it also eliminates the possibility of creating kicks that
slide directly into bass notes. This is due to the special pitch lookup
table[^table] that does not work the same as the regular FAST
tuning. It's also helpful to note that the instrument TRANSPOSE setting
can be turned OFF in order to avoid this problem when transposing
phrases.

Now that we've discovered DRUM tuning, let's hear the difference between
a FAST kick and a DRUM kick!

![FAST pitch kicks vs. DRUM pitch kicks](../media/fast-drum.mp4)

Fine-tuning Wave Kicks
----------------------

Now that we've got the wave kick basics down, let's look at some ways to
adjust different aspects of the kick, starting with the first part of
the kick: the attack. Often overlooked, a snappy kick attack can make
all the difference to help cut through the mix.

There are a few ways to adjust the attack of the kick, and the most
flexible options can be utilized by applying a table to the wave kick
instrument. This way we have control over what happens on every tick.
When I create a kick table, I usually set a fast P command as the very
first command, which controls how fast the pitch slides downwards from
the note it's playing. Directly below it as the second command, I place
an L command with a TSP value of `80`. Setting this value means that no
matter which note is playing in the phrase, the pitch will slide
downwards to the lowest note possible, and because the L command stops
when it reaches this value, the pitch will not wrap around and play the
highest pitch. This is helpful if I decide later to change the tempo of
the song to a slower tempo, since DRUM P and L commands are not affected
by tempo. Additionally, it means that I'm free to change the note of the
kick in the phrase and adjust the speed of the P command to my liking.
Let's experiment with different notes around the octaves of C5 and
above.

![Changing the octave of the kick lets you adjust the transient and the P command value](../media/kickpitch.mp4)

Another option is to change the waveform of the kick on the first tick.
This is a variation of what's sometimes known as the "Kyoto kick"
technique as popularized by Toriena and others. A [waveform that
contains some noise and grit](02-lsdj-wave-synth-deep-dive-part-2.md.html) can
be set as the first waveform, and afterwards it changes to the normal
kick waveform. In this example, Wave 00 is a kick waveform modified to
contain more noise, while Waves `01-0F` are the normal kick waveforms. A
command of F01 is placed on the second line of the kick table to switch
from Wave `00` to Wave 01. However, we can eliminate the need for this F
command if we set the wave instrument to Play Loop, Length `1`, Repeat `0`,
Speed `01`. This will play Wave `00` for 1 tick and then switch to Wave `0F`.

![Changing the first waveform can also add impact to the kick transient](../media/frametransient.mp4)

It's also worth noting that DRUM tuning can be very effective when used
to create other types of drum sounds such as toms and snares. And it
works on pulse instruments as well!

Moving from Kick to Bass
------------------------

What if we want a kick instrument that transitions seamlessly into a
bass note such as an 808-style kick? For this we need to return to FAST
pitch and we need to make sure that our instrument Transpose is set to
ON. In this example, I've set the root note an octave above where the
bass note will sound. The first line of the table has a one-octave
transpose up and a P command to slide down for two ticks. The third line
of the table has a one-octave transpose down and an L command. This is
an overall much smoother sound, although you could experiment by
combining the waveform-switching technique mentioned above.

![Change P/L/V to fast when transpose is needed](../media/808kick.mp4)

It's also worth mentioning that in many cases, it's quite simple to
reduce the time between kick and bass by simply [changing the
groove](groovy-groove-and-tick-tricks-part-1.html). No fancy kick
transposition needed! In this example, the first number of ticks in
Groove `10` is how many ticks the kick will last, and the second number of
ticks is how long the bass will last.

![Changing the groove can reduce the time between playing the kick and the bass note](../media/kickgroove.mp4)

As promised, [here is a link to the save
file](https://defensemech.com/songs/kicktech.sav) including these
examples. That's all for this round of Intense Tech! Stay tuned for next
time where we'll delve into making kicks in the other channels! 

[^table]: A lookup table is the table of values where LSDj stores the
frequency of each pitch, so that when you select a note such as "A5,"
the software plays the frequency "440 Hz." DRUM pitch uses a different
lookup table during pitch slides in order to play them in a logarithmic
fashion.


