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
- Built-in amplified speaker, or easily-accessible pin header for external one
- Connected Motor signal
- Emulates two drives at the same time (Not yet supported by the firmware, but [it will come](https://github.com/keirf/FlashFloppy/wiki/Donations))
- And hey, it's Open Hardware!

All of this comes in the same form factor (and mounting holes) as the board installed in the original Gotek, hence it can be easily installed in any shell or enclosure designed for it.

### Assembly and Installation
Solder all components to the board. I suggest starting with the main microcontroller (U3), as it uses an LQFP package which is tricky to solder.

Most components are necessary, but there are a few you can skip:

- If you are not interested in the head movement sound, you can skip the following components: SPK1, D2, R5, R6, Q7.
- If your LCD/OLED display already has pull-up resistors for the SDA/SCK lines (most do), you can skip R3 and R4.

After everything has been soldered, you will need to program the STM32 microcontroller. The first time you are doing so, please [refer to these instructions](https://github.com/keirf/FlashFloppy/wiki/Firmware-Programming). Subsequent updates [can be done easily via USB](https://github.com/keirf/FlashFloppy/wiki/Firmware-Update).

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
