---
title: Ship Synproxy metrics via Telegraf
logo:
  logofile: linux.svg
  orientation: vertical
data-source: Synproxy 
data-for-product-source: Metrics
templates: ["docker"]
contributors:
  - daniel-tk
  - nshishkin
shipping-tags:  
  - prometheus
order: 800
---


## Overview

Synproxy is a TCP SYN packets proxy. Telegraf is a plug-in driven server agent for collecting and sending metrics and events from databases, systems and IoT sensors.

To send your Prometheus-format Synproxy metrics to Logz.io, you need to add the **inputs.synproxy** and **outputs.http** plug-ins to your Telegraf configuration file.

#### Configuring Telegraf to send your metrics data to Logz.io

<div class="tasklist">

##### Set up Telegraf v1.17 or higher

**Ubuntu & Debian**

```shell
sudo apt-get update && sudo apt-get install telegraf
```

The configuration file is located at `/etc/telegraf/telegraf.conf`.

**RedHat and CentOS**

```shell
sudo yum install telegraf
```

The configuration file is located at `/etc/telegraf/telegraf.conf`.

**SLES & openSUSE**

```shell
# add go repository
zypper ar -f obs://devel:languages:go/ go
# install latest telegraf
zypper in telegraf
```

The configuration file is located at `/etc/telegraf/telegraf.conf`.

**FreeBSD/PC-BSD**

```shell
sudo pkg install telegraf
```

The configuration file is located at `/etc/telegraf/telegraf.conf`.
  

##### Add the inputs.Synproxy plug-in

First you need to configure the input plug-in to enable Telegraf to scrape the Synproxy data from your hosts. To do this, add the following code to the configuration file:

``` ini
[[inputs.synproxy]]
  # no configuration
```

<!-- info-box-start:info -->
The full list of data scraping and configuring options can be found [here](https://github.com/influxdata/telegraf/blob/release-1.18/plugins/inputs/synproxy/README.md)
{:.info-box.note}
<!-- info-box-end -->

##### Add the outputs.http plug-in
  
{% include metric-shipping/telegraf-outputs.md %}
{% include general-shipping/replace-placeholders-prometheus.html %}

##### Start Telegraf  
  
**Linux (sysvinit and upstart installations)**

```shell
sudo service telegraf start
```

**Linux (systemd installations)**

```shell
systemctl start telegraf
```  
  
##### Check Logz.io for your metrics

Give your data some time to get from your system to ours, then log in to your Logz.io Metrics account, and open [the Logz.io Metrics tab](https://app.logz.io/#/dashboard/metrics/).


</div>
