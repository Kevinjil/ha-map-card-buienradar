# `ha-map-card` Buienradar plugin
![image](./preview/2025-01-26_v0.2.0.gif)


## Installation
Install [ha-map-card](https://github.com/nathan-gs/ha-map-card) version `v1.13.0` or above.
Then, install the plugin using one of these options:

#### HACS

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=kevinjil&repository=ha-map-card-buienradar&category=plugin)

#### Manual
Copy `ha-map-card-buienradar.js` to the `www` folder of your Home Assistance configuration.

## Configuration
Add the [ha-map-card](https://github.com/nathan-gs/ha-map-card) custom card to your Home Assistant dashboard.

| Option                   | Description                                                                    |
| ------------------------ | ------------------------------------------------------------------------------ |
| `delaySeconds`           | The amount of seconds between every sprite image.                              |
| `imageRange.forecast`    | The amount of forecast images after the current time to fetch.                 |
| `imageRange.history`     | The amount of historic images before the current time to fetch.                |
| `imageRange.skip`        | The amount of 5-minute intervals to skip between every image fetched.          |
| `opacity`                | The opacity of the image overlay.                                              |
| `refreshSeconds`         | The amount of seconds between fetching new image data.                         |

Use the following configuration as example:
```yaml
type: custom:map-card
card_size: 8
focus_entity: zone.home
zoom: 7
tile_layer_url: https://basemaps.cartocdn.com/rastertiles/voyager/{z}/{x}/{y}.png
tile_layer_attribution: >-
  &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>,
  &copy; <a href="https://carto.com/attributions">CARTO</a>,
  &copy; <a href="https://www.buienradar.nl">Buienradar.nl</a>
entities:
  - entity: zone.home
    display: icon
    size: 15
plugins:
  - name: buienradar
    hacs:
      module: ha-map-card-buienradar
      file: ha-map-card-buienradar.js
    options:
      delaySeconds: 0.75
      imageRange:
        forecast: 36
        history: 4
        skip: 0
      opacity: 0.7
      refreshSeconds: 300
```

Note: with a manual installation, use the following as base configuration for the plugin:
```yaml
  - name: buienradar
    url: /local/ha-map-card-buienradar.js
    options:
      ...
```
