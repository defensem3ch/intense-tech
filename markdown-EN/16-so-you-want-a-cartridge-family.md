Intense Tech with Defense Mech -- So You Want a Cartridge Family?
=================================================================

\- Posted May 21st, 2020 by [DEFENSE MECHANISM](https://defensemech.com)

Welcome back to Intense Tech with Defense Mech! Although I usually
discuss techniques within LSDj, I get a lot of questions about what kind
of cartridges I recommend. The Game Boy flash cartridge market tends to
change every few years, so I hope to add more information as it becomes
relevant. Today, I'm going to cover 3 different kinds of flash
cartridges and how to use them if you want to write music in LSDj on
Game Boy hardware (my preferred working method). Let's dive in!

------------------------------------------------------------------------

SD-card-based flash cartridges
------------------------------

For SD-card-based flash cartridges, the LSDj rom and save are stored on
a microSD card that loads into the flash cartridge itself. Examples of
these cartridges, which have gained popularity over the last several
years, are the Krikzz Everdrive GB (X3/X5/X7), the BennVenn El Cheapo
SD, and the EZ Flash Junior.

While the [Everdrive GB
X5](https://krikzz.com/store/home/47-everdrive-gb.html) is a perfectly
reasonable and functional choice of cartridge as it supports the
necessary 128kb SRAM that is required for LSDj to function, they are
often cost-prohibitive, costing around \$90 or more. A much cheaper
alternative is the EZ Flash Jr, which can be purchased for around [\$60
on
Amazon](https://www.amazon.com/EZ-Flash-EZ-FlashJr-Original-Everdrive/dp/B08379XZWY)
as well as Game Boy modding shops (*Note: prices may have risen since
this article's publication depending on availability so it may be
worthwhile to check different vendor websites*).

If you plan to use an EZ Flash Jr, you will need to download the
firmware from the website [ezflash.cn](https://ezflash.cn) and load the
"[ezgb.dat](https://penzeys.com)" file onto the root folder of the
microSD card. You can also copy the LSDj rom onto the root of the
microSD card. When you boot the cartridge up, a menu appears with the
options to select the LSDj rom. After loading the save file into memory,
LSDj will start (save files go into the "SAVER" folder on the microSD
card).

When you're done working in LSDj and turn the Game Boy off, a battery
keeps the save in memory. The next time you turn on the cartridge, the
menu will prompt you to back up your save onto the microSD card. If you
say no, all your work will be lost. You can load as many LSDj roms and
saves onto the cartridge as you can fit onto the microSD card. As long
as your save file shares the same filename as the corresponding LSDj
rom, it will be loaded with the respective rom of your choosing. If
there is no save file found, a new one will be created.

The EZ Flash Jr. also has a soft reset button that you can use to take
you back to the main menu, removing the need to turn the Game Boy off
and on again. The button is slightly hidden within the cartridge:
pressing the middle of the cartridge inwards will trigger it. This might
be a word of warning to those using Game Boy Color or SP, as setting it
down on a table and pushing on it could activate the reset button.
Otherwise, this cartridge is a very solid choice for the price.

USB-based flash cartridges
--------------------------

*Important update!* The lovely folks at insideGadgets have developed a
new USB-based flash cartridge, the
[LinkNLoad32!](https://shop.insidegadgets.com/product/gameboy-linknload32-flash-cart-4mb-128kb-fram-with-usb/).
Using the [GBxCart flasher software](https://www.gbxcart.com/), you are
able to update and back up this cartridge with ease. Although I haven\'t
used it, I can vouch for the quality of insideGadgets cartridges in
general, and would recommend this cart if you are interested in a
dedicated LSDJ flash cartridge.

Possibly the most popular cartridge format are those with their own
mini- or micro-USB port. The EMS 64M Smart Card and the Drag'n'Derp are
arguably the two most popular cartridges of this kind. Sadly,
Drag'n'Derps have not been produced for a number of years and, even more
sadlier, production on EMS 64M cartridges has recently halted. While
stock is still available, you may have luck getting them from either
[retromodding.com](http://retromodding.com) or
[store.kitsch-bent.com](http://store.kitsch-bent.com) (although prices
are likely to rise as the supply dwindles).

Despite their scarcity, I've included the EMS 64M cartridges in this
post because they are extremely popular, and also because a very handy
software called [ems-qart](https://github.com/rbino/ems-qart) makes this
cart much easier to use on modern operating systems ( the software is
written in Java and supports Windows, Mac, and Linux). Once you download
the software, follow the instructions in the README to install the
necessary USB drivers. At that point, you can use the software to manage
any number of roms and save files (both reading and writing)*.* If
you're comfortable at the command-line, [command-line tools are
available](https://github.com/Drenn1/ems-flasher) as well that can make
flashing and backup as simple as typing a command, giving more bang for
the buck for scripting-savvy users.

Flasher-based flash cartridges
------------------------------

When Game Boy flash cartridges started to become widely available to the
public, dedicated flashers were often needed and could be finicky to
use. Although many people find the ease of use of SD-card-based and
USB-based cartridges to be superior, I find it important that this
category isn't overlooked. The folks over at
[insidegadgets.com](http://insidegadgets.com/) have been making some
rock-solid cartridges and flashers for very reasonable prices.

A 1MB cartridge with 128kb SRAM is completely sufficient to run LSDj,
and [this cartridge runs only
\$29](https://shop.insidegadgets.com/product/gameboy-1mb-128kb-sram-flash-cart/).
The shop will flash the LSDj rom of your choice onto the cartridge
before it ships, which means you can get straight to composing in LSDj
on your Game Boy as soon as you get it.

However, if you want to be able to upgrade LSDj, backup your save file,
change the samples on your LSDj rom, or copy a new save onto the
cartridge, you'll need the [GBxCart-mini
flasher](https://shop.insidegadgets.com/product/gbxcart-rw/) in addition
to the cartridge itself**.** Together, they cost \$50, which is less
than the EZ Flash Jr. (not including the cost of a microSD card). But if
you're like me and you want to have two different cartridges (or even
three or four), the cost will be cheaper for each additional cartridge
than it would be to buy the same number of EZ Flash Jr's and microSD
cards.

The GBxCart-mini flasher itself is a tiny PCB with a micro-USB port and
a cartridge slot. You have the choice of whether you want to use a
command-line interface or a graphical interface to manage your roms and
save files. All the programs are downloadable from
[insidegadgets.com](http://insidegadgets.com), and all the source code
is open and freely available. I've modified the code for my own needs so
all I have to do is run one simple command which backs up my save file
to a new file with a timestamp. My version even lets me drag a save or
rom onto a command and flash it onto the cartridge. This won't be the
most convenient option for everyone, and sometimes getting the computer
to detect the cartridge takes some adjusting, but it's otherwise every
bit as simple as using an EMS cartridge. I should also note: the [4MB
ROM 128kb FRAM
cartridge](https://shop.insidegadgets.com/product/gameboy-4mb-128kb-fram-flash-cart/)
uses battery-less memory, meaning you will never have to worry about a
lost save due to a dead cartridge battery. That's pretty great!

I hope you find this useful and if you find any cartridges that I missed
out on, please [let me know](mailto:defensem3ch@gmail.com) so I can
update this for future users. Until next time, this is [DEFENSE
MECHANISM](https://defensemech.com), signing off!

*Note: traducción al Español [por Pixel Guy encontrado
aquí.](https://chiptuneswin.com/blog/intense-tech-con-defense-mech-asi-que-quieres-hablar-de-cartuchos/)*
