Intense Tech with Defense Mech -- Let's Table This Discussion!
==============================================================

\- Posted July 23rd, 2019 by [DEFENSE
MECHANISM](https://defensemech.com "Posts by DEFENSE MECHANISM")

<div>

Welcome back to Intense Tech with Defense Mech! In this post I wanted to
discuss some different ways to use tables in LSDj. After reading this
lesson, I hope you'll be inspired to use tables in new and inventive
ways! Let's [set the table](http://penzeys.com) and get started!

------------------------------------------------------------------------

Tables in LSDj are arguably the sole most useful feature to shape your
sounds. They can be used on almost any instrument, from pulse arpeggios
and leads to bass and percussion, and there never seems to be enough of
them to go around! In this lesson, I'll go over a few techniques for
tables to fuel your creativity.

First, let's go over the basics. There are four columns in a table:
Volume, Transpose, and two columns for Effect Commands. The volume
column can be used to make custom volume envelopes for instruments. The
first digit specifies volume (0-F for pulse and noise channels, and 0-3
for wave channel) and the second digit specifies the number of ticks to
hold that volume. So a volume column value of 36 would set the
instrument to volume 3 for six ticks. After six ticks, the next line of
volume is applied until the last volume command. The instrument will
remain at the volume level specified in the last line until the note is
killed, unless all 16 steps of the volume column are full, in which case
the volume column will loop, restarting from the top once the last line
is reached. In the following example, I've set a table to automate the
volume of a wave bass from volume 1 for three ticks, volume 2 for three
ticks, then volume 3 for the next tick after which it will remain that
volume.

The transpose column, commonly used for custom arpeggios, applies the
value of transpose to the current note in semitones, with 01-7F
transposing upwards and 80-FF transposing downwards. The effect command
columns are largely similar to the effect command columns in phrases,
with the exception that some commands are not usable in tables (such as
D) and L commands function according to the transpose column (only in
the first column. Also if L00 is applied, the instrument pitch will
reset).

Tables run by default at one tick per line unless the speed is specified
using a Groove command. However, a table can also be set to Automate,
meaning the table will apply one line per note.

#### Using A Commands in Tables

It might be somewhat confusing at first but it's entirely possible to
apply a table from within a table. This can be useful when a table is
set to Automate if additional effects need to be used simultaneously on
the same note. In this example, the instrument runs table 01 with
Automate. One command is used in the phrase, one command is used in
table 01, and A02 applies table 02 in the second column of table 01. Two
additional commands are used in table 02, making for a total of four
commands at once!

Used within a table without Automate, an A command effectively extends
the current table into the table specified. Lastly, using a value of 20
or above will effectively stop the table, since no tables beyond 1F
exist. This is a great way to end the table without killing the note
with a K command.

#### Simultaneous Automation

I discovered a neat trick that happens when two channels, such as both
pulses, use the same instrument with Table set to Automate=On and play
notes simultaneously: notes in channel 1 are effected by the
even-numbered table rows, and notes in channel 2 are effected by the
odd-numbered table rows. This allows for easy stereo panning or similar
effects using only one table, one instrument, and one phrase!

#### Beef up instrument attack

Tables are extremely handy to give your instruments extra pop. One way
to do this is by using volume commands. This can also be done in the
volume column, but sometimes it can be more convenient to use a command.
In this example of a noise snare, the instrument volume sets the volume
of the initial attack, and then an E command lowers the volume
drastically. The instrument volume is set relatively high to give the
snare an initial pop to help it cut through other instruments, but then
backs off so it doesn't dominate throughout with very high volume.

It may be familiar to you that accents such as placing 0C in the first
tick of the Transpose column, or changing pulse waveforms on the first
and second ticks can be effective ways to accent your instruments.
Another trick to enhance the attack of an instrument such as a pulse or
wave lead is by setting a high-frequency V command on the first tick,
then turning it off on the second tick with a V00 command, or using
lower values for a more subtle vibrato. These techniques can also be
combined for greater effect.

There are so many more ways to use tables that this article could easily
go on for many pages with examples! I hope this sparks some ideas for
you when designing your instruments. Please [let me
know](mailto:defensem3ch@gmail.com) if you have table tricks of your
own, or new ideas you might like to see me cover in the future. Until
next time, this is [DEFENSE MECHANISM](https://defensemech.com), signing
off!

*Note: traducción al Español por [Pixel Guy encontrado
aquí.](entablemos-una-discusion.html)*

</div>
