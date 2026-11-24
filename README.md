# Aquaponics IoT Monitoring

## ESP32-Based Flood & Drain Monitoring with ESPHome and Home Assistant

An IoT monitoring system designed to measure, analyze, and monitor the operation of a flood-and-drain aquaponics grow bed using an ESP32 microcontroller, water-level float switches, and Home Assistant.

The system provides real-time monitoring of water levels, flood-and-drain cycle performance, and operating conditions while automatically detecting abnormal behavior and generating alerts.

The project combines embedded programming, event-driven state management, sensor integration, home automation, and operational monitoring.

### System Overview

The monitoring system uses two float switches installed at different heights within an aquaponics grow bed.

An ESP32 running ESPHome processes sensor transitions, tracks operating cycles, and calculates performance metrics.

Home Assistant provides historical analysis, dashboards, andautomated notifications.

### Key Features

#### Real-Time Monitoring
- Upper and lower water-level sensors
- Current operating state
- Last sensor transition
- Flood-and-drain cycle tracking

#### Performance Metrics
- Fill duration
- Drain duration
- Time below the lower water-level sensor
- Completed cycles during the last 60 minutes

#### Fault Detection
- Detects prolonged upper water-level activation
- Detects prolonged low-water conditions
- Generates automatic alerts when thresholds are exceeded
- Supports mobile notifications through Home Assistant

#### Integration
- ESP32 microcontroller
- ESPHome firmware
- Custom C++ lambda-based processing
- Home Assistant automation and template sensors
- Home Assistant monitoring dashboard

### Information gathered
This system intends to answer the following questions regarding the health of the system.
- How often is the grow bed filled?
- How long does it take to drain the bed?
- How long does it take to break the bell siphon?
- How long does it take to fill the grow bed up?

### Common Error States
- Water has risen to the high water mark, but has stayed above it for some time.  This can be caused my many different factors such as water flow into the bed, or physical characteristics of the drain or bell siphon.
- Water has dropped below the low water mark, and has stayed at that low point for some time.  This can also be caused by various factors from water flow to physical drain characteristics.

## How It Works

The aquaponics system uses a bell siphon to periodically drain the grow bed into a sump tank below it. The water that is drained into the sump is then pumped at a steady rate into a 65 gallon fishtank on display in the other room.  The water then overflows and a series of pipes direct it back into the flood and drain pan where the precession starts again.

### Physical Sensor Input
- Top float off->on (while bottom float is on) - Water has risen to the high water mark.
- Top float on->off (While bottom float is on) - Water has dropped below the high water mark.
- Bottom float on->off (While top float is off) - Water has drained down below the lowest water mark.
- Bottom float off->on (While top float is off) - Siphon has stopped, and water has begun to fill.

### Operating States
- Filling	- Water level is rising
- Draining - Water level is falling
- Waiting for Siphon Cutoff - Water has fallen below the lower float switch.

These states are inferred from float-switch transitions. The system does not directly measure water flow through the siphon.

### Cycle Measurements
- Fill Duration - Time from lower switch on to upper switch on.
- Drain Duration - Time from the upper switch off to lower switch off.
- Siphon Cutoff Duration - Time spent between lower switch off to lower switch on.
- Siphon Start Duration - Time from the upper switch on to upper switch off.
- Cycles Last 60 Minutes - Number of completed cycles during the preceding hour.

### Aquaponics Monitoring Dashboard

The Home Assistant dashboard displays current water-level sensor states, inferred operating states, cycle statistics, and duration measurements.

<img width="420" height="450" alt="IMG_1477" src="https://github.com/user-attachments/assets/0e3a40c9-0e57-4f2a-8d60-2e1bd7a01394" />

### Watch the Aquaponics Monitoring System in Action

The demonstration covers a complete flood-and-drain cycle, sensor transitions, real-time dashboard updates, and fault detection.

https://github.com/user-attachments/assets/8533c0d9-8118-44ad-bc63-8f14ca01b804

## System Architecture
The system consists of three primary layers.
### Embedded Monitoring
  - An ESP32 reads the float switches and processes water-level transitions.
  - Custom C++ logic embedded in ESPHome handles cycle tracking and duration calculations.
### Home Assistant Integration
  - Home Assistant receives sensor information over the local network and provides additional processing through template sensors and automations.
### Visualization and Alerting
 - A dedicated Home Assistant dashboard provides real-time monitoring.
 - Automations detect abnormal operating conditions and generate notifications.

For additional details, see System Architecture.

## Hardware
The monitoring system uses:
- ESP32 development board
- Two water-level float switches
- Protective electronics enclosure
- Electrical connections and mounting hardware
- Existing flood-and-drain aquaponics grow bed

<img width="375" height="450" alt="Aquaponics_Float_Monitor" src="https://github.com/user-attachments/assets/0e76a0b2-fc18-42f5-9fc2-0e97f33938f2" />

## Software
- Microcontroller	- ESP32	- Sensor acquisition
- Firmware - ESPHome - Device configuration and integration
- Embedded logic - C++ - Cycle tracking and calculations
- Automation platform - Home Assistant - Monitoring, analytics, and alerts
- Configuration management - Git / GitHub	Version control and documentation\

## Repository Structure
- esphome/ — ESP32 configuration and embedded monitoring logic
- homeassistant/automations/ — Fault detection and alerting
- homeassistant/sensors/ — Historical cycle statistics
- homeassistant/dashboards/ — Dashboard configuration
- templates/ — Operating-state interpretation
- hardware/ — Hardware components and assembly
- docs/ — Architecture, installation, and additional documentation

## Installation
The system requires a working Home Assistant installation and an ESP32-compatible ESPHome environment.

Installation involves configuring the ESP32, connecting the float switches, setting local credentials, and enabling the Home Assistant monitoring components.

See Installation Guide for detailed instructions.

## Project Goals
This project was developed to improve visibility into the operation and reliability of a flood-and-drain aquaponics system.

Its primary engineering goals are:
- Detect abnormal operating conditions before they cause equipment or system problems.
- Provide measurable data about flood-and-drain performance.
- Reduce reliance on manual observation.
- Build a maintainable monitoring solution using readily available IoT hardware.
- Support troubleshooting through operational metrics and event history.
- Maintain reusable configuration in version control.

## Future Improvements
Potential enhancements include:
- Long-term cycle performance analysis
- Detection of unusual changes in fill and drain durations
- Additional water-quality and environmental sensors
- More advanced fault detection
- Improved system diagnostics
Documentation
- ESPHome Configuration
- Home Assistant Integration
- Hardware
- System Architecture
- Installation
- Monitoring Logic
- Video Demonstrations
