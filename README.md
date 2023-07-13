Upcycle BeoLab 8000 with ZOUDIO AIO438 and Raspberry Pi. All digital stream allows seamless Airplay 2, with close amplifier integration and great sound.

The ZOUDIO amplifier is connected to the Raspberry Pi over USB and I2S. The USB
connection allows `ZOUDIO_daemon.py` to control the amplifier depending on the
Airplay 2 stream state.

Setup the ZOUDIO amplifier with the provide EQ profile, and send `BT DISABLE` to the amplifier to disable the builtin Bluetooth Module. See more about this command here [ZOUDIO / AIO438-firmware-releases](https://github.com/ZOUDIO/AIO438-firmware-releases).

Then setup a newer Raspberry Pi with Raspberry Pi OS Lite, and follow the instructions in [INSTALL.MD](INSTALL.md).