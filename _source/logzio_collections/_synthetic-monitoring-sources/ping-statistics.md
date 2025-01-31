---
title: Sending ping statistics metrics from web addresses
logo:
  logofile: ping-logo.png
  orientation: vertical
data-source: Ping statistics
data-for-product-source: Synthetic monitoring
open-source:
  - title: Logzio ping statistics
    github-repo: logzio-ping-statistics
templates: ["network-device-filebeat"]
contributors:
  - nshishkin
shipping-tags:

order: 1380
---

### Overview

Deploy this integration to collect metrics of ping statistics collected from your preferred web addresses and send them to Logz.io.

The integration is based on a Lambda function that will be auto-deployed together with the layer [LogzioLambdaExtensionLogs](https://github.com/logzio/logzio-lambda-extensions/tree/main/logzio-lambda-extensions-logs). 


<!-- logzio-inject:install:grafana:dashboards ids=["1rNO8llFw8Cm9N8U3M3vCQ"] --> 


<div class="tasklist">

##### Auto-deploy the Lambda function

👇 To begin, click this button to start the automated deployment. You will need to deploy it in your environment.

[![Deploy to AWS](https://dytvr9ot2sszz.cloudfront.net/logz-docs/lights/LightS-button.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/template?templateURL=https://logzio-aws-integrations-us-east-1.s3.amazonaws.com/ping-statistics-auto-deployment/auto-deployment.yaml&stackName=logzio-ping-statistics-auto-deployment)


##### Specify the template

![Specify stack template](https://dytvr9ot2sszz.cloudfront.net/logz-docs/ping_statistics/Template.png)

Keep the defaults and click **Next**.


##### Specify the stack details

![Specify stack details](https://dytvr9ot2sszz.cloudfront.net/logz-docs/ping_statistics/Stack_details1.png)

Specify the stack details as per the table below and select **Next**.


| Parameter | Description | Required/Optional | Default |
| --- | --- | --- | --- |
| Addresses | The addresses to ping. You can add port for each address (default port for the address is 80). Addresses must be separated by comma. (Example addresses: `www.google.com`, `tcp://www.google.com`, `https://www.google.com`, `http://www.google.com`). | Required | - |
| LogzioListener | The Logz.io listener URL: `https://<<LISTENER-HOST>>:8071` {% include log-shipping/listener-var.html %} | Required | `https://listener.logz.io` |
| LogzioLogsToken | Your Logz.io log shipping token:`<<LOG-SHIPPING-TOKEN>>` {% include log-shipping/log-shipping-token.html %} | Required | - |
| LogzioMetricsToken | Your Logz.io metrics shipping token:`<<PROMETHEUS-METRICS-SHIPPING-TOKEN>>` | Required | - |
| PingCount | The number of pings for each address. | Required | `3` |
| PingInterval | The time to wait (in seconds) between each ping. | Required | `1 (second)` |
| PingTimeout | The timeout (in seconds) for each ping. | Required | `10 (seconds)` |
| SchedulingInterval | The scheduling expression that determines when and how often the Lambda function runs. | Required | `rate(30 minutes)` |


##### Configure the stack options

![Specify stack options](https://dytvr9ot2sszz.cloudfront.net/logz-docs/ping_statistics/Stack_option.png)

Keep the defaults and click **Next**.

##### Review the deployment

Confirm that you acknowledge that AWS CloudFormation might create IAM resources and select **Create stack**.


##### Run the tests

Run the ping statistics tests to generate metrics.


##### Check Logz.io for your metrics

Give your metrics some time to get from your system to ours, and then open [Kibana](https://app.logz.io/#/dashboard/kibana). All metrics that were sent from the Lambda function will have the prefix `ping_stats` in their name.

{% include metric-shipping/custom-dashboard.html %} Install the pre-built dashboard to enhance the observability of your metrics.

<!-- logzio-inject:install:grafana:dashboards ids=["1rNO8llFw8Cm9N8U3M3vCQ"] --> 

{% include metric-shipping/generic-dashboard.html %} 

</div>

