# ESP32 BLE Combo Keyboard & Mouse library

This library allows you to make the ESP32 act as a Bluetooth keyboard and mouse with Arduino.

## Todo

## Features

 - [x] Send key strokes
 - [x] Send text
 - [x] Press/release individual keys
 - [x] Media keys are supported
 - [ ] Read Numlock/Capslock/Scrolllock state
 - [x] Set battery level (basically works, but doesn't show up in Android's status bar)
 - [x] Compatible with Android
 - [x] Compatible with Windows
 - [x] Compatible with Linux
 - [ ] Compatible with MacOS X (Untested)
 - [ ] Compatible with iOS (Untested)

## Installation
- (Make sure you can use the ESP32 with the Arduino IDE. [Instructions can be found here.](https://github.com/espressif/arduino-esp32#installation-instructions))
- [Download the latest release of this library from the release page.](https://github.com/jakern/ESP32-BLE-Combo/releases)
- In the Arduino IDE go to "Sketch" -> "Include Library" -> "Add .ZIP Library..." and select the file you just downloaded.
- You can now go to "File" -> "Examples" -> "ESP32 BLE Combo" and select any of the examples to get started.

## Example

```
#include <BleCombo.h>

void setup() {
  Serial.begin(115200);
  Serial.println("Starting work!");
  Keyboard.begin();
  Mouse.begin();
}

void loop() {
  if(Keyboard.isConnected()) {
    Serial.println("Sending 'Hello world'");
    Keyboard.println("Hello World");

    Serial.println("Sending Enter key...");
    Keyboard.write(KEY_RETURN);

    Serial.println("Sending Play/Pause media key...");
    Keyboard.write(KEY_MEDIA_PLAY_PAUSE);


    Serial.println("Move mouse pointer up");
    Mouse.move(0,-10);
    
    Serial.println("Scroll Down");
    Mouse.move(0,0,-1);

    Serial.println("Left click");
    Mouse.click(MOUSE_LEFT);
  }
  
  Serial.println("Waiting 2 seconds...");
  delay(2000);
}
```

## API docs
The BleKeyboard interface is almost identical to the Keyboard Interface, so you can use documentation right here:
https://www.arduino.cc/reference/en/language/functions/usb/keyboard/

Just remember that you have to use `bleKeyboard` instead of just `Keyboard` and you need these two lines at the top of your script:
```
## Credits

This is fork of @T-kV's excellent [ESP32-BLE-Mouse](https://github.com/T-vK/ESP32-BLE-Mouse)
and [ESP32-BLE-Keyboard](https://github.com/T-vK/ESP32-BLE-Keyboard) libraries.

You might also be interested in:

- [ESP32-BLE-Mouse](https://github.com/T-vK/ESP32-BLE-Mouse)
- [ESP32-BLE-Keyboard](https://github.com/T-vK/ESP32-BLE-Keyboard)
- [ESP32-BLE-Gamepad](https://github.com/lemmingDev/ESP32-BLE-Gamepad)

Credits to [chegewara](https://github.com/chegewara) and [the authors of the USB keyboard library](https://github.com/arduino-libraries/Keyboard/) as this project is heavily based on their work! Also, credits to [duke2421](https://github.com/T-vK/ESP32-BLE-Keyboard/issues/1) who helped a lot with testing, debugging and fixing the device descriptor!
