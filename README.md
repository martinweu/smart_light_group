# SmartLightGroup
A Light group component for automating the control of the Ambilight+hue setting on a Philips TV, this reveals the current status of the menu setting to Home Assistant, and allows for remote or automated toggling.
## Installation

#### Option 1: (recommended)
This repository is compatible with the Home Assistant Community Store ([HACS](https://community.home-assistant.io/t/custom-component-hacs/121727)).

After installing HACS, install 'SmartGroup' from the store, and use the ```configuration.yaml``` example below.

#### Option 2: (manual)
If you have already set up the [Ambilight (Light) component](https://github.com/jomwells/ambilights), installing this component is very simple, copy the ```philips_ambilight+hue``` directory into your ```config/custom_components/``` directory,
enter the same username and password as for the ambilight component in the configuration.yaml, along with the IP of the TV, and restart home assistant:

If you have not setup any other Philips TV components, use the tool linked in the Ambilight (Light) component docs to obtain your username and password.
```
light:
  - platform: smart_light_group
    name: Ambilight+Hue
    host: 192.168.1.XXX
    username: !secret philips_username
    password: !secret philips_password
    id: 2131230774 # ambilight_hue_off node id. Default is 2131230774, but some newer TVs use 2131230778 instead.
    scan_interval: 5
```

If the component is not working, try setting `2131230778` as the `id` in the config 

*note:* there is often a noticeable lag between Home Assistant sending the request to toggle the setting, and receiving a status update from the API, for this reason, it is advised that you reduce your `scan_interval` (in seconds) to suit your needs.

