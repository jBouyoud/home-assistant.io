---
layout: page
title: "PiFace Digital I/O Binary Sensor"
description: "Instructions on how to integrate the PiFace Digital I/O module into Home Assistant as a binary sensor."
date: 2016-05-08 15:00
sidebar: true
comments: false
sharing: true
footer: true
logo: raspberry-pi.png
ha_category: DIY
ha_release: 0.45
ha_iot_class: "Local Push"
---

The `rpi_pfio` binary sensor platform allows you to read sensor values of the [PiFace Digital I/O](http://www.piface.org.uk/products/piface_digital/) .

## {% linkable_title Configuration %}

To use your PiFace Digital I/O module in your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
binary_sensor:
  - platform: rpi_pfio
    ports:
      0:
        name: PIR Office
        invert_logic: true
      1:
        name: Doorbell
        settle_time: 50
```

{% configuration %}
ports:
  description: List of used ports.
  required: true
  type: map
  keys:
    num:
      description: The port number.
      required: true
      type: map
      keys:
        name:
          description: The port name.
          required: true
          type: string
        settle_time:
          description: The time in milliseconds for port debouncing.
          required: false
          type: integer
          default: 20
        invert_logic:
          description: If `true`, inverts the output logic to ACTIVE LOW.
          required: false
          type: boolean
          default: "`false` (ACTIVE HIGH)"
{% endconfiguration %}
