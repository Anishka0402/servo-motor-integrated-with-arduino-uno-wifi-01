# Servo Motor Integrated with Arduino UNO (WiFi-01)

A small example project that sweeps a hobby servo back and forth using an Arduino Uno (or compatible board). The project uses the built-in Arduino `Servo` library and is configured for PlatformIO.

## Contents
- `src/main.cpp` — example sketch that sweeps a servo from 0° to 180° and back.
- `platformio.ini` — PlatformIO project configuration.

## Hardware Required
- Arduino Uno (or compatible)
- SG90 / similar hobby servo
- Breadboard and jumper wires (optional)
- External 5V power supply (recommended for stable servo power; see notes below)

## Wiring
- Servo signal (usually orange or yellow) -> Arduino digital pin 9
- Servo VCC (red) -> 5V (or external 5V supply)
- Servo GND (brown or black) -> GND (make sure to share ground with Arduino if using external power)

Important: Many small servos can draw significant current when under load. For reliable operation use a dedicated 5V supply capable of supplying up to 1A and connect grounds together.

## Software / Build
This project is configured to use PlatformIO. The code is in `src/main.cpp` and uses the Arduino core and `Servo` library (bundled with Arduino core on PlatformIO).

Build & upload (PlatformIO CLI):

- Build: `pio run`
- Build & Upload: `pio run --target upload`
- Monitor serial output: `pio device monitor` (the sketch starts Serial at 9600 baud)

If you're using the PlatformIO extension in VS Code or CLion with PlatformIO support, use the GUI buttons (Build, Upload, Monitor).

## Sketch Behavior
When uploaded, the sketch will:
- Attach a servo to digital pin 9
- Sweep smoothly from 0° to 180° in 1° steps (15 ms delay between steps)
- Then sweep back from 180° to 0° in 1° steps
- Repeat indefinitely

You can change the pin, sweep range, speed (delay), and step size in `src/main.cpp`.

## Troubleshooting
- Servo doesn't move: check signal wire is connected to the same pin defined in `main.cpp` (default D9). Confirm servo receives power and ground.
- Unstable movement or resets: servo may draw too much current from the Arduino 5V regulator. Use an external 5V supply and common ground.
- Upload fails: ensure correct board and COM/serial port selected in PlatformIO (`platformio.ini` or IDE project settings).
- Serial monitor shows nothing: Serial.begin(9600) is used; set your serial monitor to 9600 baud.

## Customization
- Change the servo pin by editing the `attach()` call in `src/main.cpp`.
- Change sweep speed by adjusting the `delay()` value.
- Move to non-blocking control (e.g., using millis) if you need to perform other tasks while sweeping.

## License
MIT License — feel free to copy and modify for your own projects.

## Credits
Created from a simple Arduino/PlatformIO example sketch.

--

If you want, I can also:
- Add wiring diagrams or a Fritzing image file
- Provide a non-blocking version using `millis()`
- Add a `CONTRIBUTING.md` or tests (if you plan to run unit tests with PlatformIO)

Tell me which of the above you'd like next.
