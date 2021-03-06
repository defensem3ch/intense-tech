**Intense Tech with Defense Mech – LSDj Wave Synth Deep Dive Part 1**
-Posted October 11th, 2018 by [DEFENSE MECHANISM](https://defensemech.com) *Note: [traducción al 
Español por Pixel Guy encontrado 
aquí](../es/analisis-del-sintetizador-del-canal-wave-en-lsdj-parte-uno.md.html).*

Hello, I’m DEFENSE MECHANISM! Welcome to the first installment of Intense Tech, where we’ll
take an in-depth look at some of the features LSDj. My aim is to impart to you knowledge and
wisdom to pass on to the following generations of chiptuners, thus creating an army of
bleepbloopin’ masters!!

This inaugural tutorial will cover what one needs to understand the Wave channel synth!
Specifically getting into the wave synth parameters of Signal, Filter, Volume, Q, and Cutoff.

-----------------------

<center>

If you like this article, please check out the corresponding [LSDj Learning Lab video series about 
the wave channel!](https://www.youtube.com/playlist?list=PLfhdj6Qak_ehuZgnwhiz9akZnTMsDeNpy)

<iframe width="560" height="315" style="width: 560px; height: 315px;" src="https://www.youtube.com/embed/videoseries?list=PLfhdj6Qak_ehuZgnwhiz9akZnTMsDeNpy" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</center>

-----------------------

One of the most confusing and possibly intimidating features of LSDj is the Wave channel
synth. Hopefully after working through this exercise and the next, you’ll not only find that
it’s easy to use, but once you have a clear idea of how it works, you’ll understand why it’s
one of the most powerful aspects of LSDj!

I’ll walk through each parameter in-depth to demystify what’s really going on; but first,
let’s start with a quick overview of the Game Boy Wave channel itself.

The Wave channel plays a 4-bit, 32-sample waveform. This can be represented by 32 digits in
hexadecimal `0-F`, as seen on the LSDj Wave screen below.

![Heads up: `8ECDCCBBAAA999888776665554433231` **WILL** be on the test.](../media/bgb_2018-09-24_11-43-06.png)

What this means is that each sample can only have a volume of one value ranging from 0 through
15 (`0` through `F` in hexadecimal). Compared to 16-bit audio (the most common recording standard)
which allows for 65,536 unique volume levels, the Gameboy’s 4-bit audio depth only allows 16
volume levels! While this may seem like a lot less to work with in comparison,
that’s OK because it’s part of what gives the Wave channel its characteristically
crunchy sound.

Let’s begin by taking a look at some basic audio waveforms, as shown on
  [this graphic from Wikipedia](https://en.wikipedia.org/wiki/Sine_wave#/media/File:Waveforms.svg)

![](../media/firefox_2018-09-24_12-03-51.png)

By the end of this lesson you’ll understand how to make a sine wave. Before we get there,
first I need to explain some theory behind how a musical note is produced.

Sound is made by vibrating air, and each waveform above represents what those vibrations would
look like if you could see them. You can also visualize them by imagining the way a speaker
cone moves back and forth when producing sound. The sine wave is the most basic waveform – it
contains only the pure fundamental frequency of the root note. The other waveforms contain
other [overtones](https://en.wikipedia.org/wiki/Overtone) (multiples of the
fundamental frequency). By combining different overtones at different ratios, we can create
different-sounding waveforms (this is known as changing the “timbre” of the sound itself).
When you hear the difference between a note played on a violin and the same note played on a
flute, a lot of the difference in the timbre that you hear results from the mixtures of
different overtones that are produced in the vibrating air.

To give an example of an overtone, if you multiply a frequency by 2, you get the same pitch
but 1 octave above. As you increase the multiple by 1, you create the next overtone.

Example: A 220 Hz (LSDj A3) – fundamental, aka root note

(note names in LSDj correspond to version 6+; for version 4, add 1 octave)

A 220 Hz x 2 = A 440 Hz (LSDj A4) – 1 octave above (1st overtone)

A 220 Hz x 3 = E 660 Hz (LSDj E4) – 1 octave + one 5th (2nd overtone)

A 220 Hz x 4 = A 880 Hz (LSDj A5) – 2 octaves above (3rd overtone)

A 220 Hz x 5 = C# 1100 Hz (LSDj C#5) – 2 octaves + 1 major 3rd (4th overtone)

A 220 Hz x 6 = E 1320 Hz (LSDj E5) – 2 octaves + one 5th (6th overtone)

![The first 6 notes in the harmonic series of A 220 Hz](../media/harmonicseries.png)

The [harmonic series](https://en.wikipedia.org/wiki/Harmonic_series_(music)) of a
note includes the note at its fundamental root frequency, plus that frequency multiplied by 2,
3, 4, and so on.

Each multiple of 2 (2, 4, 8, 16, etc) represents octaves of the fundamental frequency.

Each multiple of 3 (3, 6, 12, etc) represents one 5th above the fundamental frequency (except
9 and its multiples which represent a major 10th).

Each multiple of 5 (5, 10, 15) etc. represents a major 3rd above the fundamental.

Some odd-numbered multiples including 7 and above don’t match traditional notes, for example 7
is kind of an out-of-tune minor 7th, or 11 which is an out-of-tune flat 5th.

(Even the major 3rds in the harmonic series are tuned slightly differently than most of our
modern tuning, but it should be close enough that it will make sense to your ears.)

The default waveform in LSDj is a
[sawtooth wave](https://en.wikipedia.org/wiki/Sawtooth_wave), which is created when
sine waves of the all notes in the harmonic series are combined together.

![One complete cycle of a sawtooth wave generated in 
Audacity](../media/audacity_2018-09-24_11-42-38.png)

![One complete cycle of a sawtooth wave generated in LSDj](../media/bgb_2018-09-24_11-43-06-1.png)

Listen to this audio example of the sawtooth wave in Audacity, followed by sawtooth wave in
LSDj at 440 Hz:

![ ](../media/sawtooth.mp3)

![(waveform output side-by-side for comparison)](../media/audacity_2018-09-24_11-58-07.png)

You’ll hear a bit of difference, but all in all the LSDj version sounds surprisingly faithful
to the higher quality audio.

This sawtooth wave is represented as ![](../media/bgb_2018-09-24_13-37-35.png) in the LSDj
Synth screen.

The [square wave](https://en.wikipedia.org/wiki/Square_wave)
![](../media/bgb_2018-09-24_13-37-55.png) is constructed by combining sine waves of the
harmonic series, but only the odd overtones. Most of us probably know the distinct bloopy
sound of a square wave – this waveform can also be made in the pulse channels set to 50% duty
cycle.

The [triangle wave](https://en.wikipedia.org/wiki/Triangle_wave)
![](../media/bgb_2018-09-24_13-38-14.png) (note: don’t be fooled that the triangle icon looks
like a sine wave) is constructed the same as the square wave, using only odd harmonics, but
decreasing further in volume the higher they go (moreso than those of a square wave). This is
a good sound for a very deep bass, as you might be familiar with if you have heard the NES’
4-bit triangle channel.

It may not seem possible to create a sine wave in LSDj given that the “Signal” parameter has
only these 3 options, and Sine is conspicuously absent. However, because each of these
waveforms is fundamentally constructed from sine waves, I can show you how to extract a sine
wave from any of these options.

Conveniently, the next parameter in the Synth screen, “Filter”, is just the tool we need.

With “Filter”, we have 4 options: Lowpass (Lowp), Highpass (Highp), Bandpass (Bandp), and
Allpass (Allp).

If you’re familiar with a traditional filter on an analog synth or digital plugin you might
understand these. If not, you can think of the filter in LSDj as allowing you to choose which
harmonics in the sound you would like to produce in your resulting waveform. The frequency
that the filter acts on is selected by the “Cutoff” parameter.

With Lowpass, only the low harmonics of the Cutoff and below will “pass through” the filter,
meaning your fundamental frequency is the lowest tone, but you can expand to include up to the
highest harmonics (in LSDj that’s up to 15 overtones, in theory). With Highpass, only the
highest harmonics of the Cutoff and above will pass through, but you can expand to the lowest.
With Bandpass, only the range of harmonics specified by Cutoff will pass through. And with
Allpass, all harmonics will pass through, but the phases of some harmonics will be shifted
where the Cutoff is emphasized, which produces different timbres as a result.

That dry explanation aside, next let’s take a look at what happens when we set our lowpass
filter cutoff to `10`. Since this is `10` (16 in hexadecimal) out of a possible `FF` (255 in
hexidecimal), we’ve set our filter to allow only the lowest note in the harmonic series, the
fundamental. Remember that if you want to hear only the first waveform of the synth, set Play
to Manual in the Wave Instrument screen.

![A wild sine shape appears!](../media/bgb_2018-09-24_12-58-37.png)

We can see that it looks a little bit squashed, so let’s increase the Q, also known as
resonance. This parameter will give us a boost in the volume wherever our filter cutoff is
set, while leaving the rest of the harmonics at the same volume. Let’s set Q to `1` to boost the
volume of the fundamental only and see what we end up with:

![](../media/bgb_2018-09-24_12-55-16.png)

It’s somewhere in between a sine and a squashed triangle. Let’s lower the Volume to `08` and
raise Q to `3`. The Volume parameter adjusts the overall volume of the Signal before the Filter
and Q are applied.

![](../media/bgb_2018-09-24_12-56-05.png)

That’s looking pretty close to a sine wave, I’d say! Feel free to experiment with different Q,
Cutoff, and Volume values and adjust them to your liking.

Playing notes at low octaves with this waveform creates the lowest, bassiest possible sound
you can get in the Wave channel. It contains the fewest overtones possible, making it
perfectly suitable for a low kick or sub-bass. In a perfectly ideal situation, a sine wave
contains no overtones at all, only the fundamental frequency. However, because the wave
channel bit depth only gives us 16 volume values, we can only roughly approximate a sine wave,
and as a result some additional overtones creep into the sound.

Finally to wrap up the lesson, I want to show that every multiple of `10` of the “Cutoff”
actually represents 1 overtone of the harmonic series. This becomes even clearer when we
change “Lowpass” to “Bandpass” and raise our Volume to `20`. Notice that if you set the Cutoff
to `20`, you’ll hear the overtone 1 octave above. If you set the Cutoff to `30`, you’ll hear the
overtone 1 octave + one 5th above. If you set Cutoff to `40`, you’ll hear the overtone 2
octaves above, and so on. As you raise your filter cutoff, you can experiment with increasing
the Q value to further emphasize the overtone you’ve selected – the higher your filter cutoff,
the lower in volume the resulting overtone will be (this is a natural feature of how a
sawtooth wave is produced).

![](../media/bgb_2018-09-25_14-14-37.png)

And remember if you change your waveform to square or triangle, there are fewer overtones in
those waveforms, so it may seem as if some of the octaves or other overtones are missing!

Cutoff at `20`:

![](../media/bgb_2018-09-24_13-12-35.png)

![ ](../media/cutoff20.mp3)

Cutoff at `30`:

![](../media/bgb_2018-09-24_13-12-50.png)

![ ](../media/cutoff30.mp3)

Cutoff at `40`:

![](../media/bgb_2018-09-24_13-13-03.png)

![ ](../media/cutoff40.mp3)

Are you seeing any pattern in the resulting waveforms as we increase filter cutoff? Keep your
observations in mind, as we’ll use them in the next installment!

