# OpenFlops
OpenFlops is an Open Hardware Floppy Disk Drive emulator/simulator.

![Board](https://raw.githubusercontent.com/SukkoPera/OpenFlops/master/doc/render-top.png)

### Summary
From [Wikipedia](https://en.wikipedia.org/wiki/Floppy_disk_hardware_emulator):
> Older models of computers, electronic keyboards and industrial automation often used floppy disk drives for data transfer. Older equipment may be difficult to replace or upgrade because of cost, requirement for continuous availability or unavailable upgrades. Proper operation may require operating system, software and data to be read and written from and to floppies, forcing users to maintain floppy drives on supporting systems.

> Floppy disks and floppy drives are gradually going out of production, and replacement of malfunctioning drives, and the systems hosting them, is becoming increasingly difficult. Floppy disks themselves are fragile, or may need to be replaced often. An alternative is to use a floppy disk hardware emulator, a device which appears to be a standard floppy drive to the old equipment by interfacing directly to the floppy disk controller, while storing data in another medium such as a USB thumb drive, Secure Digital card, or a shared drive on a computer network. Emulators can also be used as a higher-performance replacement for mechanical floppy disk drives. 

OpenFlops is an Open Hardware implementation of such an emulator, inspired from the ubiquitous Gotek hardware. It is designed to run the [FlashFloppy](https://github.com/keirf/FlashFloppy) firmware, which gives it several improvements over the original Gotek:
- Can be installed on [many different platforms](https://github.com/keirf/FlashFloppy/wiki/Host-Platforms)
- Directly supports a [wide range of image formats](https://github.com/keirf/FlashFloppy/wiki/Image-Formats)
- [Flexible track layout](https://github.com/keirf/FlashFloppy/wiki/Track-Layouts) for Raw Sector Images
- [Extremely configurable](https://github.com/keirf/FlashFloppy/wiki/FF.CFG-Configuration-File)
- Supports [AutoSwap](https://github.com/keirf/FF_AutoSwap) for games with a large number of disks
- Easily accessible pin headers for connection of a [i2c display](https://github.com/keirf/FlashFloppy/wiki/Hardware-Mods#lcd-display) (either OLED or LCD), [rotary encoder](https://github.com/keirf/FlashFloppy/wiki/Hardware-Mods#rotary-encoder) (including power)
- Built-in amplified speaker, or easily-accessible pin header for an external one
- USB connector can either be soldered on the board or connected to a pin header
- Connected Motor signal
- Emulates two drives at the same time (Not yet supported by the firmware, but [it will come](https://github.com/keirf/FlashFloppy/wiki/Donations))
- Has additional 3.3V, 5V and GND power pins
- And hey, it's Open Hardware!

All of this comes in the same form factor (and mounting holes) as the board installed in the original Gotek, hence it can be easily installed in any shell or enclosure designed for it.

### Assembly and Installation
Solder all components to the board. I suggest starting with the main microcontroller (U3), as it uses an LQFP package which is tricky to solder: the recommended technique is drag soldering, there are many videos about that on YouTube, so please look there for advice. I recommend to solder the bare minimum components needed for programming and then to try and flash it. This way you will be able to fix your soldering without too many components getting inbetween, if needed. You will need a USB/TTL Serial converter for this: one with 3.3V I/O level is recommended, but a 5V one can be used, too (most pins on STM32 microcontrollers are 5V-tolerant, so don't worry, it's not a bad hack!). You shouldn't pay more then 1-2€ for it in any case, anyway. So, when you are ready:

- Solder U3, Y1, C3 and C5, then the programming header (the top one with power, BOOT0, TX, RX, etc.)
- Check for shorts on the 3.3V power lines, you can easily do this on the pads for C6-C10
- If your USB/Serial adapter has a 3.3V output, connect it to 3.3V on the power header, then connect ground, RX and TX
- If no 3.3V output is available, solder U4 and power the board through the 5V pin on the power header

Now you should be able to [program the STM32 microcontroller](https://github.com/keirf/FlashFloppy/wiki/Firmware-Programming). If you have difficultes you can try adding R10 (and C4) and maybe a few of C6-C10, but most likely the problem will be with the solder joints on U3, as soldering this kind of package manually is never easy, so please get a lens (or even better, a microscope) and double-check yout job.

The serial adapter is only necessary for the first flashing. Subsequent updates [can be done easily via USB](https://github.com/keirf/FlashFloppy/wiki/Firmware-Update).

Note that most components are necessary, but there are a few you can skip if you are feeling lazy:
- If you are not interested in the head movement sound, you can skip the following components: SPK1, D2, R5, R6, Q7.
- If your LCD/OLED display already has pull-up resistors for the SDA/SCK lines (most do), you can skip R3 and R4.

### Configuration
Please refer to the FlashFloppy wiki for the [initial setup](https://github.com/keirf/FlashFloppy/wiki/Initial-Setup) and an overview of the [available configuration options](https://github.com/keirf/FlashFloppy/wiki/FF.CFG-Configuration-File).

Some options that you will want to override the default values of, in order to take advantage of all the features OpenFlops provides are the following:
- `motor-delay`
- `rotary`
- `display-type`

### License
The OpenFlops documentation, including the design itself, is copyright &copy; SukkoPera 2019.

OpenFlops is Open Hardware licensed under the [CERN OHL v. 1.2](http://ohwr.org/cernohl).

You may redistribute and modify this documentation under the terms of the CERN OHL v.1.2. This documentation is distributed *as is* and WITHOUT ANY EXPRESS OR IMPLIED WARRANTIES whatsoever with respect to its functionality, operability or use, including, without limitation, any implied warranties OF MERCHANTABILITY, SATISFACTORY QUALITY, FITNESS FOR A PARTICULAR PURPOSE or infringement. We expressly disclaim any liability whatsoever for any direct, indirect, consequential, incidental or special damages, including, without limitation, lost revenues, lost profits, losses resulting from business interruption or loss of data, regardless of the form of action or legal theory under which the liability may be asserted, even if advised of the possibility or likelihood of such damages.

A copy of the full license is included in file [LICENSE.pdf](LICENSE.pdf), please refer to it for applicable conditions. In order to properly deal with its terms, please see file [LICENSE_HOWTO.pdf](LICENSE_HOWTO.pdf).

The contact points for information about manufactured Products (see section 4.2) are listed in file [PRODUCT.md](PRODUCT.md).

Any modifications made by Licensees (see section 3.4.b) shall be recorded in file [CHANGES.md](CHANGES.md).

The Documentation Location of the original project is https://github.com/SukkoPera/OpenFlops/.

### Support the Project
Since the project is open you are free to get the PCBs made by your preferred manufacturer, however in case you want to support the development, you can order them from PCBWay through this link:

[![PCB from PCBWay](https://www.pcbway.com/project/img/images/frompcbway.png)](https://www.pcbway.com/project/shareproject/OpenFlops_V1.html)

You get my gratitude and cheap, professionally-made and good quality PCBs, I get some credit that will help with this and [other projects](https://www.pcbway.com/project/member/shareproject/?bmbid=41100). You won't even have to worry about the various PCB options, it's all pre-configured for you!

Also, if you still have to register to that site, [you can use this link](https://www.pcbway.com/setinvite.aspx?inviteid=41100) to get some bonus initial credit (and yield me some more).

Again, if you want to use another manufacturer, feel free to, don't feel obligated :). But then you can buy me a coffee if you want:

<a href='https://ko-fi.com/L3L0U18L' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi2.png?v=2' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

### Get Help
If you need help or have questions, you can join [the official Telegram group](https://t.me/joinchat/HUHdWBC9J9JnYIrvTYfZmg).

### Thanks
- [keirf](https://github.com/keirf) for FlashFloppy
