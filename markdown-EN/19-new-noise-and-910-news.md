**Intense Tech with Defense Mech – New Noise and 9.1.0 News!**
-Posted January 17th, 2021 by [DEFENSE MECHANISM](https://defensemech.com)

Hello and welcome to another edition of Intense Tech! In this article, we'll talk about the changes 
in the recently-released version 9.1.0 of LSDj! This version is exciting, although it does include 
some changes that will potentially break the noise instruments in your existing songs. In order to 
prepare you for the changes, let's take a closer look!

---------------
Channel Changes
---------------

If you've ever thought the LSDj noise channel was confusing, you are not alone! Even though I 
previously wrote an [article explaining its inner 
workings](https://defensemech.com/intense-tech/en/17-the-joys-of-noise.md.html), it was not enough 
to demystify its strange behavior.  Clearly, the usability could be improved, and this prompted a 
reorganization of the entire noise channel for version 9.1.0. The new organization places all noise 
notes in order of frequency: first, the long-loop noises are ordered lowest to highest from notes 
`00` to `3B`.  Above that, the short-loop notes are organized lowest to highest, from octaves -9 
(negative 9) to 8, using note names to represent the notes that each frequency most closely matches 
(C, D, F, and G#). Each octave from -9 through 4 contains these four notes; octaves 5 through 8 only 
contain the note C (except for an extra F in octave 5).

![The noise channel uses notes again, but this time they are **actual 
notes!**](../media/noisenotes-1610903754.mp4)

If you load up an existing song or save file into version 9.1.0, your noise notes will be 
automatically converted -- however, any transpose or S command values will not. As a result, I've 
devised this handy noise converter if you are interested in manually changing the values in the 
noise channel phrases or tables. (You can also [find this converter without the article 
here](https://defensem3ch.github.io/noise-convert).)

A Whole New Land of Commands
----------------------------

One of the most useful and most exciting changes is that now it is possible to use the P command to 
sweep smoothly through the noise frequencies without using a custom table. The P command has also 
changed slightly in functionality due to added speed control: rather than `P01` applying `S01` every 
tick, it applies `S01` every 4 ticks, and `P04` applies `S01` every tick, allowing for finer control 
over the final sound of the sweep. Having that extra control means it's now possible to do some 
really nice noise kicks, hi hats, and crashes without devoting extra tables to those sounds.

![Here is an example phrase demonstrating a kick, hi hat, and crash with the same 
instrument.](../media/noise-1610903555.mp4)

Another change for commands in the noise channel is that the C command now functions essentially the 
same as it does in the pulse and wave channels in that it arpeggiates between the root note, the 
second digit, and the third digit. The most basic difference is that the values are limited to only 
the notes available in the noise channel. So to create an F minor triad arpeggio, place the note `F  
5` and apply a C command of `C12`. This will arpeggiate between F, G# (or Ab), and C. Larger values 
will extend to multiple octaves.

![An example of arps with C command](../media/noisearps-1610903924.mp4)

Lastly, a new command has been added! The V command can add noise vibrato (this vibrato is always 
tick-based).

![Vibrato can range from subtle to extreme at high values!](../media/noisevib-1610904078.mp4)

What Else is New?
-----------------

Since the last Intense Tech, besides a few bug fixes and cosmetic changes, a few other notable 
changes have been made. Let's cover them quickly!

<big>**Faster Playback Indicators**</big>

The update to version 9.0.1 includes new sprite-based playback indicators in song, phrase, and table 
screens - they now update at 60 Hz, making table indicators much more visible!

![Epic table view!](../media/table-1610904442.mp4)

<big>**TICK Vibrato Changes**</big>

Also, tick-based vibrato speeds have been changed to be more rhythmic at the default groove. This is 
explained in the changelog like so:

```none
V vibrato rates in PITCH=TICK mode now match phrase steps:

    V0x = 16 steps
    V1x = 12 steps
    V2x = 32/3 steps
    V3x = 8 steps
    V4x = 6 steps
    V5x = 16/3 steps
    ...
    VFx = 1/2 step
```

<big>**Increased precision for instrument FINETUNE**</big>

FINETUNE values in instruments are now expanded to two digits. A previous finetune value of `01` now 
equals `10`.

<big>**Bookmark changes**</big>

Bookmarking individual chains in the song screen has been changed in favor of bookmarking entire
rows. Pressing B+Up/Down will jump between previous and next bookmark.

![Jumping between bookmarks](../media/bookmarks-1610904841.mp4)

<big>**Wave synth LIMIT overflow**</big>

LIMIT in wave synth has been expanded to two digits, and it can now be increased beyond a value of 
`0F`. By doing so, it's possible to create a kind of overdrive.  This also allows for the ability to 
wrap values while using CLIP distortion, as well as introducing new higher harmonics. Try it out and 
see what kind of new sounds will result!

![Increasing LIMIT beyond `0F`](../media/limit-1610904715.mp4)

<big>**Wave F command overrides silky wave**</big>

F commands in wave phrases had previously been delayed by silky wave, but the commands now happen 
instantaneously as they did before silky wave was implemented in version 7. While this will 
reintroduce slight clicking, it allows for immediate wave frame changes for enhanced rhythmic 
precision as it has in past versions.

<big>**Noise instruments no longer need FREE/STABLE**</big>

Noise FREE/STABLE setting was removed and random noise channel muting has been reduced. However, 
many hardware Gameboy models are still affected by a hardware bug that could cause the noise channel 
to mute randomly, while emulators such as BGB and Sameboy, as well as most Gameboy Advance models, 
are unaffected.
