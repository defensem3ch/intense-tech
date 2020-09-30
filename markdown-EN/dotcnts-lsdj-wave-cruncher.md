Intense Tech with Defense Mech -- DOTCNT's LSDj Wave Cruncher!
==============================================================

\- Posted June 25th, 2019 by [DEFENSE
MECHANISM](https://defensemech.com "Posts by DEFENSE MECHANISM")

<div>

Welcome back to Intense Tech with Defense Mech! In this lesson we're
going to cover how to use [DOTCNT](https://www.facebook.com/dotcnt/)'s
[LSDj Wave Cruncher](https://github.com/iLambda/lsdj-wave-cruncher) to
take samples and generate your own custom wave synth instruments that
you can patch into LSDj save files and songs!

------------------------------------------------------------------------

You may remember the previous [Intense Tech lesson featuring the LSDJ
wavetable import tool](lsdj-wave-cruncher-instrument-library.html) that
[4ntler created](https://github.com/stijnfrishert/liblsdj/releases),
which allows for patching wavetables directly into an LSDj save file or
lsdsng file, such as those from the [LSDj wave synth instrument
library](https://github.com/psgcabal/lsdjsynths). But how do you
generate a wavetable synth from a sample? Today we'll answer that
question as we deep dive into the incredible work of
[DOTCNT](https://www.facebook.com/dotcnt/), the [LSDj wave
cruncher](https://github.com/iLambda/lsdj-wave-cruncher)!

I had the pleasure of meeting Ada, aka
[DOTCNT](https://soundcloud.com/dotcnt) in France last year, and I
immediately praised her for the incredible work she had done to provide
the LSDj community with this tool. In essence, the wave cruncher is a
way to automate the downsampling of a single sample into the format that
works with the LSDj wave synth, essentially turning it into a wavetable
sampler. This allows you to play notes, bend the pitches, arpeggiate
chords, and so on, in ways that you can't when playing samples from kits
in the LSDj ROM. This lesson will be incorporating a lot of previous
knowledge from [past Intense Tech articles](https://defensemech.com), so
feel free to refer back to those if you need to!

The [original tool](https://github.com/iLambda/lsdj-wave-cruncher)
requires you to install node, Python 2, and several libraries for each,
but I've also compiled
[binaries](https://github.com/urbster1/lsdj-wave-cruncher/releases) that
should run in the command-line/terminal environment on Mac, Windows, or
Linux machines without involving any setup. (If you need a refresher on
the command-line/terminal, feel free to check [the article I wrote about
liblsdj as well.](manage-your-lsdj-save-files-with-liblsdj.html))

There are a few more important requirements you will need before you can
start crunching some waves. First, you will need your instrument sample.
Ideally this should be a .wav file that contains just 1 note. It's also
important that the note be *tonal* -- that is, it needs to be a constant
pitch. Think of a musical instrument that plays one note, and you'll
have the idea of the kinds of sounds that will work well with wave
cruncher. Sounds that work especially well are those with lots of
[overtones](lsdj-wave-synth-deep-dive-part-1.html) like bells, FM
e-pianos, steel drums, and so on. Sounds that won't work well are sounds
that are especially noisy, or non-tonal such as snare drums, train
whistles, vibra-slaps, or samples from songs by the [Red Hot Chili
Peppers](https://penzeys.com).

For this example, I'll use an e-piano sample.

\
FM E-Piano sample\

Next, you will need the [wave cruncher
binary](https://github.com/urbster1/lsdj-wave-cruncher/releases).
Download the appropriate version for your platform and place it in the
same folder as any samples you want to crunch, and [open a command line
terminal to that folder](manage-your-lsdj-save-files-with-liblsdj.html).

When you run wave cruncher, you'll provide it with certain parameters or
arguments, like so:

`crunch [SAMPLE.WAV] [NOTE|FREQUENCY|auto] --flag`

"Crunch" is whichever binary you would call on your system, for Windows
we would call "crunch-win.exe" followed by the filename of the
instrument sample we want to use such as "epiano.wav". Following the
sample is either the note such as "A4", the frequency in Hz such as
"440", or simply the word "auto" which will attempt to auto-detect the
frequency of the sample. Auto-detection is very nice when it works, but
it may sometimes fail to detect the pitch of some overly complex
waveforms, and it can take around a minute or so to work (or fail),
which can be time-consuming.

You can feel free to run the cruncher at this point, and if all goes
well, you'll be rewarded with the output of a .snt file which can then
be [patched into a save
file](lsdj-wave-cruncher-instrument-library.html) using the [liblsdj
wavetable patcher](https://github.com/stijnfrishert/liblsdj/releases).

Let's take a look at the output when we run\
`crunch-win.exe epiano.wav auto`

`$ crunch-win.exe epiano.wav autoCrunching data...Auto-detecting           frequency...Frequency detected: 136.47859664570356 HzSaving data as           epiano.snt... Done!Successfully output epiano.snt!`

At this point, we can patch "epiano.snt" to our LSDJ save file. However,
we can also provide additional flags to finetune the wavetables.

The first optional flag affects which wave cycles the cruncher puts into
the wavetable output. By default, it takes the first 16 wave cycles. But
this may not really capture the entirety of the sound of the sample,
especially if the sample is long. So the first flag, "`--linear`", takes
a linear sampling of wave cycles from the entire waveform from beginning
to end. You can think of this as slicing the entire sample evenly into
16 equal slices, and taking 1 wave cycle from each slice.\
The second flag, "`--exp`", mimics a kind of exponential sampling. In
other words, it takes more wave frames from the beginning and fewer wave
frames from the end. This can be useful if you want to capture more of
the nuance of the attack of the sample and less of the decay or release.
It's probably worth playing around with these options as they can
drastically change the sound of the resulting wave instrument.

The next optional flag. "`--normalize`", affects the volume of the
sample. Adding this flag will maximize the volume of the sample before
it is crunched. This is often advised if the sample hasn't been
amplified because normalization generally results in better-sounding
synths. Your samples may already be normalized, in which case this flag
is safe to omit.

The third optional flag is "`--channel=0`" or "`--channel=1`" for stereo
wave files. Since the LSDj wave synth is monophonic, the wave cruncher
has to select either the left or right channel of the sample to crunch.
By default it uses channel 0 (left), but if you prefer, you can set the
flag to channel 1 to crunch the right channel instead.

The fourth optional flag is "`--output=filename`" which allows you to
specify the output of the .snt file. By default, wave cruncher uses the
filename of the wave file sample, but this can get confusing if you want
to test results of different parameters for the same sample. By
specifying "`--output=bell-exp.snt`" for instance, you can specify that
the resulting .snt used the --exp flag, rather than the default or
linear sampling flags. In short, it is just designed as an option to
help keep things organized.

Lastly, there is an optional "`--analyze`" flag which is simply designed
to analyze frequency. It will not output a .snt file. Think of this as a
test mode -- you can run the cruncher with --analyze to make sure that
the pitch auto-detection doesn't fail. This can be helpful when batch
processing samples just to ensure that the process will run smoothly
without hiccups -- if pitch auto-detection fails, the sample won't be
crunched. Auto-detection can also add about 30-60 extra seconds to
process the wave file. Since the `--analyze` flag outputs the frequency
that it detects, frequency can then be provided in subsequent crunches
to speed up the process.

Let's run the cruncher a couple more times with our epiano sample and
test the results. Since it took about 45 seconds to detect the
frequency, I'll provide the value instead of using 'auto' to speed
things up, and see what sounds result when using the different flags.

`$ crunch-win.exe epiano.wav 136.47859664570356 --normalize --linear           --output=epiano-lin.sntCrunching data...Samples: 311847Sample rate:           44100Cycles: 965Linear interpolationTaking frame every 60 cyclesSaving           data as epiano-lin.snt...Done!Successfully output epiano-lin.snt!`\
\
`$ crunch-win.exe epiano.wav 136.47859664570356 --normalize --exp           --output=epiano-exp.sntCrunching data...Samples: 311847Sample rate:           44100Cycles: 965Exponential interpolationSaving data as           epiano-exp.snt...Done!Successfully output epiano-exp.snt!         `

Once you run the cruncher, you can then [follow the instructions
here](lsdj-wave-cruncher-instrument-library.html) to patch your .snt
files into your save files and lsdsngs! Keep in mind that you will have
to set the Play, Length, and Speed parameters in the wave instrument
appropriately. Depending on the tempo, try it with Play Once, Length 3,
Speed 3, and adjust from there. If the result sounds good, please
consider [contributing them to the LSDj synth instrument
library](https://github.com/psgcabal/lsdjsynths)! Let's check the
results of our instruments below. I've patched each instrument into
Instruments 1, 2, and 3, and Synths 1, 2, and 3 respectively. Chains and
Phrases 01, 02, and 03 will play these respective sounds.

\
***Each Wave instrument may need different parameters***\

I hope that this article gives you some insight into the wave cruncher
and encourages you to try crunching some of your own wave samples!

Please do yourself a favor and check out more of [DOTCNT
here](http://facebook.com/dotcnt/) and
[here](https://soundcloud.com/dotcnt)!

As always, if you have any questions feel free to contact me at
<defmech@chiptuneswin.com>. Until next time, this is [DEFENSE
MECHANISM](https://defensemech.com), signing off!

*Note: traducción al Español por [Pixel Guy encontrado
aquí](el-lsdj-wave-cruncher-de-dotcnt.html).*

</div>
