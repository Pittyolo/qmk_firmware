# Bevezetés

A számítógép billentyűzében is egy processzor van, éppmint a számítógépében. Ezen processzoron futó program feladata a billentyű lenyomások észlelése és a billentyűzet állapotának küldése, ha a billentyűket lenyomják vagy felengedik. A QMK játsza a szoftver szerepét, észleli a gombnyomásokat és továbbítja ezeket az információkat a számítógép felé. Amikor egyéni keymap-et hoz létre, egy a billentyűzeten futtatható program megfelelőjét hozza létre.

A QMK sok hatalmat próbál a kezébe tenni azáltal, hogy a könnyű dolgokat könnyűvé, a nehezeket lehetővé teszi. Nem kell tudnia programozni egy jó keymap létrehozásához - csak néhány egyszerű szintaxisszabályt kell követnie.

# A kezdetek

Mielőtt elkezdené elkészíteni a keymap-jét, néhány software-t kell installálnia és elő kell készítenie a programozási környezetet. Ezt csak egyszer kell megtenni, függetlenül attól, hogy hány billentyűzetre tervezi a firmware szerkesztését.

Ha inkább a grafikusa felhasználói felületet szereti, kérjük fontolja meg az online [QMK Configurator] (https://config.qmk.fm) használatát. Lásd: [Első firmware létrehozása az online felület felhasználásával] (newbs_building_firmware_configurator.md).

## Software-ek letöltése

### Szövegszerkesztő

Szüksége lesz egy programra, amellyel **egyszerű szöveges** fájlokat szerkeszthet és menthet el. Ha Windows rendszert használ, megteszi a Jegyzettömböt, és Linuxon a gedit is használható. Mindkettő egyszerű, de hasznos szövegszerkesztő. MacOS rendszeren legyen óvatos az alapértelmezett TextEdit alkalmazással: nem menthet egyszerű szöveges fájlokat, kivéve, ha a _Make Plain Text_ menüpontot választja a _Format_ menüből.

You can also download and install a dedicated text editor like [Sublime Text](https://www.sublimetext.com/) or [VS Code](https://code.visualstudio.com/). This is probably the best way to go regardless of platform, as these programs are specifically made for editing code.

Letölthet és telepíthet egy dedikált szövegszerkesztőt, például a [Sublime Text] (https://www.sublimetext.com/) vagy a [VS Code] (https://code.visualstudio.com/). Ez valószínűleg a legjobb mód a platformtól függetlenül történő továbblépéshez, mivel ezeket a programokat kifejezetten a kód szerkesztésére készítették.

?> Not sure which text editor to use? Laurence Bradford wrote [a great introduction](https://learntocodewith.me/programming/basics/text-editors/) to the subject.

### QMK Toolbox

QMK Toolbox is an optional graphical program for Windows and macOS that allows you to both program and debug your custom keyboard. You will likely find it invaluable for easily flashing your keyboard and viewing debug messages that it prints.

[Download the latest release here.](https://github.com/qmk/qmk_toolbox/releases/latest)

* For Windows: `qmk_toolbox.exe` (portable) or `qmk_toolbox_install.exe` (installer)
* For macOS: `QMK.Toolbox.app.zip` (portable) or `QMK.Toolbox.pkg` (installer)

## Set Up Your Environment

We've tried to make QMK as easy to set up as possible. You only have to prepare your Linux or Unix environment, then let QMK install the rest.

?> If you haven't worked with the Linux/Unix command line before, there are a few basic concepts and commands you should learn. These resources will teach you enough to be able to work with QMK:<br>
[Must Know Linux Commands](https://www.guru99.com/must-know-linux-commands.html)<br>
[Some Basic Unix Commands](https://www.tjhsst.edu/~dhyatt/superap/unixcmd.html)

### Windows

You will need to install MSYS2 and Git.

* Follow the installation instructions on the [MSYS2 homepage](http://www.msys2.org).
* Close any open MSYS2 terminals and open a new MSYS2 MinGW 64-bit terminal.
* Install Git by running this command: `pacman -S git`.

### macOS

You will need to install Homebrew. Follow the instructions on the [Homebrew homepage](https://brew.sh).

After Homebrew is installed, continue with _Set Up QMK_. In that step you will run a script that will install other packages.

### Linux

You will need to install Git. It's very likely that you already have it, but if not, one of the following commands should install it:

* Debian / Ubuntu / Devuan: `apt-get install git`
* Fedora / Red Hat / CentOS: `yum install git`
* Arch: `pacman -S git`

?> Docker is also an option on all platforms. [Click here for details.](getting_started_build_tools.md#docker)

## Set Up QMK

Once you have set up your Linux/Unix environment, you are ready to download QMK. We will do this by using Git to "clone" the QMK repository. Open a Terminal or MSYS2 MinGW window and leave it open for the remainder of this guide. Inside that window run these two commands:

```shell
git clone --recurse-submodules https://github.com/qmk/qmk_firmware.git
cd qmk_firmware
```

?> If you already know [how to use GitHub](getting_started_github.md), we recommend that you create and clone your own fork instead. If you don't know what that means, you can safely ignore this message.

QMK comes with a script to help you set up the rest of what you'll need. You should run it now by typing in this command:

    util/qmk_install.sh

## Test Your Build Environment

Now that your QMK build environment is set up, you can build a firmware for your keyboard. Start by trying to build the keyboard's default keymap. You should be able to do that with a command in this format:

    make <keyboard>:default

For example, to build a firmware for a Clueboard 66% you would use:

    make clueboard/66/rev3:default

When it is done you should have a lot of output that ends similar to this:

```
Linking: .build/clueboard_66_rev3_default.elf                                                       [OK]
Creating load file for flashing: .build/clueboard_66_rev3_default.hex                               [OK]
Copying clueboard_66_rev3_default.hex to qmk_firmware folder                                        [OK]
Checking file size of clueboard_66_rev3_default.hex                                                 [OK]
 * The firmware size is fine - 26356/28672 (2316 bytes free)
```

# Creating Your Keymap

You are now ready to create your own personal keymap! Move on to [Building Your First Firmware](newbs_building_firmware.md) for that.
