Intense Tech with Defense Mech --- Manage your LSDj save files with libLSDj!
============================================================================

\- Posted February 19th, 2019 by [DEFENSE
MECHANISM](https://defensemech.com)

Hello and welcome back to Intense Tech with Defense Mech! In this
installment, we're going to get down and dirty with the command line to
introduce you to a true power tool for handling your LSDj save files and
songs! By the end of this lesson you will know how to organize a set of
folders for each song and create a master list of all the songs on your
save files. If this sounds like something you need in your life, keep
reading!

------------------------------------------------------------------------

If you're an LSDj user, chances are that at some point you've had to
deal with backing up your save files, whether from a hardware flash
cartridge or with an emulator such as BGB. Maybe you're ready to play
your first live set, and you want to put your best songs in order in a
brand new save. Although there is the well-known
[LSDManager](https://github.com/jkotlinski/lsdmanager) for managing the
songs in these save files, its UI makes it tedious to manually import
and export every song. Furthering that aggravation, the UI requires the
user to load each save file to review which songs it contains. Since
that's a task of pure tedium, it's likely that you'll forget what's in
your save files by the next time you need to put a new save file
together.

![***How am I supposed to know what's going on here?***](image3.png)

Luckily, to help save us from tedium, our friend
[4ntler](http://soundcloud.com/4ntler) has been hard at work creating
some tools using a library he created called
[libLSDJ](https://github.com/stijnfrishert/liblsdj)! The [current
release](https://github.com/stijnfrishert/liblsdj/releases) includes 2
tools we're going to take a look at today: **lsdsng-export** and
**lsdsng-import**. In order to get started, first you'll want to
download the zip file of the current release for your platform (Mac or
Windows).\*

#### Note: [Lemondrop](https://twitter.com/lemondropbass) has kindly made a nifty save management tool using libLSDJ for both Windows and Mac! Check it out here: <https://github.com/InspectorConstructor/lsdjSongManager/releases/>

For today's lesson, I've created a folder called 'LSDJ' and extracted
the lsdsng\_tools.zip into that folder. I've also created a subfolder
inside 'LSDJ' called 'saves' inside which I placed the save files I want
to organize from my website at <https://defensemech.com/songs>. [Grab a
copy for yourself](https://penzeys.com) -- or use your own save files to
follow right along!

To begin, we need to open the command-line or Terminal window. On
Windows, with a window open to the LSDJ folder, you can open a
command-line window by pressing Shift+Right-Click and choosing "Open
command window here". (Note: Windows 10 no longer allows this, so you
will need to run 'cmd' using Windows+R or clicking the Start menu,
typing 'cmd' and press Enter, then type 'cd' followed by a space and
dragging the LSDJ folder and pressing Enter to set it to the current
folder.) On Mac, you can open Terminal from Spotlight, and then type
'cd' followed by a space, then click and drag the LSDJ folder onto the
Terminal and press Return to set it to the current folder.

To view the songs in a save file, you can type: `lsdsng-export -p` and
the save file you want to view. This will "**p**rint" the list of songs
into our command-line or Terminal window. In our case, because
lsdsng-export also recognizes folders, we can view the contents of every
save file at once by typing: `lsdsng-export -p saves` and violà! A list
appears so we can instantly read what's in any save file. When you see
'WM' underneath the name of the save file, that indicates the song that
is preloaded into the working memory of that save. This can be turned
into a "master list" of the songs in every save file and saved as a text
file. This is simple to do on the command line by simply typing:
`lsdsng-export -p saves > songlist.txt` which creates a text file called
"songlist.txt" that includes the entire output of every save file in the
'saves' folder and the songs within them. This can be extremely handy,
although it is limited to one folder only. If you have another folder
containing save files within the 'saves' folder, that subfolder will be
ignored

To view one save by itself, like SUNBURST.sav, we can type:
`lsdsng-export -p saves/SUNBURST.sav`. (We use a slash to tell
lsdsng-export to look inside the 'saves' folder for SUNBURST.sav.) The
output looks like this:

``` {.wp-block-code}
SUNBURST.sav
#   Name     Ver    Fmt
WM  ENAMORED *          7
0   ENAMORED 6D         7
1   ILLUMIN8 78         7
2   NEARMISS 7D         7
3   FRESH    92         7
4   BLONGING 52         7
```

Without the **-p** argument, typing `lsdsng-export saves/SUNBURST.sav`
will extract all lsdsng files into our 'LSDJ' folder. On Windows, you
can also drag a save file onto lsdsng-export without opening the command
line at all! You can even extract EVERY lsdsng in the folder 'saves'
just by typing: `lsdsng-export saves` If you want to organize every song
into its own **f**older, it's also possible to do this by specifying
with the **-f** argument: `lsdsng-export -f saves` This will place each
lsdsng into a folder named after it. When extracting a lot of save
files, this can be very helpful if you have multiple backups of songs.
Each folder will contain every version of that song from all of your
save files!

Let's say we want to extract the lsdsng files from SUNBURST.sav into a
new folder called 'songs'. We can tell lsdsng-export to do this by
typing: `lsdsng-export saves/SUNBURST.sav -o Sunburst` which will
**o**utput every lsdsng file into a folder called 'Sunburst'. If there
is no 'Sunburst' folder yet, it will be created!

If I only wanted to extract the lsdsng for NEARMISS, I could specify by
**n**ame or by **i**ndex. (Index refers to the number of the song listed
underneath \#.) To extract it by name, I would type:
`lsdsng-export -n NEARMISS saves/SUNBURST.sav` To extract by index I
would type: `lsdsng-export -i 0 saves/SUNBURST.sav` These options can be
used more than once to extract multiple songs like:
`lsdsng-export -n NEARMISS -n ILLUMIN8 saves/SUNBURST.sav` and they can
also be combined together, like:
`lsdsng-export -n NEARMISS -i 1 saves/SUNBURST.sav` (It's worth keeping
in mind that the first song in the index is 0, not 1.) These can be
combined with the output folder:
`lsdsng-export -n NEARMISS -i 1 saves/SUNBURST.sav -o songs`

It's also possible to extract the lsdsng for the song in working memory.
This can be handy if you forgot to save your song in LSDj but the
changes you've been making are still loaded and intact. You can do this
by typing: `lsdsng-export -w saves/SUNBURST.sav`

So far so good? OK! Once we've extracted our songs, it's time to compile
them into a save file using lsdsng-import. Again, there are a few ways
to do this.

Let's say we have one or more lsdsng files that we want to turn into a
save file. On Windows, without opening a command line, you can drag one
or all of the lsdsng's together onto lsdsng-import, which will
automatically create a save file called 'out.sav'.

To do this on the command line, type: `lsdsng-import` followed by any
number of lsdsng files which will be combined into 'out.sav' by default.
You can specify the name of the **o**utput save file by using the -o
argument: `lsdsng-import -o mysave.sav song1.lsdsng song2.lsdsng` (and
so on). If you want to add another song to 'mysave.sav' later, you can
use the -s argument: `lsdsng-import song3.lsdsng -s mysave.sav` which
will add song3.lsdsng onto 'mysave.sav'.

To combine all the songs in the 'songs' folder into one save file, you
can type: `lsdsng-import songs` which create a save file called
'songs.sav'. This method will place them in the save file in order of
the file names, so before doing this, you may need to rename the save
files so that they appear in the proper order when they are sorted by
name.

If at any point you forget how to run either lsdsng-export or
lsdsng-import, typing either `lsdsng-export`or `lsdsng-import` with no
other arguments will display help text that describes the options.

\*Footnote for Linux users: Not to exclude you, but compiling from
source and using the command line are hopefully familiar enough to you
that you may not need this tutorial! 😄

I hope this article has helped you, and thanks again to 4ntler for all
the great work on these tools and libLSDj! Feel free to contact me with
any questions at <defensem3ch@gmail.com>. Until next time, when we'll
take another look at libLSDj and the wave channel, this is [DEFENSE
MECHANISM](https://defensemech.com), signing off!

*Note: traducción al Español por [Pixel Guy encontrado
aquí](organiza-tus-archivos-de-guardado-con-liblsdj.html).*
