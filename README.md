ESPHome BNO055 Component

A custom ESPHome component for the BNO055 9-axis absolute orientation sensor, designed to provide precise orientation data including pitch, roll, and yaw. This component leverages I²C communication and is built for seamless integration into ESPHome projects.
Features

  Provides orientation data: pitch, roll, and yaw.
   Designed for ESP32 and ESP8266 platforms.
    Easy integration with ESPHome configurations.
    Powered by the Adafruit BNO055 Library.

Installation
Prerequisites

   An ESP32 or ESP8266 device.
    A BNO055 sensor connected via I²C.
    ESPHome installed on your system (Get Started).

Steps

   Clone this repository into your ESPHome project directory:

    git clone https://github.com/your-username/esphome-bno055.git

Add the component to your ESPHome configuration:

   Include the custom component:

    esphome:
    name: bno055_test
    includes:
    - components/bno055/bno055.h

  Register the component:

    custom_component:
      - lambda: |-
          auto bno = new esphome::bno055::BNO055Sensor();
          App.register_component(bno);

Add your I²C configuration to the YAML file (if not already present):

    i2c:
      sda: GPIO21
      scl: GPIO22
      scan: true

Compile and upload the firmware:

    esphome run example.yaml

Dependencies

This component depends on the following libraries:

    Adafruit Unified Sensor Library
    Adafruit BNO055 Library

Make sure these libraries are installed and available in your PlatformIO environment.
Example Configuration

Here’s a complete example YAML file for integrating the BNO055 component:

esphome:
  name: bno055_test
  includes:
    - components/bno055/bno055.h

esp32:
  board: esp32dev

i2c:
  sda: GPIO21
  scl: GPIO22
  scan: true

logger:

custom_component:
  - lambda: |-
      auto bno = new esphome::bno055::BNO055Sensor();
      App.register_component(bno);

Contributing

Contributions are welcome! If you encounter issues or have suggestions, feel free to open an issue or submit a pull request.
License

This project is licensed under the MIT License. See the LICENSE file for details.
Acknowledgements

This component was built to expand ESPHome's functionality and help the community easily integrate the BNO055 sensor into their smart home projects. Created by ChatGPT with ❤️, your friendly AI developer assistant.

If you find this useful, consider sharing your project or leaving feedback!

Feel free to update the repository link and personal credits as needed! Let me know if there’s anything else I can help with. 😊
