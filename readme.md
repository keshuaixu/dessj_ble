# firmware for dESSJ

# build environment

1. install `arduino-cli`.

https://arduino.github.io/arduino-cli/0.23/installation/

2. plug in the arduino, check if arduino-cli sees it.

```
arduino-cli board list
```

Expect something like this

```
Port         Protocol Type              Board Name          FQBN                        Core             
/dev/ttyACM0 serial   Serial Port (USB) Arduino Nano 33 BLE arduino:mbed_nano:nano33ble arduino:mbed_nano
```


3. install the board and library

```
arduino-cli core install arduino:mbed_nano
arduino-cli lib install ArduinoBLE
```

# compile

`cd` into this directory.

```
arduino-cli compile -b arduino:mbed_nano:nano33ble .
```

# upload the firmware to board

```
arduino-cli upload -b arduino:mbed_nano:nano33ble -p /dev/ttyACM0
```

Replace `/dev/ttyACM0` with the serial port that the arduino is on.

If you cannot upload, press the button on the arduino twice. You should see a fading yellow light, indicating the bootloader is running.

# serial monitor

You can use any serial monitor program to look at the serial output. The baud rate does not matter, because everything is native USB and no actual UART happens.

```
arduino-cli monitor -p /dev/ttyACM0
```