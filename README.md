*Please :star: this repo if you find it useful*

<p align="left"><br>
<a href="https://paypal.me/eyalco1967?locale.x=he_IL" target="_blank"><img src="http://khrolenok.ru/support_paypal.png" alt="PayPal" width="250" height="48"></a>
</p>

# Read Your Meter

The read your meter integration can be used to read your house water consumption and hopefully will enable you to save water and to early detect water leaks.

![Heat Map](./docs/water_meter.jpg)

There is currently support for the following device types within Home Assistant:

- [Sensor](#sensor)

## Requirements

For the integration to work, you need the following:

- Account in read your meter
- Selenuim standalone chrome running on same device as Home Assistant.

### Install Selenuim

For installing [Sellenuim](https://www.selenium.dev/) please refere to the [offical documentation](https://www.selenium.dev/documentation/en/selenium_installation).

If you want to run the Sellenuim on Raspbery Pi, you can use the following command to download and start container with the following command:

```
docker run -d -p 4444:4444 --name selenium chadbutz/rpi-selenium-standalone-chrome
```

or with docker-compose

```
version: '2.1'

services:

  selenuim:
    image: chadbutz/rpi-selenium-standalone-chrome
    container_name: selenuim
    ports:
      - 4444:4444
    restart: unless-stopped
```

### MANUAL INSTALLATION

1. Download the `read_your_meter.zip` file from the
   [latest release](https://github.com/eyalcha/read_your_meter/releases/latest).
2. Unpack the release and copy the `custom_components/read_your_meter` directory
   into the `custom_components` directory of your Home Assistant
   installation.
3. Configure the `read_your_meter` integration.
4. Restart Home Assistant.

### INSTALLATION VIA HACS

1. Ensure that [HACS](https://custom-components.github.io/hacs/) is installed.
2. Search for and install the "thermal" integration.
3. Configure the `read_your_meter` integration.
4. Restart Home Assistant.

## Configuration

To enable this integration with the default configuration, add the following lines to your configuration.yaml file:

```yaml
read_your_meter:
  host: Selenuim host url
  username: Account user name
  password: Account password
```

|Parameter |Required|Description
|:---|---|---
| `host` | Yes | Selenuim url (path & port)
| `username` | Yes | Account username
| `password` | Yes | Account password
| `name` | No |  NOT SUPPORTED YET Sensors prefix **Default** Read your meter
| `scan_interval` | No | NOT SUPPORTED YET **Default**: 1800 sec

Here is an example for a configuration:

```yaml
# Example configuration.yaml entry

read_your_meter
  host: http://localhost:4444
  username: john.brinston@gmail.com
  password: verycomplicatedpassword
```

## Sensors

### `sensor.read_your_meter`

```
state: Total water consumption

attributes:
	meter_number: Meter number
```

### `sensor.read_your_meter_daily`

```
state: Total water consumption daily

attributes:
	reading_state: E.g., approximate etc.
```

### `sensor.read_your_meter_monthly`

```
state: Total water consumption monthly

attributes:
	reading_state: E.g., approximate etc.
```

# Services

TBI

---

I put a lot of work into making this repo and component available and updated to inspire and help others! I will be glad to receive thanks from you — it will give me new strength and add enthusiasm:
<p align="center"><br>
<a href="https://paypal.me/eyalco1967?locale.x=he_IL" target="_blank"><img src="http://khrolenok.ru/support_paypal.png" alt="PayPal" width="250" height="48"></a>
</p>