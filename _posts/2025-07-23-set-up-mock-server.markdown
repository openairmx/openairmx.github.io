---
layout: post
title:  "Set up a mock server"
date:   2025-07-23 09:06:41 +0800
---

When setting up or pairing your AIRMX Pro with our [setup page][setup-page],
it's important to first configure [the mock API server][server]. This is
necessary because when your device receives the Wi-Fi credentials during
the process, it attempts to connect to the internet and sends a device
registration request to _i.airmx.cn_ for identification.

Unfortunately, the endpoint is hardcoded in the firmware, and we cannot modify
it during the setup process. Therefore, we need to remap this domain name in
the upstream device—the router.

Since every router has a different configuration, you can consult your
router's manual or use an open-source DNS tool, or configure a DNAT rule
with IPTables. For instance, if you are using a router running on EdgeOS and
you have set up the mock server on your Raspberry Pi, which is accessible at
_192.168.10.10_, you can use the following commands:

{% highlight bash %}
set system static-host-mapping host-name i.airmx.cn inet 192.168.10.10
set system static-host-mapping host-name mqtt.airmx.cn inet 192.168.10.10
{% endhighlight %}

It's essential to also configure _mqtt.airmx.cn_, as this is the domain name
for the MQTT broker that the device connects to after completing the
registration request. All device status updates and remote controls are
handled through this broker. Meanwhile, _i.airmx.cn_ is responsible for
processing device registration requests, and the device will periodically sync
the time with this endpoint.

I am using [Eclipse Mosquitto][mosquitto] as the MQTT broker and configuring
it for **anonymous** access since I only run it on my home network. Here’s the
configuration file `mosquitto.conf` that I use to start the service:

{% highlight conf %}
listener 1883
allow_anonymous true
{% endhighlight %}

Ensure that the network traffic from your AIRMX Pro and your computer is
routed through the configured router. You can test the DNS resolution using
the `ping` command:

{% highlight bash %}
ping i.airmx.cn
{% endhighlight %}

If the configuration is correct, you should see that the resolved IP address
is _192.168.10.10_ (replace with your local server's IP). Once confirmed, you
can return to [the setup page][setup-page] and continue pairing your device.


[setup-page]: https://github.com/openairmx/setup
[server]: https://github.com/openairmx/server
[mosquitto]: https://mosquitto.org
