# Configure ESPHome to read this add on:

## Create the device in ESPHome Builder with the yaml below:
```yaml
# Aquaponics IoT Monitoring
# Source: aquaponics-iot-monitoring Git repository

substitutions:
  wifi_ssid: !secret wifi_ssid
  wifi_password: !secret wifi_password
  aquaponics_api_encryption_key: !secret aquaponics_api_encryption_key
  aquaponics_fallback_password: !secret aquaponics_fallback_password

packages:
  aquaponics:
    !include ../aquaponics-iot-monitoring/esphome/aquaponics-water-level.yaml
```

## Create the secrets in your secrets.yaml in the device's home
