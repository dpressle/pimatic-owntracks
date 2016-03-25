
# pimatic-owntracks

Pimatic Plugin for <a href="http://owntracks.org/">OwnTracks</a> location tracking app

## Status of implementation

This version supports the following

* PresenceSensor

## Getting Started

This section is still work in progress.

## Plugin Configuration

After setup MQTT broker, you can load the plugin by editing your `config.json` to include the following
in the `plugins` section.

    {
        "plugin": "owntracks"
    }

Full config

    {
      "plugin": "owntracks",
      "host": "127.0.0.1",
      "port": 1883,
      "username": "",
      "password": ""
    }

The configuration for a broker is an object comprising the following properties.

| Property  | Default     | Type    | Description                                                                           |
|:----------|:------------|:--------|:--------------------------------------------------------------------------------------|
| host      | "127.0.0.1" | String  | Broker hostname or IP                                                                 |
| port      | 1883        | integer | Broker port                                                                           |
| username  | -           | String  | The login name                                                                        |
| password  | -           | String  | The Password                                                                          |


## Device Configuration

Devices must be added manually to the device section of your pimatic config.

### Owntracks Presence Sensor

'OwntracksDevice' is a device based on the `PresenceSensor` device class.

    {
      "name": "My Phone",
      "id": "my-iphone",
      "class": "OwntracksDevice",
      "topic": "owntracks/my-phone/iphone",
      "lat": 33.19469267,
      "long": 35.65596431,
      "radius": 100
    }

It has the following configuration properties:

| Property   | Default  | Type    | Description                                 |
|:-----------|:---------|:--------|:--------------------------------------------|
| topic      | -        | String  | Topic for device state                      |
| lat        | 0        | Number  | latitude value                              |
| long       | 0        | Number  | longitude value                             |
| radius     | 0        | Integer | The radius in meters                        |

The presence sensor exhibits the following attributes:

| Property      | Unit  | Type    | Acronym | Description                                      |
|:--------------|:------|:--------|:--------|:-------------------------------------------------|
| presence      | -     | Boolean | -       | Presence State, true is present, false is absent |

The following predicates are supported:

* {device} is present|absent

##Rules example

* if {device} is presence then switch the {switch device} on

## Configure OwnTracks

<a href="http://owntracks.org/booklet/">owntracks documentation</a>

## Credits

<a href="https://github.com/wutu/">wutu</a> for his module <a href="https://github.com/wutu/pimatic-mqtt">pimatic-mqtt</a> from which it comes also part of the mqtt code.

<a href="https://github.com/Oitzu/">Oitzu</a> for for his module <a href="https://github.com/Oitzu/pimatic-location">pimatic-location</a> from which it comes also part of the presence code.
