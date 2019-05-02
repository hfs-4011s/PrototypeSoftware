Based off of the ESP-IDF A2DP-SINK demo
======================

This uses the Bluetooth legacy profile A2DP for audio stream reception, AVRCP for media information notifications, and I2S for audio stream output interface.

When connected to a speaker, this code allows the ESP32 to function as a basic bluetooth speaker.

### Hardware Required

To play the sound, there is a need of loudspeaker and possibly an external I2S codec. Otherwise, the output can be monitored through the count of audio packets and commands recieved from an external bluetooth device.

The I2S DAC used with this code is the UDA1334A BR. The pinout is as follows

| ESP pin   | I2S signal   |
| :-------- | :----------- |
| GPIO22    | DATA         |
| GPIO25    | LRCK         |
| GPIO26    | BCK          |

### Configure the project

Run
```
make menuconfig
```
to about an SDK to allow for the configuration of the code and ESP32

* Set serial port under Serial Flasher Options.
* Set the use of external I2S codec for audio output, and configure the output PINs under A2DP Example Configuration
* Enable Classic Bluetooth and A2DP under Component config --> Bluetooth --> Bluedroid Enable

### Build and Flash

Build the project and flash it to the board, then run monitor tool to view serial output.
```
make -j4 flash monitor
```
(To exit the serial monitor, type ``Ctrl-]``.)

## Output

After the program is started, the esp-32 awaits to be discovered by another bluetooth device and have a device connect to it. It will appear on other bluetooth devices as "ESP_SPEAKER". Any smartphone or other bluetooth compatible device should be able to connect with it