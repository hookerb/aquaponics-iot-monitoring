##  Add the dashboard to HA be adding this to configureation.yaml
```yaml
# Aquaponics IoT Monitoring Dashboard (GitHub source)
lovelace:
  mode: storage
  dashboards:
    aquaponics-monitoring:
      mode: yaml
      title: Aquaponics Monitoring
      icon: mdi:fishbowl
      show_in_sidebar: true
      filename: aquaponics-iot-monitoring/homeassistant/dashboards/aquaponics.yaml
```