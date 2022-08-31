# ESP32-S3 Camera IO board with 4G module

Sponsored by [FilzerTech](https://filzertech.com/)

<img src="https://github.com/hotteshen/esp32-s3-camera-4g/blob/develop/doc/pcba.png?raw=true" style="width: 50%">

## Hardware Summary

* ESP32-S3-WROOM-1
* Camera interface
  - tested with OV2640, OV5640
  - support auto focus camera power pins
* 4G module interface
  - tested with SIM7600G 4G LTE module
* IO
  - PCA9554 I2C I/O expander
  - PCA9531 PWM LED driver
  - BMP280 / BME280 environmental sensors for humidity, temperature, and pressure sensing
  - buttons and LEDs

## Testing with [ESP-WHO](https://github.com/espressif/esp-who)

Tested with `human_face_detection` example of [ESP-WHO](https://github.com/espressif/esp-who) library.

```sh
git clone https://github.com/espressif/esp-who
cd examples/human_face_detection/web
idf.py set-target esp32s3
idf.py menuconfig
idf.py build flash monitor
```

At the time of working on this project, the ESP32-S3-WROOM-1U-N16R8 used in the design was out of stock on JLCPCB.
Thus, used ESP32-S3-WROOM-1-N8R2 [C2913204](https://lcsc.com/product-detail/WiFi-Modules_Espressif-Systems-ESP32-S3-WROOM-1-N8R2_C2913204.html) while ordering PCBA on [JLCPCB's online ordering form](https://jlcpcb.com/quote).

ESP32-S3-WROOM-1-N8R2 has 8MB of Flash memory and 2MB or QSPI mode PSRAM.
Thus it needed to configure patition table and boot mode accordingly on menuconfig.

For reference, copies of `sdkconfig` and `partitions.csv` files are included in [`doc`](./doc/) folder.
