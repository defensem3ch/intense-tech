**Intense Tech With Defense Mech -- Let's Mix It Up (and Down)!**
- Posted April 30th, 2020 by [DEFENSE
MECHANISM](https://defensemech.com) *Note: [traducción al Español por Pixel Guy encontrado aquí.](../es/15-que-no-se-te-pase-la-mezcla.md.html)*

Hello again, and welcome back to another edition of Intense Tech! This
month, let's take a look at some different ways to consider mixing in
LSDj. After reading this article, I hope you'll have some new ways to
think about working with the volumes, stereo panning, and frequency
ranges of your instruments to make them shine throughout your tracks!
Let's dig in!

------------------------------------------------------------------------

Ever since I started using LSDj, I've always struggled to make the parts
fit in such a way that they enhance each other, but I've stumbled upon
some ways to help balance instruments and channels such that each part
has a place and complements the others.

While it's worthwhile to think about mixing in terms of volume of the
instruments and channels, there are other ways to adjust the sound that
don't involve simply turning volumes up and down. We can also think
about stereo placement of the sound, as well as frequency range. If we
consider these three options together, we can have even more
possibilities when balancing the components in a mix, even on a Game
Boy!

Control Space Using Panning
---------------------------

One of the great strengths of the Game Boy's sound chip is that it has
stereo sound control. Even though you can only control Left, Right, or
both channels at once, it can still be used to great effect. Even just
adding some alternating panning on things like pulse channel notes or
noise channel hi-hats can create a sense of space and ambience. In this
example, first an arrangement plays a lead in the first pulse, some
backing harmony in the second pulse, a kick and bass in the wave
channel, and hi hats and snare in the noise channel. Listen to the
difference between the first part without panning, and the second part
with panning:

![ ](../media/panning.mp4)

Control Frequency Using Octaves
-------------------------------

This might seem so obvious, but don't overlook the possibilities that
you have by doing some simple octave transposing. Using the previous
example, let's examine what happens when we apply an octave transpose to
the melody:

![ ](../media/octave.mp4)

This can freshen up a lead that might seem a bit stale, and it has the
added benefit of making sure that two instruments don't get caught
fighting in the same frequency range. Think about playing a piano with
two hands: it's much easier to place your left hand in a lower range of
the piano, and your right hand above it in a higher range. If both hands
are trying to play notes in the exact same octave, it can seem like the
hands are trying to battle it out. Rather than increasing the volume,
try seeing if you can change the frequency so that each channel is
situated comfortably in its own range. While this won't work for every
case, you might find that it opens up quite a bit of room in the mix ---
and when you only have four bits of dynamic range, every little bit
counts!

Control Volume Using Transients
-------------------------------

A [*transient*]("https://en.wikipedia.org/wiki/Transient_(acoustics)") is
a sound that contains a sudden loud, short burst at the beginning. I
learned this great trick from [Pain
Perdu](https://soundcloud.com/pain-perdu): You can utilize this burst of
noise to make a snare stand out in the mix without overpowering the
other channels. Here is are three example of a snare that's soft, then
loud, then utilizing a transient:

![ ](../media/snare.mp4)

Setting the instrument volume to a relatively medium or high volume like
90 means the instrument starts with this loud volume, and the volume is
reduced when the E command plays in the table. This also means you can
use E commands in the phrase next to the snare if you want to raise or
lower the volume of the transient. As you can hear, it can help the
snare cut through the mix and creates more impact without blasting over
everything else, offering some nuance to your percussion. This can also
be used effectively for other noise instruments or even pulse
instruments.

Control Wave Channel Volume Using Limit
---------------------------------------

The wave channel can provide a lot of power and impact in a track, but
sometimes volume control can be tricky. Using E commands provides
limited help in cases where `E03` at 100% volume is too loud, but `E02` at
50% volume is too soft. Using Limit in the wave synth instrument lets
you keep the wave synth at full volume while controlling the maximum
volume of the waves. You might recall that Limit will constrain the
dynamic range of the waveform to a certain range of volume, no matter
how loud the Volume for the wave synth or the wave instrument is set.
Setting Limit to `8` will reduce the wave instrument to 50% volume even
while set to Volume level `3`, so setting Limit anywhere from `9` (about 56%
volume) to `E` (about 94% volume) will allow you to access more variation
in volume. See the example video below:

![ ](../media/limit1.mp4)

Additionally, if you set the start and end points to different Limit
values, you can use W commands to control the speed and length. This
allows for even greater control of volume, as shown in the following
example:

![ ](../media/limit2.mp4)

Control Pulse Channel Volume Using ADSR
---------------------------------------

Lastly, there is a wonderful feature in the newest versions of LSDj
which is the volume
[ADSR]("https://en.wikipedia.org/wiki/Envelope_(music)#ADSR"). It might
seem confusing at first, but you can consider it like chaining E
commands together. For each stage of the ADSR, the first digit specifies
volume and the second digit specifies the length. Once you provide the
second digit, the next stage opens. This can be used similarly to a
transient, to start loudly and fade to a lower volume. Or, it can be
used to start at a low volume and fade in to a higher volume. The big
advantage to fading in with ADSR is that, unlike with an E command which
fades in, increasing in volume until the volume maxes out at F (or until
the next E command), the next stage of the ADSR can be set to a lower
maximum volume. Here's an example of how the ADSR works:

![ ](../media/adsr.mp4)

In previous versions as well as current versions of LSDj, ADSR can be
mimicked with the volume column of a table. Although it uses an extra
table, it can be helpful when the regular E commands don't provide the
extra level of detail you might need when trying to get that part to sit
just right in the mix.

