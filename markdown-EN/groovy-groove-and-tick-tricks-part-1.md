Intense Tech with Defense Mech --- Groovy Groove and Tick Tricks Part 1! {#groovy-groove-and-tick-tricks-part-1}
========================================================================

\- Posted April 11th, 2019 by [DEFENSE
MECHANISM](https://defensemech.com "Posts by DEFENSE MECHANISM")

Hello and welcome back to Intense Tech with Defense Mech! This month
I'll be sharing a few examples of how to use different grooves in LSDj.
After you read this lesson, you should feel comfortable using more
advanced techniques to manipulate timing in your LSDj songs!

------------------------------------------------------------------------

I'd like to start with covering the [basics](http://penzeys.com), so
bear with me as we may be retreading familiar territory. First, what is
a **tick**? A tick is the smallest unit of time in LSDj. It's like a
pixel of time; you can't divide time into any smaller components (that
makes it basically the Planck unit of LSDj!). How long or short a tick
actually lasts depends upon the **tempo** setting, so for instance one
tick at 80 BPM is twice as long as one tick at 160 BPM. (Sometimes
individual tick values may vary slightly in the interest of keeping the
tempo as consistent as possible.)

Values for commands such as **K**ill, **D**elay, and **R**etrigger are
specified as a number of ticks. For instance, K01 will kill a note after
1 tick. Wave instrument Speed is also specified in ticks. Additionally,
tables run commands at 1 tick per line by default.

Setting a **groove** allows us to specify how many ticks each line of a
phrase or table should last. The default groove is 6/6, which means the
first line of a phrase lasts for 6 ticks, and the second line also lasts
for 6 ticks (in fact the second '6' in this groove is redundant and can
be removed without changing playback of the song). To apply a groove to
a phrase or table, place a **G** command. The line where the G command
is placed will last the number of ticks in the first line of the
specified groove, and each line afterwards will last the number of ticks
specified in each following line of the groove. For example, a 7/5
groove placed on line 3 of a phrase or table means line 3 will last 7
ticks, line 4 will last 5 ticks, and so on.

To organize grooves within a song, I use a technique that I learned from
[Hypnogram](http://hypnogram.angelfire.com/) which is to set the number
of ticks in grooves according to the number of the groove itself. So for
instance, Groove 00 is the default, but you can't specify 0 ticks so I
leave that at 6/6 (or 6, or whatever I want to be the default). For the
following grooves, Groove 01 is set to 1, Groove 02 is set to 2, and so
on. I generally set these all the way up to Groove 0C or 12, which is
double the default of 6 (though you can feel free to set these up to
Groove 0F if you want). This way when I use a G command in a phrase or
table, it's immediately obvious how many ticks each line lasts for. I
then usually specify custom grooves for Groove 10-1F -- if I look at a G
command and see G12 or G17, I know each line will last a different
number of ticks. So, for instance I may make G10 a 7/5 swung groove

One fun technique is to exploit the unique ability of LSDj to have
different grooves on each channel. In [my cover of the song "Into You"
by Ariana Grande](https://www.youtube.com/watch?v=a1rFQiJ6NvA), I put
the wave channel on a 7/5 groove to swing the kick and the bass, while
the rest of the channels are straight 6/6 groove. It adds a nice tension
to the time feel which sounds kind of in-between swung and straight
time.

In a groove such as 7/5, the first line lasts for seven ticks and the
second line lasts for five ticks. Since there are only 2 values
specified in this groove, each subsequent line alternates between
lasting seven ticks or five ticks. This long-short feel adds 16th-note
swing. Increasing the difference to 8/4 or 9/3 will increase the swing
even more dramatically.

You might also experiment with one channel on 8/4 swing and the other
channels on 7/5 swing for more fluid swing feels. In my song
[Illumin8](https://defensemechanism.bandcamp.com/track/illumin8), I used
a variety of swung grooves in the lead to emphasize different parts of
the melody. Some grooves, like 8/5/7/4, combine both swing feels while
still comprising 24 ticks over four lines, the same as a 6-tick or 7/5
groove. This further increases the push and pull of the melody and
contributes a looser, less rigid, more human-like feel to the lead
instrument. It provides a nice subtle contrast to the simpler 7/5 groove
the rest of the channels are playing.

\
Grooves 10, 11, 13, and 15 are all various swung grooves

I might make G11 a 3/9 groove for note bending (I usually make this
something like 3/9/6/6 in case I need room to add a few more commands
until I can fit a G command to return to a 6-tick groove). This groove
is also handy if you want a wave channel kick to last only three ticks
before a bass note. Here's an example where I used this groove both ways
in BEAT JUiCE:

\* I'll add a note here that LSDj version 6 allows for retriggering the
same groove by using successive G commands to restart the same groove
over from line 1. Previous LSDj versions however will not restart the
groove if the same groove command is used consecutively.

While working in the default 6-tick groove is fairly common, there may
be cases where 6 ticks per line is too slow. Choosing a default groove
of 3 ticks per line provides a higher resolution for faster note and
command triggering. Essentially, playing phrases at a 6-tick groove
allows you to play 16 notes and commands each 6 ticks long for a total
of 96 ticks per phrase. If you play a phrase at a 3-tick groove, you can
play notes and commands twice as fast, but each phrase only lasts 48
ticks, so you'll need two 3-tick phrases to cover the same amount of
time as one 6-tick phrase. Likewise, as phrase resolution increases,
you'll need three 2-tick phrases, or six 1-tick phrases to cover the
same amount of time.

One way to take advantage of higher-resolution phrases is to use a
**H**op command within the phrase to add ticks to its duration. With the
right Hop commands, a phrase that normally lasts 48 ticks can be made to
last 96. Sometimes this results in some complicated looping, but it can
be rewarding to figure it out!

In this example from my song [Near
Miss](https://defensemechanism.bandcamp.com/track/near-miss), I set one
channel to a 3-tick groove and looped the notes I wanted to arpeggiate.
It's common to use tables to create arpeggios, but this method uses
phrases to accomplish the same thing. In phrases, the first digit of the
H command specifies how many times to hop (0 means skip to the next
phrase), and the second digit specifies which line to hop to. So for
instance, H71 hops to Line 1 seven times, then continues playing the
phrase until H5A, which hops to Line A five times before finishing the
phrase.

\
Phrases can be lengthened by using H commands

I hope this lesson has given you some new ideas to use grooves in your
tunes! Next time, we'll take a look at a few more examples of how to use
different grooves in phrases and tables!

Until then, this is [DEFENSE MECHANISM](https://defensemech.com),
signing off!

*Note: traducción al Español por [Pixel Guy encontrado
aquí](un-groove-grooveante-y-trucos-para-los-ticks-parte-uno.html).*
