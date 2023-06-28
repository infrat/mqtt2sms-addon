# MQTT2SMS Broker Add-on for Home Assistant

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports i386 Architecture][i386-shield]


The SMS Modem MQTT Broker Add-on allows you to integrate the [SMS Modem MQTT Broker for Node.js](https://github.com/infrat/mqtt2sms-broker) into your Home Assistant installation. It provides seamless communication between MQTT clients and devices equipped with SMS modems, enabling bidirectional control and monitoring of your SMS-enabled devices.

**This add-on is configured by default to work with the control panel of the Polish manufacturer Satel Perfecta 16, but with little effort it can be used to control any device that provides an SMS interface.**

Look on how it works with Satel Perfecta 16 WRL:
https://www.youtube.com/shorts/O_2iIL2zDMQ

[![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Finfrat%2Fmqtt2sms-addon)
## Features

- **Home Assistant Integration**: This add-on is designed to be compatible with Home Assistant, a popular open-source home automation platform. It can be easily installed and managed using the Home Assistant Supervisor.

- **SMS Modem MQTT Broker**: The add-on wraps the [SMS Modem MQTT Broker for Node.js](https://github.com/infrat/mqtt2sms-broker), allowing you to control and monitor devices via SMS commands and states using MQTT. It provides a reliable and efficient messaging interface for your SMS-enabled devices.

- **Easy Configuration**: The add-on provides a user-friendly configuration interface within Home Assistant. You can easily set up MQTT parameters, SMS modem settings, and authentication options to suit your specific requirements.

- **Flexible Topic Structure**: The MQTT broker supports a flexible topic structure, allowing you to organize your MQTT topics hierarchically to reflect your device hierarchy or any other logical grouping.

- **Secure Communication**: The add-on supports authentication and encryption options to ensure secure communication between MQTT clients and the SMS modems. You can configure authentication credentials and enable TLS encryption as needed.

- **Scalability and Reliability**: The add-on is designed to handle a large number of MQTT clients and devices, leveraging the scalability and reliability of the underlying SMS Modem MQTT Broker for Node.js.

## Installation and Usage

To install and use the SMS Modem MQTT Broker Add-on in Home Assistant, you can follow these steps:

### Prerequisites

- A running instance of Home Assistant with Supervisor.
- USB GSM modem plugged and recognized by your host (see [GSM modem + SIM card](https://github.com/infrat/mqtt2sms-broker/blob/master/docs/installation.md#gsm-modem--sim-card))

### Installation Steps

1. Open your Home Assistant.

2. Go to your Home Assistant settings

3. In the settings, click on 'Add-ons' item.

4. Go to 'Add-on Store' (bottom right)

5. Look for three vertical dots (top right), click on them and select 'Repositories'

6. In the bottom enter the following repository URL: `https://github.com/infrat/mqtt2sms-addon`.

7. Click 'Add' to add the repository.

8. Close the repository dialog.

9. In the Add-ons page, you should now see the 'MQTT2SMS Broker Addon' add-on listed.

10. Click on the 'MQTT2SMS Broker' add-on.

11. Click on the 'INSTALL' button to install the add-on.

12. Wait for the installation to complete. This may take a few moments.

13. Once the installation is finished, you can configure the add-on by clicking on the 'CONFIGURE' tab.

14. Enter the required configuration parameters. The most of configuration params can be left with their default values. The only two you need to setup are 'Alarm SMS number' which should be set to you Alarm Panel GSM number, and 'Gammu device path' which should be set to your GSM modem device (usually it's something like `/dev/ttyUSB0` or `/dev/ttyUSB1`)

15. After configuring the add-on, click on 'SAVE' to apply the changes.

### Starting and Managing the Add-on

1. After saving the configuration, go back to the add-on details page.

2. Click on the 'START' button to start the MQTT2SMS Broker add-on.

3. Monitor the add-on logs to ensure everything starts up correctly and there are no errors.

4. You can access the add-on logs by clicking on the 'LOGS' tab.

### Integration with Home Assistant

1. With the add-on running, you can now integrate your SMS-enabled devices with Home Assistant.

2. In your Home Assistant configuration, add the MQTT broker as an integration using the configured MQTT parameters.

3. Configure your devices to communicate with the MQTT broker using the appropriate MQTT topics and messages for control and status reporting.

4. Enjoy controlling and monitoring your SMS-enabled devices through Home Assistant!

### Default configuration supporting Satel Perfecta Alarm Panel
If you want to use this Add-on with its default configuration to integrate your Home Assistant with Satel Perfecta Alarm panel, add following configuration to your `configuration.yaml`
``` yaml
mqtt:
  alarm_control_panel:
    - state_topic: "home/alarm"
      command_topic: "home/alarm/set"
      code: 1234    
```
Also you need to configure you Perfecta to allow SMS commands that are sent from this integration. More details you can see in [Satel Perfecta setup](https://github.com/infrat/mqtt2sms-broker/blob/master/docs/installation.md#satel-perfecta-setup).

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg