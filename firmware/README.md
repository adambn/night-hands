# Firmware

XIAO ESP32S3 Sense + Seeed Bus Servo Driver Board, talking to Feetech
SCS/STS bus servos over half-duplex UART.

Planned:
- `set_servo_id/` — run once per servo, assigns IDs 1–6
- `slider_ui/` — ESP32 hosts a WiFi page with 6 sliders (Jonathan's control panel)
- `poser/` — torque off, pose by hand, press a key to save to `gestures/`
- `hh_robot/` — the main sketch: gestures + distance sensor

Reference + example code: https://wiki.seeedstudio.com/xiao_bus_servo_adapter/
