---
layout: page
title: About
permalink: /about/
---

Hello! Welcome to Open AIRMX, a site dedicated to everything related to
AIRMX Pro.

This project originated from my desire to integrate the device with
Apple Home, enabling remote control. However, around mid-2024, an unexpected
issue arose when someone reported in the repository that the AIRMX company
had gone out of business. This created a challenge for users who needed to
retrieve the device’s key, as there was no way to access it with the official
servers down.

After an extensive investigation and reverse engineering of the AIRMX mobile
application, we were able to find a solution. We are excited to offer you the
ability to fully localize your device on your home network. Currently, we
provide dedicated repositories for:

- [A mock API server][mock-server] that handles device registration and
  time synchronization.
- [A setup page][setup-page] to assist you in pairing or reconnecting your
  device to the internet.
- [A JavaScript project][airmx] called [airmx][airmx] that allows you to
  control the device. This is a low-level package for composing and validating
  MQTT messages, making it ready for integration with various platforms.
- [A Homebridge plugin][homebridge-airmx] for AIRMX Pro, which enables you to
  control your device across your Apple devices, including via Siri.

The project scope has expanded significantly beyond our initial expectations.
We are open-source enthusiasts and do not have any affiliation with
AIRMX—The company. The project is managed by a software engineer and a
UI designer. If you appreciate our work, we would be grateful for your support
through GitHub Sponsors or PayPal. Your generosity means a lot to us.

If you have any questions or just want to say hello, please feel free to
send us a message at [hello@openairmx.org][contact-email].

[mock-server]: https://github.com/openairmx/server
[setup-page]: https://github.com/openairmx/setup
[airmx]: https://github.com/openairmx/airmx
[homebridge-airmx]: https://github.com/openairmx/homebridge-airmx
[contact-email]: mailto:hello@openairmx.org
