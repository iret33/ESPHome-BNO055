#include "esphome.h"
#include <Adafruit_Sensor.h>
#include <Adafruit_BNO055.h>

namespace esphome {
namespace bno055 {

class BNO055Sensor : public PollingComponent {
 public:
  BNO055Sensor() : PollingComponent(1000) {}

  void setup() override {
    if (!bno_.begin()) {
      ESP_LOGE("BNO055", "BNO055 initialization failed!");
    } else {
      ESP_LOGI("BNO055", "BNO055 initialized successfully.");
    }
  }

  void update() override {
    sensors_event_t event;
    bno_.getEvent(&event);
    ESP_LOGI("BNO055", "Orientation: x=%f, y=%f, z=%f",
             event.orientation.x, event.orientation.y, event.orientation.z);
  }

 private:
  Adafruit_BNO055 bno_ = Adafruit_BNO055(55);
};

}  // namespace bno055
}  // namespace esphome
