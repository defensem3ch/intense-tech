Intense Tech With Defense Mech -- Let's Appreciate Version 8!
=============================================================

\- Posted March 26th, 2020 by [DEFENSE
MECHANISM](https://defensemech.com "Posts by DEFENSE MECHANISM")

<div>

Hello again, and welcome to another edition of Intense Tech! This month,
I'd like to highlight some of the changes that've been implemented since
[my version 7](scoping-out-new-features.html) article. Let's dive on in!

------------------------------------------------------------------------

### The LSDJ Manual has been updated to version 8!

For those of us who like to RTFM, it's nice to know that the official
LSDJ manual has now been updated with all the new changes for version 8!
So if you have specific questions about features or functionality, the
answers can most likely be found in the manual, which is located [on the
LSDJ website in the documentation
section.](https://www.littlesounddj.com/lsd/latest/documentation/)

### New screen layout

The screen layout has been updated to reduce the amount of switching
between screens. Instead of the old three-row layout, there are now only
two rows. The main row which includes the Song, Chain, Phrase,
Instrument, and Table screens, remains unchanged. The top row now
includes, in order from left to right, Project, Groove, Synth, and Wave
screens. Additionally, when navigating upwards from the main row, LSDJ
remembers which screen you were on previously. This enables easy
switching between the Phrase screen and the Synth screen, for instance.
Some shortcuts exist for convenience: for example, navigating upwards
from the Song screen always goes to the Project screen, and going
upwards from a G command will always go to the Groove screen. Here's a
map of the new screen layout from the LSDJ manual:

<div>

![](image4.png){width="659"}

</div>

### ADSR for Pulse and Noise Instruments

As mentioned in the previous [interview with Johan
Kotlinski](interview-with-lsdj-developer-johan-kotlinski.html), the
Envelope settings for Pulse and Noise instruments is now replaced with
ADSR for finer volume control. The ADSR has three stages, each with two
digits: the first digit 0 through F controls volume, and the second
digit 0 through 7 controls duration (0 holds at that volume
indefinitely). An ADSR of 5100 is like the old Envelope of 51, volume
starts at 5 and quickly decays to 0. An ADSR of 246732 would start at
volume 2, rise to volume 6 somewhat quickly, decay to volume 3 more
slowly, then quickly fade to 0. Using the ADSR in combination with
commands such as RFx (retrigger with a decrease in volume) can act
similarly to a tremolo command. E commands and the volume columns in
tables remain unchanged and function the same as they have previously --
they will override the ADSR volume when used in tables or phrases.

### Z command enhancements

In the post ["Don't Sleep on Z (feat.
Hypnogram)"](dont-sleep-on-z-feat-hypnogram.html), I indicated that Z
did not work with D, G, or H commands. This is no longer the case! Z now
works with every command except H (and of course, Z itself). This could
make for some very interesting rhythmic consequences, as we now have the
ability to randomize using a straight groove or a swung groove, for
example. I'm really looking forward to trying this out and seeing what
happens!

### Miscellanous minor changes

To wrap up this entry, there are a few minor changes that are likely
worth mentioning to help avoid confusion. Let's have a little "lightning
round" of small changes:\
\
• Tables can now switch between "Play" and "Step", where Play is the
usual 1-tick-per-line, and Step is what was previously called
"Automate".\
\
• The setting previously called "FX/SPEED" in version 7 has been renamed
to "CMD RATE".\
\
• The wave instrument screen now shows the parameter "Loop Pos" instead
of "Repeat" and rather than setting how many frames will loop, it sets
the position of the loop point. Setting the loop point to 0 will repeat
every wave frame specified by the length for the instrument.\
\
• Using R commands in the wave channel will now retrig the synth from
the beginning wave frame.\
\
• Wave instruments are now set to Manual playback by default.\
\
• Synths can now be cloned from the Wave Instrument screen (press
Select+(A,B) on the Synth number).\
\
• By default, a new instrument is set to use the channel where it was
created.\
\
• Setting xF in the table volume column will hop to row x.\
\
• It's now possible to use prelisten with a PS/2 keyboard, and to
configure key delay in the Project screen.\
\
• "Clean Song Data" and "Clean Instrument Data" now remove duplicate
chains, instruments, and tables.

### Optimizations and tweaks for usability

This is truly last but NOT least! Many changes have been made to
optimize the playback of songs and the responsiveness of the interface.
For a while, it's been known by many users that simultaneously using V
commands in three channels could potentially cause the Game Boy to slow
down, freeze, become unresponsive, and/or possibly crash. *This is no
longer the case!* The old brick DMG can handle this and more at tempos
in excess of 250 without choking or slowing down. Some of the button
presses (such as pressing A twice to make a new chain) have been
optimized to be more user-friendly, and screen navigation and scrolling
is more responsive.

Once again, a huge thanks to Johan Kotlinski for doing some amazing work
over the past few months to make version 8 a truly incredible piece of
software, and making improvements that almost seem like they should be
impossible!

Let me know if you have any questions about the new version, or ideas
that you would like to see for future installments of Intense Tech by
emailing me at <defensem3ch@gmail.com>! Until next time, this is DEFENSE
MECHANISM, signing off!

*Note: traducción al Español [por Pixel Guy encontrado
aquí](apreciemos-la-version-8.html).*

</div>
