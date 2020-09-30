Intense Tech with Defense Mech -- Scoping Out New Features!
===========================================================

\- Posted January 15th, 2020 by [DEFENSE
MECHANISM](https://defensemech.com "Posts by DEFENSE MECHANISM")

<div>

Hello and welcome back to Intense Tech with Defense Mech! This time
let's cover some of the brand new features from LSDj version 7! I
guarantee you'll find something here that will pique your interest in
checking out the latest version, so let's dig in!

***Disclaimer: At the time of writing, version 7 is still buggy and WILL
CRASH! So feel free to play with new features, but please back up your
work! It is still recommended to stay at the latest stable version
6.9.0.***

------------------------------------------------------------------------

During the last several weeks, the benevolent developer Johan Kotlinski
has been hard at work making more improvements to the much-beloved LSDj
Game Boy tracker. Last time we left off at version 7.0.6 to talk about
the new functionality of DRUM pitch. This time we're taking a look at
version 7.7.4 and demonstrating some of the most exciting new features!
Let's get started!

FX/SPEED Setting
----------------

One new feature is the FX/SPEED setting. As its name implies, it sets
the speed for some effect commands: namely, C, P, R, and V commands (P
and V commands for pulse and wave channels are only affected in TICK
pitch). Increasing the value increases the number of ticks each effect
lasts, effectively slowing the speed of the effect. The video below
demonstrates each effect in order.

\
*Changing FX/SPEED to slow down effects*.\

B: mayBe Command
----------------

A brand new command has made its way into version 7. This command is
similar in some ways to [the Z command we've covered
before](dont-sleep-on-z-feat-hypnogram.html). Like Z, the B command can
be used to apply probability to notes or tables. Using B in tables also
allows probability to be applied. B works similarly to the H command in
that it will hop to a row, but whether it does so or not can be left up
to chance. Setting a B command of B05 will never hop to row 05, and
setting a B command of B85 will hop to row 05 about 50% of the time.
Setting BF5 will hop to row 05 about 15 times out of 16.

Using the B command with pulse, wave, and noise instruments allows a
probability to be set from 0 to F (15). Setting the command to B00 will
never trigger the note, and setting the command to B0F will always
trigger the note. Values in between apply other probabilities: B04 means
the note is 25% likely to play, B08 means the note is 50% likely to
play, and so on. For kit instruments, each digit affects the left or
right sample separately, meaning a command of B48 means the left sample
is 25% likely to play while the right sample is 50% likely to play.
Let's take a peek at how this looks *and* simultaneously scope out
another new feature, the...

Wave Channel Oscilloscope!
--------------------------

Perhaps the most mind-blowing feature will be easy to showcase here, but
all the same, yes, the wave channel now features an oscilloscope!

\
*Not the most inspired tune, but it sure is nice to look at!*\

Silky Wave
----------

Another equally awe-inspiring feature is dubbed Silky Wave. Many
long-time Game Boy musicians are probably familiar with the infamous
clicking of the wave channel endemic to the hardware itself. While it
previously required a brute acceptance of this hard fact, thanks to the
brilliant efforts of Johan Kotlinski, an incredible workaround has been
achieved! The details are perhaps a bit esoteric, but as best I
understand, a timer was implemented to allow changing the waveform at a
more opportune time and avoiding such a harsh click. What this means is
that a wave synth using the fastest Speed of 1 is now eminently more
audible at its intended frequency. The video below compares the silky
wave before and after.

\
*The extra clicking has been eliminated with silky wave!*\

R8x: Super-fast Retrig
----------------------

One of the most-requested features was the return of the old wave
channel pitch wrap. Interestingly, this characteristic sound was caused
by the sound generator restarting at a very fast rate. Using it on the
wave channel allows the sound to be tuned at the user's will rather than
simply relying on a P command. Using it on a pulse instrument such as a
kick allows the sound to go about 3 whole tones lower than the pulse
channel is normally capable of generating. Here's a video to
demonstrate!

Wave instrument finetune
------------------------

As the name of this feature implies, it is now possible to apply a
finetune from -F (-15) to +F (+15) in the wave instrument.

Max tempo increase
------------------

Again, as the title states, max tempo is now 295 BPM! Tempos from 256 to
295 BPM can also be applied using the T command values 00 through 27.

Faster song loading and saving
------------------------------

Loading and saving time for songs has been drastically decreased. You
might notice what appears to be visual glitches on the screen, but this
is completely intentional!

Did I leave anything out? Feel free to reach out to me at
defensem3ch\@chiptuneswin.com if you have any questions about these
features or other changes new in version 7! Until next time, I hope you
enjoy playing with the new version. This is DEFENSE MECHANISM, signing
off!

*Note: traducción al Español [por Pixel Guy encontrado
aquí](examinando-las-nuevas-funciones.html).*

</div>
