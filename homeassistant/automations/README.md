## Configure this file to be read by HA (edit configuration.yaml)
```yaml

#Aquaponics IOT Monitoring Configuration(Github source)
automation aquaponics: !include aquaponics-iot-monitoring/homeassistant/automations/automations.yaml

```

## Also, create the notification in secrets
```yaml

aquaponics_notification_service: notify.mobile_app_phone

```
## Restart HA