---
title: Energieleser
description: Instructions on how to integrate Energieleser devices within Home Assistant.
ha_release: 2026.6
ha_category:
  - Energy
  - Sensor
ha_codeowners:
  - '@AjinkyaGokhale'
ha_quality_scale: bronze
ha_domain: energieleser
ha_integration_type: device
ha_iot_class: Local Polling
ha_config_flow: true
ha_zeroconf: true
ha_platforms:
  - sensor
---

The Energieleser {% term integration %} fetches real-time energy data from your Energieleser devices, such as Stromleser, Gasleser, Wasserleser, and Wärmeleser, using a local HTTP API.

Energieleser is manufactured by nineti GmbH, a German company that provides smart readers for various utility meters.

{% include integrations/config_flow.md %}

### Configuration parameters

{% configuration_basic %}
Host:
  description: The IP address of your Energieleser device.
{% endconfiguration_basic %}

## Data updates

The integration fetches data by locally polling the device's async HTTP web server.
## Available sensors

The following sensors are supported depending on the device type and meter capabilities:

- **stromleser**:
  - Imported energy (kWh): Cumulative energy consumed
  - Exported energy (kWh): Cumulative energy exported to the grid
  - Active power (W): Current active power
  - Phase 1,2,3 power (W): Current active power per phase
- **gasleser**:
  - Total gas (m³): Cumulative gas volume consumed
  - Gas flow rate (m³/h): Current gas flow speed
- **wasserleser**:
  - Total water (m³): Cumulative water volume consumed
  - Water flow rate (l/h): Current water flow rate in liters per hour
  - Volume flow rate (m³/h): Current water flow rate in cubic meters per hour
- **wärmeleser**:
  - Energy tariff 1, 2, 3 (MWh): Cumulative heat energy per tariff
  - Power (kW): Current thermal power
  - Total volume (m³): Cumulative volume of heating medium
  - Volume flow (l/h): Current flow rate of heating medium
  - Flow temperature (°C): Temperature of the incoming heating medium
  - Return temperature (°C): Temperature of the outgoing heating medium
  - Temperature difference (K): Difference between flow and return temperature
- **Common sensors**:
  - Signal strength (dBm): WiFi signal strength of the device

## Removing the integration

This integration follows standard integration removal. No extra steps are required.

{% include integrations/remove_device_service.md %}
