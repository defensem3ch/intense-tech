**Intense Tech with Defense Mech --- LSDj Wave Cruncher Instrument Library!**
- Posted March 28th, 2019 by [DEFENSE
MECHANISM](https://defensemech.com) *Note: traducción al Español por [Pixel Guy encontrado aquí](../es/biblioteca-de-instrumentos-lsdj-wave-cruncher.md.html).*

Hello again and welcome to an extremely exciting edition of Intense
Tech! I'm thrilled to share the results of the past few months with you
because I believe that an entire new world of sounds is now at your
disposal. Come with me as we return to the command line using 4ntler's
lsdj-wavetable-import tool from libLSDJ!

You may recall from [our previous
installment](04-manage-your-lsdj-save-files-with-liblsdj.md.html),
which introduced us to the command line and libLSDJ, and the first two
articles diving deep into the LSDj Wave Synth. This time we're going to
combine these tools to allow you to patch custom waveform data directly
into an .lsdsng or .sav file. Over the past few weeks I've begun to
build an instrument library to make many sounds available for anyone to
use. Before I get ahead of myself, let me explain from the beginning how
this works.

A few years ago, I happened upon a tool by [DOTCNT](https://soundcloud.com/dotcnt) called
"[lsdj-wave-cruncher](https://github.com/iLambda/lsdj-wave-cruncher)." The idea was to take a sample 
of an instrument, such as a steel drum, and reduce it to a series of 4-bit waveforms
compatible with the Game Boy wave channel synth. It's already possible
to sample instruments by using LSDPatcher to patch custom samples
directly into the LSDj ROM, but with limitations inherent to the LSDj
sample kit instruments. Playing notes at different pitches requires
patching one sample per pitch. Some sample manipulations can be done but
they are not always suitable for tonal monophonic instruments.

The [revelation](https://www.penzeys.com) of the wave cruncher is that
it turns the wave synth itself into a rudimentary sampler! Instead of
generating waveforms using the built-in synth, wavetables can be created
from an instrument sample to allow it to be patched into the 16 wave
frames of a wave channel instrument. Let's take a look the following
example of an electric piano:

![FM E-Piano sample](../media/epiano.mp3)

When this sample is put through the wave cruncher, the wave cycles will
be reduced to fit each cycle within 1 of the 16 wave instrument
wavetables. From there, set the Wave Instrument to Play: Once, and
adjust Length and Speed parameters to your liking. Here's a little riff
with Length 3, Speed 3:

![E-Piano reduced to 4-bit wave instrument in LSDj](../media/epiano2.mp3)

The bad news is that tweaking the sample, the wave cruncher settings,
and the wave synth settings can result in a lot of work before getting a
satisfying result. The good news is that I've already done a bit of this
work for you! I've created a repository on Github called
[lsdsynths](https://github.com/psgcabal/lsdjsynths) that contains the
synth wavetables as .snt files. Using the libLSDj lsdj-wavetable-import
tool will allow you to utilize these sounds in your projects! Unlike kit
samples which are patched into the ROM, the wavetable synth instruments
are patched into the save file instead, which is handy when
collaborating or sharing save files with other LSDj users.

Now let's take a minute to go over how to utilize the
lsdj-wavetable-import tool. If you haven't already, grab [the liblsdj
release](https://github.com/stijnfrishert/liblsdj/releases) for your
platform.

Place lsdj-wavetable-import and the synth (.snt file) you want to patch,
along with your LSDJ save file or .lsdsng file in the same folder. Open
a command-line or Terminal window to this location. To patch the .snt
file, the commands are as follows:

`lsdj-wavetable-import savefile.sav synth.snt 0`

This will patch
"synth.snt" to synth 0 of "savefile.sav". When patching a save file,
only the song loaded in working memory is patched, so be sure the song
you want to patch is loaded in the save. Otherwise, you can substitute
any .lsdsng file instead of "savefile.sav." Pretty simple!

I hope you find these sounds interesting and useful! Feel free to share
the results of trying this out for yourself.

