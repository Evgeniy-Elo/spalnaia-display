# Spalnaia Display

ESPHome node for a dedicated display that shows a "beautiful" thermostat UI while the real thermostat runs on a separate ESPHome node.

This repository contains an example ESPHome configuration (for ESP8266 / Wemos D1 Mini + ST7789 240×240) which reads all data from Home Assistant and renders it on the display.

Files
- spalnaia-display.yaml — main ESPHome configuration (example)
- LICENSE — MIT license
- .gitignore — ignores local/IDE files

Quickstart
1. Place this repo on your machine or clone it into your ESPHome configuration folder.
2. Edit spalnaia-display.yaml:
   - Replace `!secret wifi_ssid`, `!secret wifi_password`, and `!secret ota_password` with your secrets or keep them and set them in your ESPHome secrets file.
   - Verify `entity_id` values (the example assumes `climate.spalnaia`). Change if your entity is named differently (Developer Tools → States in Home Assistant).
   - Adjust display pins (spi clk/mosi, reset, dc, cs) to match your wiring.
   - Put TTF font files under `fonts/` relative to the ESPHome config directory (e.g. `config/esphome/fonts/Roboto-Regular.ttf`).
3. Upload to the display device via `esphome run spalnaia-display.yaml`.

Notes and recommendations
- The provided lambda is a basic drawing example (big temperature, needle, target, preset and mode). You can extend it to match the pictured UI (colored gradient arc, triangle pointer for target temp, wifi/time icons, presets buttons).
- Performance: ESP8266 has limited RAM. If you run into memory issues or want smoother graphics, use ESP32.
- Control: The example includes two GPIO buttons mapped to increase/decrease the target temperature by 0.5°C. You can replace with touch input or on-screen controls if your display supports touch.

If you want I will adapt the pins and entity_id to your exact hardware and draw a more detailed lambda to match the image UI.
