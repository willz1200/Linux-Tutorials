How to change the ATmega2560 bootloader frequency and upload speed (stk500v2)
==================================================================================

- This will allow you to reliably run an Arduino Mega at **3.3V**! Use Frequency: 8MHz, Upload Speed: 15200 to achieve this.

- The default for the Arduino Mega is, Frequency: 16MHz, Upload Speed: 115200

- Download the precompiled binary with your required parameters using the following table:

|                       | Frequency = 8MHz                                          | Frequency = 16MHz                                          |
|-----------------------|-----------------------------------------------------------|------------------------------------------------------------|
| Upload Speed = 9600   | [Binary](stk500v2/stk500boot_v2_mega2560-8MHz-9600.hex)   | [Binary](stk500v2/stk500boot_v2_mega2560-16MHz-9600.hex)   |
| Upload Speed = 115200 | [Binary](stk500v2/stk500boot_v2_mega2560-8MHz-115200.hex) | [Binary](stk500v2/stk500boot_v2_mega2560-16MHz-115200.hex) |

## How to Install the new bootloader

1. The bootloader lives inside this `arduino-x.x.x/hardware/arduino/avr/bootloaders/stk500v2/` folder.

2. The `arduino-x.x.x/hardware/arduino/avr/boards.txt` file is used to configure the operating parameters of the arduino, you must change the frequency and upload speed to match your bootloader using the following line:

Set the operating frequency in Hz e.g. 8MHz = `8000000L` or 16MHz = `16000000L`:  

- `mega.build.f_cpu=16000000L`

Set the upload speed either `9600` or `115200`:

- `mega.menu.cpu.atmega2560.upload.speed=115200`

If you didn't rename the bootloader to its original name then change the following line to match your filename:

- `mega.menu.cpu.atmega2560.bootloader.file=stk500v2/stk500boot_v2_mega2560.hex`

## How to compile your own bootloader binary under linux

- This is only necessary if the parameters you need aren't in the table above.

1. Install the AVR compiler

`sudo apt-get install gcc-avr binutils-avr avr-libc`

2. Move to the bootloader source code directory (Can be acquired from the Arduino github repo)

`cd stk500v2/`

3. To change the operating frequency and upload baud rate, open the makefile and edit the following lines (You may need to add the `mega2560: BAUDRATE =` line):

```
mega2560:	F_CPU = 16000000
mega2560: BAUDRATE = 115200
```

3. Clean previously compiled files

`make clean`

4. Compile the bootloader

`make mega2560`
