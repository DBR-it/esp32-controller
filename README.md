# ESP32-C6 Smart Controller (Package-Based)

This **ESP32-C6 Smart Controller** configuration is published as an **ESPHome package**, allowing you to include it directly from GitHub without copying YAML files locally.

## Usage
In your **own** ESPHome YAML, add:
```yaml
esphome:
  name: ${device_name}

packages:
  remote_package_files:
    url: https://github.com/DBR-it/esp32-controller
    files: [esp32_controller.yaml]
    ref: main
    refresh: 1d    
```

### How It Works
- The **`packages`** section pulls the YAML configuration directly from GitHub.
- The **`${device_name}`** is the customizable name for your device in Home Assistant.
- The configuration is updated automatically based on the `refresh` interval (e.g., `refresh: 1d`).

## Customizing the Controller
You can override default **substitutions** in your local YAML file:
```yaml
substitutions:
  device_name: "my_smart_controller"
  use_ethernet: "true"  # Set to "true" for Ethernet or "false" for Wi-Fi
  display_switch_name: "Display Power"
  button1_name: "Left Button"
  button2_name: "Center Button"
  button4_name: "Right Button"
  fallback_ssid: "My-Fallback-AP"
  fallback_password: "AnotherPassword"
```

### Example Setup Wifi
```yaml
esphome:
  name: ${device_name}

packages:
  remote_package_files:
    url: https://github.com/DBR-it/esp32-controller
    files: [esp32_controller.yaml]
    ref: main
    refresh: 1d

substitutions:
  device_name: "my_smart_controller"
  use_ethernet: "true"
  display_switch_name: "Display Power"
  button1_name: "Left Button"
  button2_name: "Center Button"
  button4_name: "Right Button"
  fallback_ssid: "My-Fallback-AP"
  fallback_password: "AnotherPassword"
```
### Example Setup Ethernet
```yaml
esphome:
  name: ${device_name}

packages:
  remote_package_files:
    url: https://github.com/DBR-it/esp32-controller
    files: [esp32_ enet_ controller.yaml]
    ref: main
    refresh: 1d 
    
substitutions:
  device_name: "ethernet_controller"  # Main device name (Home Assistant entity)
  display_switch_name: "Display On/Off"
  button1_name: "Button 1"
  button2_name: "Button 2"
  button4_name: "Button 4"
```
## What This Controller Does
- Uses an **ESP32-C6** with optional **Ethernet (W5500)** or **Wi-Fi**.
- Displays **IP Address** and **Network Status** on an **SSD1306 OLED**.
- Supports **Home Assistant** integration and **OTA updates**.
- Provides a **web server** on port 80 for local access.
- Allows customization of **button names** and **display controls**.

This approach keeps your local configuration clean and allows automatic updates through the remote package. Feel free to expand on this README or add project-specific details as needed!

