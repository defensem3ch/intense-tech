**Intense Tech with Defense Mech - Don't Sleep on Z (feat. Hypnogram)**
- Posted December 13th, 2018 by [DEFENSE MECHANISM](https://defensemech.com) Note: [traducción al Español por Pixel_Guy encontrado aquí](../es/03-no-te-duermas-sobre-la-z-presentando-a-hypnogram.md.html).

Hello, and welcome back to Intense Tech, where we take an in-depth look at
some of the features of LSDj to both help you level up your understanding and your skills as
an artist!

In last month’s lesson, we looked at the wave synth. We’ll be detouring away from wave
synthesis for a couple lessons, but we’ll return after we lay the groundwork for an exciting
wave synth lesson! This month, we’ll take a look at the Z command for LSDj and explore how it
can [spice up your life!](https://www.penzeys.com/)

**Note**: An earlier version of this post, written by
[Hypnogram](https://hypnogram.bandcamp.com) appears at
  [https://hypnogrammusic.blogspot.com/2016/03/dontsleep-on-z-by-h-ypnogram.html](https://hypnogrammusic.blogspot.com/2016/03/dontsleep-on-z-by-h-ypnogram.html)
(Used with permission – Thanks Noah!).

---------------------------------------

Like the LSDj Wave synth which we looked at in the last
[two](https://defensemech.com/intense-tech/en/01-lsdj-wave-synth-deep-dive-part-1.md.html)
[tutorials](https://defensemech.com/intense-tech/02-lsdj-wave-synth-deep-dive-part-2.md.html)
, the perplexing Z command is often misunderstood. Let’s clear the matter up with some fun
demonstrations of creative uses of the Z command. By the end of this lesson, you’ll be armed
with a load of new techniques for adding some controlled chaos to your compositions!

To begin, let’s take to the
[LSDj manual](https://www.littlesounddj.com/lsd/latest/documentation/) (version
6+), to get at exactly what the Z command is:

> **Z: RandomiZe**
>
> The Z command repeats the last non-Z command, adding a random number to the original command
> value. The Z value controls the maximum value of each digit to be added.

Now, let’s get right into learning by example!

**Random Vibrato**
------------------

![ ](../media/z01.mp4)

For the first example, I’ll break things down step by step. On step 0, we have a note with a
`V00` command. Every other step afterwards, we have the same note with a `Z03` command. Since the
last non-Z command was V, each `Z03` will act as another V command, applying one value out of
four possible values: either `V00` again, `V01`, `V02`, or `V03`. However, it will not add to or
otherwise affect the previous Z command – so you can’t randomize a Z command itself.

**Random Duty Cycle**
---------------------

![ ](../media/z02.mp4)

It may not entirely make sense at first how the Z command could apply to a case like pulse
duty cycle, since the W command uses graphical values instead of numbers, but rest assured it
works very well.

12.5% pulse width = `00`

25% pulse width = `01`

50% pulse width = `02`

75% pulse width = `03`

In this example. every `Z03` command has the possibility of applying any possible duty cycle.
However, since 25% and 75% effectively sound identical, it will provide more random variation
in the sound if the Z command’s range is reduced by changing it to `Z02`, which will give us
either 12.5%, 25%, or 50% with equal probability.

**Random Panning**
------------------

![ ](../media/z03.mp4)

The O command is another case where it isn’t obvious how the Z command works. O controls
left/right output and can also be used to mute output from both channels entirely. It is
therefore important when applying Z commands that you choose the initial value of the O
command carefully.

`OLR` (both channels on) = `00`

`O__` (both channels off) = `01`

`OL_` (Left channel only) = `02`

`O_R` (Right channel only) = `03`

In this example, we are alternating between left-only and right-only panning. However, if we
wanted to randomly choose between both channels on, left channel only, and right channel only,
we would set our initial O command to `OL_`, then use successive `Z02` commands.

In version 6, the Z command also works in tables, where it will randomize the last effect used
in the table. Randomly alternating between `OLR` and `O__` can be used on a table for an
instrument with Automate=ON for a random gating effect, as shown here:

![ ](../media/z04.mp4)

In this case and in the case of pulse duty cycle changes above, if the range of the Z command
exceeds these four values, the value will be the remainder after the Z value is divided by 4. For
example, if `Z11` (`11` in hex equals 17 in decimal) randomly applies the value of 17 to our P or O 
command, 17 divides into 4 4 times, while leaving a remainder of 1, so this Z command would apply 
the same effect as it would if it were applying the value of `01`.

**Random Melody**
-----------------

![ ](../media/z05.mp4)

Let’s note the second part of the LSDj manual’s description of the Z command, where it states
that Z controls “the maximum value of each digit to be added.” This means that each digit of
the Z command functions independently of the other.

> **Example:**
>
> `Z02` adds one of `0`, `1`, `2` to the original value.
>
> `Z20` adds one of `0`, `10`, `20` to the original value.
>
> `Z22` adds one of `0`, `1`, `2`, `10`, `11`, `12`, `20`, `21`, `22` to the original value.
>
> Note: Randomize does not work with Hop, Groove and Delay commands at the
> moment.

*Note on the note: Randomize DOES work with Hop, Groove, and Delay commands as of version 8.1.9.*

This can be useful in cases where we want to randomize pitch, for instance using the F
command. `Fxy` controls pulse finetune with the second digit `y`, and the first digit `x` controls
the tuning for pulse channel 2. `x` represents how many semitones (half-steps) should be added
to the current note. So by applying `ZF0`, we can randomize a melody, but only in pulse channel
2. Each Z command will add any note in between and including our current note to an octave
plus a major third above it.

<h2>Random Chords</h2>

![ ](../media/z06.mp4)

In LSDj version 4, the digits in the Z commands were not independent of one another, which
makes using Z with the C (Chord) command less useful, but that doesn’t mean you can’t get some
interesting sounds out of it. With the independence version 6 introduced, it’s possible to
gain more control so that, for instance, chords can randomly alternate between major and
minor. A minor chord is created with `C37`, and a major chord is created with `C47`. Therefore, if
we use a `C37` command and apply `Z10`, the Z command will apply either `C37` or `C47`.

<h2>Random Sweep</h2>

![ ](../media/z07.mp4)

Our final example is a
[signature Hypnogram sound](https://soundcloud.com/hypnogram/phantasm-dragon)
(listen at the 1:30 mark to hear it in context). It’s really fun and easy. Keep in mind that
this lead sound will only work in Pulse channel 1 as it’s the only channel that features a
hardware sweep.

<iframe width="100%" height="166" style="height: 166px;"  scrolling="no" frameborder="no" 
allow="autoplay" 
src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/319678401&color=%2322c8ff&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>

These are just a few examples of what you can do with the Z command. Don’t be afraid to
experiment and try to come up with your own!

------------------------------------------

Please support [Hypnogram](https://hypnogram.bandcamp.com) by buying their albums on Bandcamp!!

<center>
<iframe style="border: 0; width: 350px; height: 470px;" 
src="https://bandcamp.com/EmbeddedPlayer/album=696052333/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/transparent=true/" 
seamless><a href="https://hypnogram.bandcamp.com/album/xiii">XIII by Hypnogram</a></iframe>
</center>

