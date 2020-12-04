**Intense Tech with Defense Mech: Interview with LSDj Developer Johan Kotlinski!**
- Posted February 20th, 2020 by [DEFENSE
MECHANISM](https://defensemech.com) *Note: traducción al Español [por Pixel Guy encontrado aquí](../es/13-entrevista-con-el-desarrollador-del-lsdj-johan-kotlinski.md.html).*

Welcome back to Intense Tech! This time I'm really excited to share with
you an interview with Johan Kotlinski, the developer of LSDj! Let's dive
right in!

------------------------------------------------------------------------

<div class="interview">
**DEFENSE MECH: Hi Johan! Thanks for agreeing to do this interview with
me for Intense Tech!**
</div>

Johan Kotlinski: Hi! Thank you.

<div class="interview">
**DM: You know, the Game Boy turned 30 years old in 2019, and it still
remains a memorable piece of hardware to a lot of us gamers and
musicians who played it in our youth.**

**Why do you think the Game Boy was the platform that inspired you to
write a program for music composition?**
</div>

JK: I think it's mostly timing and luck. I had been interested in making my
own music editor for some time, and so it just happened that Game Boy
Color appeared at the right time as a fun and interesting platform. You
see, in 2000 it was not that "retro" but rather the most popular
handheld, even if the architecture was dated already then.

<div class="interview">
**DM: Did you have any prior expertise in developing music software, or
software for game consoles?**
</div>

JK: Not really! I had made a few toy music programs, but Little Sound Dj was
probably the first thing I worked on that went over a thousand lines
\[of code\]. Also, I had never written assembly code before, so there
was a lot of things to learn. This is not to say I was an absolute
beginner. I had been programming since I was twelve or so. I just did
not have any experience in writing a real program that people actually
use.

<div class="interview">
**DM: Game Boy music has really become popular as a platform among chiptune
artists -- it's almost always the case that if a chiptune show is
happening, there is going to be at least one artist, if not several
more, performing on a Game Boy with LSDj.** **In some ways, it's hard to
imagine what the chiptune scene would be today without it.**

**What was your experience with chipmusic before LSDj?**
</div>

JK: Like many others in Sweden, I grew up with Commodore 64 and Amiga and so
got accustomed to these sounds early on. Early 90s, I learned Protracker
and shared .mod files on bulletin board systems, and made friends over
FidoNet who shared my taste in music; mostly the techno/house/IDM stuff
that were popular back then.

At that time, the term "chip music" was mostly synonymous with what is
today known as keygen music, .mod files with tiny looped samples. It was
considered neat and clever, but not something anyone would do
exclusively. Anyway, I listened and liked. There was also inspiring
Commodore 64 SID music, and games like "Poing" by Paul van der Valk.

In mid 90s, I started to use a new synthetic music program for Amiga
named Musicline Editor. I don't think it ever got popular, since at this
time people were switching to PC and Playstation. I liked it a lot
though. Compared to Protracker, it was possible to create new sounds
rather than just using samples. Also, the vertical workflow made it
easier for me to actually finish songs. I made a lot of music, had fun
and mail-swapped tapes with the few people I found who were at all
interested in listening.

Over time, I grew more passionate about listening to and making music. I
got a PC and synthesizers and started using Cubase. In the end, I found
the same problem as with Protracker: I mostly made loops and had
difficulties actually finishing anything. So I decided just to continue
using Musicline, making a serious effort in making the best music I
could and see what might happen. Even if hardly anyone would consider
this 8-bit repetitive noise as "real music".

Inspired by the local indie/DIY scene, I set up my own CD-R label
"[Bleep Street](https://bleepstreet.bandcamp.com/)" in 1998, where I
published music made by myself and friends with similar ideas. I sold
maybe 50 copies of each record to friends, strangers, & small record
stores. Fun!

In 2000, I printed the 7″ vinyl "[Papaya
EP](https://bleepstreet.bandcamp.com/album/papaya-ep)" with Commodore 64
music made by my friend [Goto80](https://www.goto80.com/). Surprisingly
enough, people liked it enough to sell a thousand copies. I think it
inspired us both to put more effort into what we were doing.

It was around this time I started to make some kind of music program for
the Game Boy Color, which turned out to be surprisingly fun. I named it
[Little Sound Dj](https://www.littlesounddj.com), sold cartridges over
the internet and to a local record store. I found more like-minded
people in Stockholm and on the Internet. From there on, thanks to
[micromusic.net](https://micromusic.net) and other early Internet
communities, things kind of exploded. Suddenly, lots of people who were
thinking that this music deserved to be treated as "real music" realized
they were not alone, learned how to network and organize shows. It got
recognized as a movement of sorts. And from there, it just continued.

If anyone is interested, some of my old music is still online. Search
for "rolemodel" on [micromusic.net](https://micromusic.net), or
[8bitpeoples
8BP047](http://www.8bitpeoples.com/products/520230-role-model-a-new-fragrance).

<div class="interview">
**DM: Ableton Live was released in October 2001, and the LSDj changelog
shows its own "Live mode" was implemented in January 2001 -- looks like
maybe they owe you some credit? I'm not familiar with the entire history
of trackers, but it seems like the idea to make the tracker more than
simply a tool for linear composition, to go beyond that and to offer
different possibilities during live performance, is unique to LSDj.**

**Do you remember what sparked the idea to want to be able to cue
different song sections on the fly?**
</div>

JK: It is very flattering to think otherwise, but for sure Live Mode is from
Ableton Live and not the other way around. If I remember right, Tobi-Wan
of Puss was a beta tester and showed me how it worked. Incidentally, I
lived in Berlin October 2001, just a few blocks away from Ableton
offices. Maybe I even went to the 1.0 party. My memory is a bit foggy,
so I can't tell for sure.

<div class="interview">
**DM: Later this year, it will be LSDj's 20th birthday! That's pretty neat
since not many trackers or other software for legacy hardware are being
actively developed over so many years.**

**What has inspired you to keep developing LSDj?**
</div>

JK: Certainly that people keep on using and caring about it! Otherwise, I do
not think I would put any effort into it at all. I think now is really a
good time. Good music is being made and I get nice ideas and help from
the community. That makes it fun. I like staying somewhat connected with
the chip music scene that I love so much.

<div class="interview">
**DM: When you think about LSDj's development, what are you most proud of?**
</div>

JK: Overall I'm not too proud. Most of the time I am very lazy, and there
has been many bad bugs and terrible design decisions over the years. I
am just grateful that so many kept the patience to this point, including
myself.

There are some changes that I thought were maybe nice or at least
interesting:

-   **Optimized dual kit sample mixing in v1.4.0.**

I was happy for days when I managed to make this fast enough to work on
DMG. This code is extremely clever and I find it very hard to understand
today. In part because the comments are completely outdated and
misleading.

-   **File screen in v3.0.0.**

It took longer than it should to figure out that simple RLE compression
would go a long way in fitting many songs on one cartridge. Often, the
difficulty is just to start thinking in the right direction and not
dismissing problems that are not immediately obvious how to solve. After
this change, I think LSDj started to become as popular as Nanoloop.

-   **Prelisten in v3.9.5.**

It's a really simple thing, to hear the notes as you enter them, but I
think it goes a long way in making note entry more efficient,
interactive and fun, especially for those who do not have musical
backgrounds. For some, it felt like cheating.

-   **New pitch engine in v5.1.0.**

This one was actually a total disaster. It took way too long until it
was on par with what was there before in terms of kick crafting. I am
happy it is finally paying off though. The vibrato in latest versions is
spot on and things harmonize so much better than they used to. It is a
bit unfortunate that I had to break everyone's songs, but in Sweden
there is this saying, "There are no shortcuts to the perfect sound"...

<div class="interview">
**DM: When I think about LSDj, my mind cannot really comprehend how it would
have been possible to pack it full of so many features, like the ability
to sequence channels at independent grooves, the wavetable synthesizer,
and the dual-channel sample playback. It seems like every month that
goes by, someone has discovered a new technique or invented a new
sound.**
**What do you think is next for the sound of the Game Boy and for
LSDj?**
</div>

JK: I think the near future is pretty clear. At some point, what went in
over the last months will become the new stable v8, meaning e.g.
accurate vibrato, de-clicked WAV playback, slowed-down C command,
probability sequencing, higher max tempo, wave finetune, optimized
playback, high-speed retrig. Also, I just started working on multi-stage
envelope for pulse and noise channels. *\[Editor's note: ADSR envelopes
are now implemented in the latest version, v8.1.8 at the time of this
writing!\]*

Next, I am not sure. Generally, I think the wave channel has lots of
untapped potential now that it is virtually clickfree, but not sure
exactly what to do next. There is plenty of good and important ideas on
the [LSDJ Wishlist](https://littlesounddj.fandom.com/wiki/LSDj_Wishlist)
too. It totally depends on what people want to see. I'll ask [on
Facebook](https://www.facebook.com/groups/LittleSoundDJ/) at some point;
for those who don't have it, I appreciate it if you send your
suggestions [by e-mail](mailto:info@littlesounddj.com) or [add them to
the Wiki](https://littlesounddj.fandom.com/wiki/LSDj_Wishlist). This
input really helps when I decide what to do next.

<div class="interview">
**DM: Thanks again!**
</div>

JK: Thank you!

