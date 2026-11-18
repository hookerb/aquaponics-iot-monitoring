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
<img width="420" height="450" alt="IMG_1477" src="https://github.com/user-attachments/assets/112f7994-a73a-4de4-b0ed-39813e3c1676" />
