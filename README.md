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

## How It Works

The aquaponics system uses a bell siphon to periodically drain the grow bed into a sump, where water is constantly pumped into the fish tank which steatily overflows into the grow bed.

As the bed fills, water passes the lower and upper float switches. Once the water reaches the appropriate level, the bell siphon initiates drainage.

The monitoring system tracks these transitions to identify operating phases and calculate elapsed times.

### Operating States
- Filling	- Water level is rising
- Draining - Water level is falling
- Waiting for Siphon Cutoff - Water has fallen below the lower float switch, and the siphon will eventually automatically cut off.

These states are inferred from float-switch transitions. The system does not directly measure water flow through the siphon.

### Cycle Measurements
- Fill Duration - Time associated with the filling portion of the cycle
- Drain Duration - Time associated with the draining portion of the cycle
- Siphon Cutoff Duration - Time spent below the lower float switch
- Cycles Last 60 Minutes- Number of completed cycles during the preceding hour

### Aquaponics Monitoring Dashboard

The Home Assistant dashboard displays current water-level sensor states, inferred operating states, cycle statistics, and duration measurements.

TBD - Image of the sensors

### Watch the Aquaponics Monitoring System in Action

The demonstration covers a complete flood-and-drain cycle, sensor transitions, real-time dashboard updates, and fault detection.

TBD - Video or link to YouTube

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

See Hardware Documentation for component information, wiring, and installation details.

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
