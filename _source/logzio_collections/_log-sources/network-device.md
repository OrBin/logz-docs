---
title: Ship logs from network devices
logo:
  logofile: network-device.svg
  orientation: horizontal
short-description: Configure your network device to send logs to your Filebeat server, which can then forward your logs to Logz.io.
data-source: Network device
data-for-product-source: Logs
templates: ["network-device-filebeat"]
contributors:
  - imnotashrimp
  - schwin007
shipping-tags:
  - server-app
order: 290
---
This integration allows you to send logs from your network devices to your Logz.io account. 

#### Guided configuration

**Before you begin, you'll need**:

* [Filebeat](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-installation.html) installed
* Root access

<div class="tasklist">

##### Configure your device

Configure your network device to send logs to your Filebeat server, TCP port 9000.
See your device's documentation if you're not sure how to do this.

{% include log-shipping/certificate.md %}

##### Add TCP traffic as an input

In the Filebeat configuration file (/etc/filebeat/filebeat.yml), add TCP to the filebeat.inputs section.

{% include log-shipping/log-shipping-token.html %}

{% include log-shipping/filebeat-input-extension.md %}


```yaml
# ...
filebeat.inputs:
- type: tcp
  max_message_size: 10MiB
  host: "0.0.0.0:9000"

  fields:
    logzio_codec: plain

    # You can manage your tokens at
    # https://app.logz.io/#/dashboard/settings/manage-tokens/log-shipping
    token: <<LOG-SHIPPING-TOKEN>>
    type: network-device
  fields_under_root: true
  encoding: utf-8
  ignore_older: 3h
```


##### Set Logz.io as the output

If Logz.io is not an output, add it now.
Remove all other outputs.

{% include log-shipping/listener-var.html %} 

```yaml
# ...
output.logstash:
  hosts: ["<<LISTENER-HOST>>:5015"]
  ssl:
    certificate_authorities: ['/etc/pki/tls/certs/COMODORSADomainValidationSecureServerCA.crt']
```

##### Start Filebeat

[Start or restart Filebeat](https://www.elastic.co/guide/en/beats/filebeat/master/filebeat-starting.html) for the changes to take effect.


##### Check Logz.io for your logs

Give your logs some time to get from your system to ours, and then open [Kibana](https://app.logz.io/#/dashboard/kibana).

If you still don't see your logs, see [Filebeat troubleshooting](https://docs.logz.io/shipping/log-sources/filebeat.html#troubleshooting).

</div> 
