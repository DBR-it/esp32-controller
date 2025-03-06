# ESP32-C6 Smart Controller (Package-Based)

This **ESP32-C6 Smart Controller** configuration is published as an **ESPHome package**, allowing you to include it directly from GitHub without copying YAML files locally.

## Usage
In your **own** ESPHome YAML, add:
```yaml
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

## Customizing the Controller for Wi-Fi
You can override default **substitutions** in your local YAML file wi-Fi options:
```yaml
substitutions:
  device_name: "esp32-wifi-controller"                # Main name for the ESPHome device
  fallback_ssid: "Smart Fallback Hotspot"             # SSID for fallback AP
  fallback_password: "DefaultPassword123"             # Password for fallback AP
  ota_password: "2eac13bfeea21fd59a7926e874d5127a"    # OTA password
  display_switch_name: "Display On/Off"               # Name for the OLED display switch
  button1_name: "Button 1"                            # Name for Button 1
  button2_name: "Button 2"                            # Name for Button 2
  button4_name: "Button 4"                            # Name for Button 4
```
## Customizing the Controller for ethernet
You can override default **substitutions** in your local YAML file Ethernet options:
```yaml
substitutions:
  device_name: "ethernet-controller"  # Main device name (Home Assistant entity)
  display_switch_name: "Display On/Off"
  button1_name: "Button 1"
  button2_name: "Button 2"
  button4_name: "Button 4"
```
### Example Setup Wifi
```yaml
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
packages:
  remote_package_files:
    url: https://github.com/DBR-it/esp32-controller
    files: [esp32_ enet_controller.yaml]
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

