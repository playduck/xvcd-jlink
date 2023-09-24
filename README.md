
As of J-link software pacakge version V7.92d, an official XVCD server is included.

This makes this program obsolete for all future versions!

Check out the official documentation at:
https://wiki.segger.com/J-Link_XVCD_Server

---

# xvcd-jlink

An Xilinx xvc compliant j-link bridge.

The bridge works natively with Vivado without legacy iMPACT or ChipScope.

The code is comprised out of [xvcd-jlink by fantomgs](https://github.com/fantomgs/xvcd-jlink) and [XilinxVirtualCable example](https://github.com/Xilinx/XilinxVirtualCable).

This fork simply adds functionality for the `getinfo` and `settck`.
As of now any arguments to `settck` are ignored.
However this still seems to work.

This has been tested using Vivado 2022.1

## Build

### Windows 

Using `CMake` and `MinGW`

1. `$ cmake . -G "MinGW Makefiles"`
2. `$ make`

Make sure `cmake` and `MinGW`'s bin folder are located in your system `PATH` variable.

### JLinkARM.dll

This fork upgrades the `JLinkARM.dll` to `7.64.5`.
To change the version simply replace the dll.
If you don't have access to the j-link SDK you can find the dll bundled at the installation folder of your j-link driver (usually `C:\Program Files\SEGGER\JLink`).
I have no idea where `JLinkArm.h` originated from.

**Note**: The dll in this repository is for 32-Bit systems/compilations only!
For a 64-Bit system it must be replaced by the corressponding dll from your j-link SDK installation.
Thanks to [Michael from emb4fun](https://www.emb4fun.de) for pointing this out!

## Usage
`xvcd [-v] [-p port] [-s jtag_speed_in_kHz] [-i core_id]`

| Flag | Option | Description |
|---|---|---|
| `-v` | v | verbose |
| `-p` | port | listen port (by default is 2542) |
| `-s` | jtag_speed_in_kHz | speed of the JTAG connection in Khz (by default 1000 kHz) |
| `-i` | core_id | IDCODE of hardware core to search in JTAG chain (probably unnecessary feaure, just for test) |
