# BeagleBone Black PRU
A programmable real-time unit (PRU) is a fast (200-MHz, 32-bit) processor with single-cycle I/O access to a number of the pins and full access to the internal memory and peripherals on the AM3358 processor on BeagleBones. 

1 - if any chage was made in PRU-RC-RECEIVER-00A0 must to re-compile for pru_0 .dts with the following line, then restar bbb:

        dtc -O dtb -I dts -o /lib/firmware/PRU-RC-RECEIVER-00A0.dtbo -b 0 -@ PRU-RC-RECEIVER-00A0.dts

2 - if any change wasn't made should be able to charge the .dtbo without re-compile .dts with the following line whi:

        echo PRU-RC-RECEIVER > /sys/devices/bone_capemgr.?/slots

3 - checkout the configuracion of the followings pins with the following line:

        cat /sys/kernel/debug/pinctrl/44e10800.pinmux/pins

- Table of the correct configuration mode for pins in prus:

        =======================================================================
        pin number | pin in bbb | mode | PRU | description
        _______________________________________________________________________
        15         | P8.15      | 0x26 | 0   | input pin for receiver channel 1
        _______________________________________________________________________
        14         | P8.16      | 0x26 | 0   | input pin for receiver channel 2
        _______________________________________________________________________
        103        | P9.28      | 0x26 | 0   | input pin for receiver channer 3
        _______________________________________________________________________
        101        | P9.29      | 0x26 | 0   | input pin for receiver channel 4
        =======================================================================
