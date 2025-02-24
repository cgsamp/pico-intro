# Intro to the Pi Pico

The Raspberry Pi Pico is a microcontroller with on-board digitial General Purpose IO pins, three Analog to Digital (ADC) pins, and support for communication protocols like UART, I2C and one-wire.
https://www.raspberrypi.com/documentation/microcontrollers/pico-series.html

# Programming

The Pico can be programmed in C or Python. This guide uses Micropython.

## Flashing Firmware

Step one is getting the right firmware on the Pico.
1. Download the appropriate Micropython firmware. [Micropython for Pi Pico 2 W](https://micropython.org/download/RPI_PICO2_W/)
2. Connect the Pico to your computer via USB in Storage Device mode.
  a. Use a MicroUSB cable connected to your computer.
  b. Hold the BOOTSEL button while connecting the USB cable to the Pico.
  c. Release the BOOTSEL button.
  d. The Pico will appear as a USB drive in your File Explorer.
3. Drag and drop the .uf2 file onto the Pico.
4. Disconnect the Pico from the USB
5. Reconnect the Pico with the USB without pressing any buttons.

The Pico will boot with the new firmware and be in Serial mode.

## Writing and Uploading Code

Coding is similar to writing Python in other environments, except that it is handy (essential) to have a Pico connected to the PC in normal (not USB) mode, so that it may execute the code. The only real complication is making sure all code files are synchronized. If you edit program.py, and then fail to copy it to the Pico, you will have a lot of frustration as you wonder why your changes don't work.

[Thonny](https://thonny.org/) is a common standalone IDE that is ... sufficient. There are also plug-ins for VS Code for a more robust development environment.

- Connect the Pico to the PC.
- Launch Thonny.
- Choose File / View -> Files, File / View -> Shell to see those windows.
- In the bottom right, you have to select the Pico as the target runtime. (There are various things that go wrong here, but generally it seems to work.)
- In the top File window, navigate to the location of your project.
- Here you can right-click on a given file and "Copy to /" to copy it to the Pico's root. You can move entire folders.
- If you have code open in the main code window, and it has focus, F5 will run the current editor's code on the Pico.

## Hello-World

The classic hello world is blink.py, that makes the on-board LED blink.

# Connecting Hardware

It's nice to have the pinout chart handy.
https://www.raspberrypi.com/documentation/microcontrollers/pico-series.html#pinout-and-design-files

## Switches

A Switch will connect to one of the Pico's GPIO pins, and the other side of the switch will connect to GND. The Pico has an internal pull-up resistor, so the GPIO sees +3.3V when the switch is OFF / not connected, and 0V when the switch is ON.

## Potentiometers

Pots have the left and right pins connected to GND and +3.3V respectively, with the center pin, Wiper, attached to one of the ADC pins.

## I2C Devices

Many devices like displays use the I2C protocol, that allows the Pico to send commands and data by sending binary. Two of their pins connected to 0V and +3.3V, and the other two connect to SDC and SCA pins on the Pico.
