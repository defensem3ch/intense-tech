**Intense Tech with Defense Mech – The Joys of Noise!**
-Posted November 5, 2020 by [DEFENSE MECHANISM](https://defensemech.com) *Note: [traducción al Español por Pixel Guy encontrado aquí](../es/17-las-alegrias-del-ruido.md.html).*

Hello and welcome to another edition of Intense Tech! This time, we'll be delving into the 
intricacies of the noise channel and discovering what's possible, aiming to grow our arsenal of 
sound possibilities to the max! We'll explain how the noise channel generates sound and exploit a 
few principles to get some unexpected textures. Let's dig in!

--------------------------------------------------------------------
Putting the "Gritty" in Nitty-Gritty
--------------------------------------------------------------------
As you've likely come to expect from this blog, it's time for another deep dive. Feel free to skip 
this section if you're not interested in the inner workings of the noise channel, but otherwise, 
keep reading! It's also absolutely worth mentioning [this excellent video tutorial by Boy Meets 
Robot](https://www.youtube.com/watch?v=wD7omqjHXmI) which breaks down the noise channel in a similar 
way. You can always return to this section as a reference if needed!

The noise channel works according to a concept known as a Linear Feedback Shift Register - for our 
purposes, it's sufficient to know that it's a fairly quick and easy way to generate pseudo-random 
noise, and that it generates a series of 1-bit pulse waves each with random width. The noise is 
generated according to a clock which is first divided according to... a divisor – except for the 
highest digit, which actually doubles the frequency. The output is then divided by a power of two, 
which essentially controls the octave of the noise. This is abstracted in LSDj to allow us to 
control the octave with the first digit of the noise shape, and the second digit controls the 
frequency divisor.

<center><big>**Noise Shape Chart**</big></center>
First Digit | Octave | Second Digit | Frequency Divisor Value
------------|--------|--------------|--------------
**F** | Highest octave | **F** | Multiplied by 2
**E** | One octave lower | **E** | Unchanged (multipled by 1)
**D** | Two octaves lower | **D** | Divided by 2
**C** | Three octaves lower | **C** | Divided by 3
**B** | Four octaves lower | **B** | Divided by 4
**A** | Five octaves lower | **A** | Divided by 5
**9** | Six octaves lower | **9** | Divided by 6
**8** | Seven octaves lower | **8** | Divided by 7
**7** | Eight octaves lower | **7** | Multiplied by 2
**6** | Nine octaves lower | **6** | Unchanged (multipled by 1)
**5** | Ten octaves lower | **5** | Divided by 2
**4** | Eleven octaves lower | **4** | Divided by 3
**3** | Twelve octaves lower | **3** | Divided by 4
**2** | Thirteen octaves lower | **2** | Divided by 5
**1** | <span style="color:gray;">*Not used - NO SOUND*</span> | **1** | Divided by 6
**0** | <span style="color:gray;">*Not used - NO SOUND*</span> | **0** | Divided by 7
<div class="fig">*Note: In versions prior to 8.6.0, octave 5 of the note in the phrase corresponds 
to the first digit of the noise instrument shape (octave 6 in versions prior to 5.1.6). Changing the 
octave up or down changes the first digit of the noise shape up or down (if the highest or lowest 
digit is reached, moving the octave up or down respectively has no further effect). The pitch of the 
note does not affect noise shape, only the octave.*</div>

You may have noticed that the divisor value for the second digit is the same for digits F and 7, E 
and 6, etc. This is because digits 0-7 set the noise channel to **short-loop** mode, and digits 8-F 
set it to **long-loop** mode. Short-loop mode means that the noise waveform is half as long, and the 
result is that this produces more tonal, ringing, metallic tones. Long-loop mode sets the noise 
waveform to the full length, resulting in a sound that is less pitched and more akin to white noise.  
We can illustrate this by sweeping through the noise shapes of `CF` to `C0`:

![Playing shapes `CF` through `C0`](../media/noise-sweep.mp4)

In contrast to the wave synth where sounds are constructed by multiplying the base frequency by 
whole numbers to generate the harmonic series, the noise channel notes generate the *negative* 
harmonic series, which results from dividing the frequency by whole numbers. So, since the base note 
is near the frequency of a C, we can see what notes result when that frequency is divided by each 
number:

![The available pitches in short-loop mode are not exact, but they sound the closest to C, F, A♭, and D.](../media/negative-harmonic-series.png)

One excellent example of using short-loop mode to generate tonal pitches is this demo by 
[they/them](https://theythemmusic.bandcamp.com/), which only uses the noise channel:
<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" 
src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/265499387&color=%2322c8ff&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true" 
style="height: 166px;"></iframe>

How It All <span class="defense">S</span>hapes Up
--------------------
Noise shape can be controlled by the S command, and this is useful for having finer control over 
noise shape. While LSDj versions 8.6.0 and newer allow you to program noise shape directly in 
phrases instead of notes, it's still important to understand how the S command works.

The S command adds the value of the command to the noise shape *per-digit*. So unlike other commands 
where you might be expected to think that applying an S command with value `01` to shape `4F` would 
result in shape `50`, that's not the case since each digit is affected separately.  Applying `S01` 
to shape `4F` results in shape `40`. Likewise, applying `SFF` to shape `4F` results in shape `3E`.

Contrast this with the noise transpose in both phrase and table, where both  digits *ARE* affected. 
Here, applying a TSP value of `01` to shape `4F` DOES result in shape `50`, and likewise TSP `FF` 
results in shape `4E`.

Another clear difference in tables between S commands and transpose is that the S command is 
*additive*, meaning that successive S commands keep adding to the previous noise shape. The 
transpose column applies the transpose only while the table runs the respective line, and the noise 
shape reverts to the previous shape value when no transpose is active.

<span class="defense">P</span>utting More <span class="mechanism">C</span>ommands Into Play
----------------------------------
Now that we've covered how the S command works, we can extrapolate its functionality to two more 
commands: P and C. Each of these commands adds its respective value to the noise shape. The 
difference is that the C command alternates between the base shape and the added shape on each tick, 
while the P command adds continously. So if the base shape is `FF`, setting `C01` will alternate 
between `FF` and `F0` on each tick, while setting `P01` will cycle from `FF` to `F0`, then `F1`, 
`F2`, and so on. If changing shape on each tick is too fast, adjusting the CMD/RATE for the noise 
instrument to a higher value will make the rate slower.

Because these commands don't take into account the frequencies that are generated and they freely 
switch between long-loop and short-loop modes, it's still sometimes necessary to make custom tables 
with S commands when you want to sweep through the shapes smoothly. Here are a couple examples of 
how to do that using tables to sweep smoothly down and up:

![Smoothly sweeping through the noise shapes](../media/custom-sweep.mp4)

Working With The Quirks
-----------------------
One of the special quirks of the Game Boy's noise channel is that *sometimes it goes silent for no 
reason.* That's right – there's a chance of 1 out of 256, or 0.4%, that the noise channel will go 
silent if it switches from long-loop mode to short-loop mode; in other words, if a noise shape with 
the second digit of 8-F is changed to end with 0-7, the noise channel might get muted. In order to 
prevent this from happening, you can change the noise instrument S MODE (or S CMD in previous 
versions) from FREE to STABLE. This will allow the instrument's divisor value to change without 
changing the loop mode, meaning that the loop mode will solely be determined by the base noise shape 
of the note that is provided.

Getting Into A Crash
--------------------
One cool trick that I learned from [this EXPLORING CHIP TUNES video 
tutorial](https://youtu.be/4jPUOpUUYd0?t=948) was to use the Z command with noise shape to make 
random noise crash cymbals to add some variation when playing the song live. Recall from [Don't 
Sleep on Z](https://defensemech.com/intense-tech/dont-sleep-on-z-feat-hypnogram.html) that Z 
randomizes each digit independently, so this allows us to control the variations to be within a 
certain loop mode in a certain octave, for example. But don't be afraid to go all out!

![](../media/noise-crash.mp4)

<div class="fig">In this example, Z can add 1 to the first digit 4 times, meaning the highest digit 
possible will be F. If it were to exceed F then it would wrap around to 0, which is silent. In order 
to avoid that, I've set some of the Z commands to have a first digit of 0. However, since I want the 
divisor to be completely random every time, I've set the second digits to F. That way, it's possible 
for the divisor to be any value from 0 through F on each line.</div>

Kicking Off With A Bang
-----------------------
One of the most useful aspects of the noise channel is its capablity to generate low bass 
frequencies, even if they're hard to tame. This is useful for obvious reasons: sometimes you just 
need a boost in the low end that is hard to get out of pulse kicks, or maybe the other 3 channels 
are busy, but you still need a kick! So after thinking about how the noise channel works, I started 
rethinking how I make noise kicks. As always, this is just one example of what a noise kick can look 
like. After explaining my methods here, I hope you're able to apply them in your own way too!

![](../media/noise-kick.mp4)

<div class="fig">This example starts by slowing down the table so you can see and hear how the kick 
sounds as the table advances on each line. I'm starting with a base noise shape of `95`, but the 
first step of the table has a transpose of `10`, so the sound you hear on the first tick is actually 
shape `A5`. This way of adjusting the pitch of the first tick means that I can move the TSP up or 
down to change the attack without changing the sound of the rest of the kick. After that, I am 
sweeping downwards to `93`, `91`, then `90`.  I don't want the second digit to wrap back around to 
F, so then I go further downwards from the first digit to `80`, then `70`, and end on `60`. It's 
worth noting that the noise instrument is set to STABLE mode so that it stays in short-loop mode 
only, ensuring that it won't mute accidentally. Last but not least, noise kicks sound great when 
they are LOUD!
</div>

Lengthening The Possibilities
-----------------------------
Believe it or not, we've still only cracked the surface of the sounds we can get out of the noise 
channel. By rapidly switching the noise channel on and off, it's possible to generate a pulse wave. 
The easiest way to do that is using the R command. (Quick note about the R command: depending on the 
version of LSDj, `R00` may retrig only once or it may retrig every tick. In version 8.9.3, `R01` retrigs 
every tick.) To control the loudness of the sound, we can either set a shorter LENGTH or a shorter 
ADSR/Envelope. The pitch of the resulting pulse wave is determined by both the rate of the R 
command, the tempo of the song (which controls the length of each tick), and the noise shape itself.  
You can also use `R80` through `R8F`, the super-fast retrig, which is not affected by song tempo or 
LENGTH.  Here's a video that demonstrates a couple of examples: 

![](../media/noise-retrig.mp4)

Putting it all together
-----------------------
One of the most epic tracks I've heard this year has come from none other than 
[.exe](https://dotexe.space) called NOIZE JAMS, which amazingly uses only the noise channel.  
<iframe width="100%" height="166" style="height: 166px;" scrolling="no" frameborder="no" 
allow="autoplay" 
src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/753000481&color=%2322c8ff&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>

Thankfully, he's agreed to allow me to share the save file here! It's confirmed to work with LSDj 
v8.5.1 stable.

<center><span style="font-size: 200%;"> --> [**NOIZE JAMS 
SAV**](https://defensemech.com/intense-tech/dotexe-NOIZE_JAMS.sav) <-- </span></center>

Please also support .exe by [buying his album on 
Bandcamp!](https://dotexechiptune.bandcamp.com/album/jams-exe)

<center>
<iframe style="border: 0; width: 350px; height: 470px;" 
src="https://bandcamp.com/EmbeddedPlayer/album=3256814611/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/transparent=true/" 
seamless><a href="https://dotexechiptune.bandcamp.com/album/jams-exe">JAMS.exe by .exe</a></iframe>
</center>
