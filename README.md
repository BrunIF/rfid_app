rfid_app
========

Linux command line tool for China 125kHz rfid reader/writer (RFID_APP_EN)

## install

```bash
wget -c https://github.com/BrunIF/rfid_app/releases/download/v.1.0/rfid_app -O rfid
chmod +x ./rfid
sudo cp rfid /usr/bin/
```

p1d_rfid
========

Linux command line tool for Priority 1 Design rfid reader/writer


idrw_linux
==========

Linux command line tool for another China 125kHz rfid reader/writer usb based one (ffff:0035)


Building
========

make - for building the binaries
make install - for installing the idrw_linux udev rules file


Usage
=====

```bash
./rfid_app
rfid_app version 1.0, Copyright (c) 2014 Benjamin Larsson <benjamin@southpole.se>
Usage: rfid_app [OPTION]...
	 -r Read rfid tag/fob
	 -f [0|1|2|3|4] output read result in different formats
	 -l try to detect rfid hardware
	 -d tty device to connect to (/dev/ttyUSB0 default)
	 -w [10 char hex string] write data to tag/fob
	 -b don't beep while accessing tag/fob, might affect some tags
```

Detect rfid hardware:
```
./rfid_app -l
Found device: ID card reader & writer6
```

```
./p1d_rfid -l
Found P1D device with firmware version: 208
```

Reading a tag (default hex output):
```
./rfid_app -r
0F0021BC9B
```

Reading a tag (spaced hex output):
```
./rfid_app -r -f 1
```

Reading a tag (decimal output):
```
./rfid_app -r -f 2
0002210971
```

Reading a tag (2H+4H decimal output):
```
./rfid_app -r -f 4
033,48283
```

Writing a tag:
```
./rfid_app -w 0F0021BC9B
0F0021BC9B
```

Writing to an incompatible tag:
```
./p1d_rfid -w 0F0021BC9B
NOTAG
```

