# UniSoft Riden Firmware Mirror

This repo is a mirror of alternative firmware created by [UniSoft](https://www.eevblog.com/forum/profile/?u=682208) for the Riden family of power supplies by [RD Tech](https://rdtech.aliexpress.com/store/923042).


## Installation instructions

### Download this firmware:

```bash
git clone git@github.com:wildekek/riden-firmware-unisoft.git
```

### Preparing your power supply:

- Press Shift+Menu to enter settings
- Navigate to "Interface" and set it to "USB".
- (Only if updating UniSoft firmware)
  - Set the USB Interface to 115200
  - Disable UART Interface- 

### Find the serial port:

First list your serial ports:

```bash
$ ls /dev/tty.*
/dev/tty.Bluetooth-Incoming-Port  /dev/tty.wlan-debug
```

Then connect your machine to the Riden via micro-usb and list the ports again

```bash
$ ls /dev/tty.*
/dev/tty.Bluetooth-Incoming-Port /dev/tty.usbserial-110 /dev/tty.wlan-debug
```

In my case the Riden is connected to **/dev/tty.usbserial-110**, remember this when flashing.

### Flash the firmware
I recommend you use Timo Kokkonen's [riden-flashtool](https://github.com/tjko/riden-flashtool). **Make sure to adapt the command to reflect your serial port and device model**:

```bash
$ git clone git@github.com:tjko/riden-flashtool.git
$ cd riden-flashtool
$ pip3 install pyserial
$ ./flash-rd.py /dev/tty.usbserial-110 ../riden-firmware-unisoft/FIRMWARES/RD6006/RD60062_V1.38.1h.bin
Serial port: /dev/tty.usbserial-110 (115200bps)
Firmware size: 201472 bytes
Check if device is in bootloader mode...No
Found device (using Modbus): RD6006 (60062) v1.37
Rebooting to bootloader mode...
Device information (from bootloader):
    Model: RD6006 (60062)
 Firmware: v1.37
      S/N: 00010013
Updating firmware.....................................................................................b'OK'

```

## Manual
A really helpful [user manual](/RD60xx%20Custom%20Firmware%20Reference.pdf) was created by [Sunkmail](https://github.com/sunkmail) with contributing authors Dougg (Doug G.) and bateau020.


## Credits and support
The repo merely serves to easily find the latest version of the firmware and documentation. All credits go to UniSoft for developing and maintaining the software. All firmware issue should be discussed in the relevant [EEVblog thread](https://www.eevblog.com/forum/testgear/ruideng-riden-rd6006-dc-power-supply/msg4302538/#msg4302538).
**Please only create issues in this repo if it is outdated and there is a new firmware version.**
 