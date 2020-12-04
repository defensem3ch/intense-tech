**Intense Tech with Defense Mech – ADSR Makes Life Easier!**
-Posted November 29, 2020 by [DEFENSE MECHANISM](https://defensemech.com) *Note: [traducción al 
Español por Pixel Guy encontrado aquí](../es/18-el-adsr-hace-la-vida-mas-facil.md.html).*

Hello and welcome to another edition of Intense Tech! This time we'll be taking a look at a 
relatively new feature introduced in version 8.1.0: pulse and noise instrument ADSR! This is a 
pretty big upgrade from the old envelopes, so we'll examine what's new and different. We'll also 
cover a pretty substantial change from previous versions: the change from hardware to software 
volume in 8.8.0. Let's dig in!

--------------------------------------------------------------------
Attacking the Volume Learning Curve
--------------------------------------------------------------------
ADSR, which stands for Attack-Decay-Sustain-Release, refers to four stages of volume that are 
usually considered when shaping a sound. This can be visualized as the following:

*****************************************
*        .                              *
*       / \                             *
*      /   \                            *
*     /     '-------------------.       *
*    /                           \      *
*   /                             \     *
*  /                               \    *
* Attack  Decay   Sustain       Release *
*****************************************

A sound with a long attack starts at a low volume and increases volume slowly, whereas a sound with 
a short attack increases to a loud volume nearly instantaneously; likewise, a sound with a short 
decay will quickly fade to silent, but a long decay allows the sound to fade out slowly. Sustain 
allows you to optionally set a constant volume if the note is held. Lastly, setting a short or long 
release will allow the note to fade quickly or slowly, respectively, to silence from the sustained 
volume after the note is released. Like sustain, this is also optional, and may have no effect if 
sustain is not enabled.

With all that explained, we can begin to discuss how the ADSR works in LSDj. You may already be 
familiar with the previous instrument envelopes, as well as E commands, where the first digit 
represents an initial volume of `0` through `F`, and the second digit represents the decay: values 
of `1` through `7` *decrease* volume where `1` is the fastest and `7` is the slowest, and values `9` 
through `F` *increase* volume where `9` is the slowest and `F` is the fastest. Values `0` and `8` 
sustain the note at the volume of the first digit indefinitely.

Like the E commands, the ADSR works in a similar fashion. Rather than setting a volume for each 
distinct stage of Attack-Decay-Sustain-Release, each stage of the ADSR essentially acts as one E 
command. The first digit specifies the volume, and the second digit specifies the length of time to 
retain that volume. Whether the volume increases or decreases over that length of time is specified 
by the next stage of the ADSR, until the third stage is reached, when the volume will fade to zero.

**Example: `54/00/--`**

A sound with this ADSR would start at volume `5`, then decay with speed `4` to silence.

**Example: `03/A2/71`**

A sound with this ADSR would start at volume `0`, quickly increase at speed `3` to volume `A`, then 
quickly decrease at speed `2` to volume `7`, and quickly fade to silence at speed `1`.

**Example: `74/07/43`**

A sound with this ADSR would start at volume `7`, then decay with speed `4` to volume `0`, then 
increase slowly at speed `7` to volume `4`, then fade to silence at speed `3`.

Upgrading Volume Control with New Versions
------------------------------------------

In all versions of LSDj before 8.8.0, the volume for pulse and noise is controlled by the Game Boy 
hardware. An unfortunate side effect is that when hardware envelope is changed, the pulse or noise 
channel's sound is reset, which results in an audible click. In the noise channel this also results 
in a slight change in the tone of the noise for an instant after resetting. Therefore it was not 
possible to achieve smooth transitions between stages of the ADSR.

However, beginning with version 8.8.0, software has taken over control of the volume! Volume changes 
now happen without any reset of the sound, resulting in smooth uninterrupted volume changes for 
pulse and noise channels. Using the volume column in tables no longer generates clicks either, 
offering yet another method of click-free control.

E commands work as before to maintain compatibility with older songs, but software ADSR adds more: 
speed `1` is extremely short, while speed `F` is a bit longer than the previous speed `7`.  Here's a 
chart that shows the best correspondence of the old hardware envelopes to the new software ADSR:

<style>
th { display: none;}
</style>
--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--
**Software** | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F
**Hardware** | 0 | - | - | - | - | - | 1 | - | 2 | 3 | 4 | 5 | 6, 7 | - | - | -

As you can see, we have five lengths that are faster than the fastest hardware envelope, and three 
that are longer than the longest! Using the faster software speeds gives us very fine control over 
the attack and decay, which is extremely useful when designing percussion instruments, especially at 
slow tempos. Setting the length to `0` always sustains indefinitely at the specified volume.

Instant Decay
----------------------

To create a sound that decays instantly, set the second or third stage of the ADSR to a length of 
`1`. The following example shows a 2-stage ADSR with instant decay.

![Instant decay](../media/adsrinst.mp4)

Noise Percussion Transients
---------------------------

Here are a couple examples of noise percussion with transients.

The following video shows four hi-hats with a transient of volume `6` quickly lowered to volume `4` 
and then fading to silence, followed by four hi-hats that start at volume `4` and fade to silence.

![ADSR Hi-hat](../media/adsrchh.mp4)

Do you notice the extra impact of the first four hi hats? Although it's subtle, even this simple 
adjustment can help hi-hats to cut through the mix. You can play with the volumes and lengths of 
both stages of the ADSR, and even use both instruments - maybe you want transients to only happen on 
the downbeats.

The first example below is of a snare using E commands in a table with hardware volume in version 
8.5.0.  The second example is of a snare using transients in ADSR in version 8.9.6.

![Snare with transients in v8.5.0](../media/esnare.mp4)

![Snare with ADSR in v8.9.6](../media/adsrsnare.mp4)

As you can see, it's now possible to achieve these sounds without resorting to placing E commands in 
an instrument table. At slow tempos, these transients can last less than a tick, which is impossible 
to achieve only controlling the volume from a table. You may also notice that the K command no 
longer causes a click at the end of the note.

***Important note: BGB does not support software envelope at all if it is running in Gameboy mode.  
If you use BGB, make sure you set the emulator to Gameboy Color, or the volume will not work 
correctly.***

Re-thinking Tremolo
-------------------

One neat side-effect of ADSR is what happens when R commands are used. Because the R command can 
change the volume on each retrig, it's now possible to achieve a kind of tremolo effect. Here's an 
example:

![Tremolo with ADSR and R command](../media/tremolo.mp4)
