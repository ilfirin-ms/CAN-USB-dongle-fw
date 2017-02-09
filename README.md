# CVRA CAN to USB interface [![Build Status](https://travis-ci.org/cvra/CAN-USB-dongle-fw.svg?branch=master)](https://travis-ci.org/cvra/CAN-USB-dongle-fw)

## Usage

use with SocketCAN
```
sudo modprobe can
sudo modprobe can-raw
sudo modprobe slcan

# configure CAN interface
sudo slcan_attach -s8 -o /dev/ttyACM0
sudo slcand ttyACM0 slcan0
sudo ifconfig slcan0 up

# use with can-utils
cansend slcan0 123#2a
candump slcan0
```

## Building & flashing

```
# make sure all submodules are initialized
git submodule update --init

# building
make

# flashing using USB DFU
# to enter DFU mode, press the button while plugging USB in.
make dfu
```


## Supported commands

- 'T', 't', 'R', 'r': send CAN frames
- 'Sx': set bitrate
- 'O': open channel
- 'l', 'L': open in loop back or silent mode
- 'C': close channel
- 'V', 'v': hardware and software version
