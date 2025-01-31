---
title: Ship logs from Aiven
logo:
  logofile: aiven-logo.png
  orientation: vertical
data-source: Aiven
data-for-product-source: Logs
templates: ["network-device-filebeat"]
contributors:
  - nshishkin
shipping-tags:
  - popular
order: 1380
---
[Aiven](https://aiven.io/) provides managed open source data technologies on all major clouds. This topic describes how to configure Aiven to send system logs to Logz.io. 

**Before you begin, you'll need**: 

* an active account with Logz.io
* an Aiven project with the service enabled 

<div class="tasklist">


##### Configure Aiven to send syslog notifications to Logz.io

1. Log in to your Aiven account and navigate to **Projects**.
2. Select the project that you need to send logs from.
3. Navigate to **Integration Endpoints**.
4. Select **Syslog** and click **Create new**.
   ![1](https://dytvr9ot2sszz.cloudfront.net/logz-docs/aiven/aiven1.png)
5. Fill out the parameters as follows:
   ![2](https://dytvr9ot2sszz.cloudfront.net/logz-docs/aiven/aiven2.png)
   * Endpoint name: Logz.io 
   * Server: The Logz.io listener URL: `https://<<LISTENER-HOST>>:8071` {% include log-shipping/listener-var.html %} 
   * Port: 5001 
   * Format: custom
   * Log Template: 

   ```shell
   <<LOG-SHIPPING-TOKEN>> <%pri%>%protocol-version% %timestamp:::date-rfc3339% %HOSTNAME% %app-name% %procid% %msgid% [type=Aiven] %msg%\n
   ```
   {% include log-shipping/log-shipping-token.html %}  |

   * PEM encoded CA certificate: 

   ```shell
   -----BEGIN CERTIFICATE-----
   MIIEMjCCAxqgAwIBAgIBATANBgkqhkiG9w0BAQUFADB7MQswCQYDVQQGEwJHQjEb
   MBkGA1UECAwSR3JlYXRlciBNYW5jaGVzdGVyMRAwDgYDVQQHDAdTYWxmb3JkMRow
   GAYDVQQKDBFDb21vZG8gQ0EgTGltaXRlZDEhMB8GA1UEAwwYQUFBIENlcnRpZmlj
   YXRlIFNlcnZpY2VzMB4XDTA0MDEwMTAwMDAwMFoXDTI4MTIzMTIzNTk1OVowezEL
   MAkGA1UEBhMCR0IxGzAZBgNVBAgMEkdyZWF0ZXIgTWFuY2hlc3RlcjEQMA4GA1UE
   BwwHU2FsZm9yZDEaMBgGA1UECgwRQ29tb2RvIENBIExpbWl0ZWQxITAfBgNVBAMM
   GEFBQSBDZXJ0aWZpY2F0ZSBTZXJ2aWNlczCCASIwDQYJKoZIhvcNAQEBBQADggEP
   ADCCAQoCggEBAL5AnfRu4ep2hxxNRUSOvkbIgwadwSr+GB+O5AL686tdUIoWMQua
   BtDFcCLNSS1UY8y2bmhGC1Pqy0wkwLxyTurxFa70VJoSCsN6sjNg4tqJVfMiWPPe
   3M/vg4aijJRPn2jymJBGhCfHdr/jzDUsi14HZGWCwEiwqJH5YZ92IFCokcdmtet4
   YgNW8IoaE+oxox6gmf049vYnMlhvB/VruPsUK6+3qszWY19zjNoFmag4qMsXeDZR
   rOme9Hg6jc8P2ULimAyrL58OAd7vn5lJ8S3frHRNG5i1R8XlKdH5kBjHYpy+g8cm
   ez6KJcfA3Z3mNWgQIJ2P2N7Sw4ScDV7oL8kCAwEAAaOBwDCBvTAdBgNVHQ4EFgQU
   oBEKIz6W8Qfs4q8p74Klf9AwpLQwDgYDVR0PAQH/BAQDAgEGMA8GA1UdEwEB/wQF
   MAMBAf8wewYDVR0fBHQwcjA4oDagNIYyaHR0cDovL2NybC5jb21vZG9jYS5jb20v
   QUFBQ2VydGlmaWNhdGVTZXJ2aWNlcy5jcmwwNqA0oDKGMGh0dHA6Ly9jcmwuY29t
   b2RvLm5ldC9BQUFDZXJ0aWZpY2F0ZVNlcnZpY2VzLmNybDANBgkqhkiG9w0BAQUF
   AAOCAQEACFb8AvCb6P+k+tZ7xkSAzk/ExfYAWMymtrwUSWgEdujm7l3sAg9g1o1Q
   GE8mTgHj5rCl7r+8dFRBv/38ErjHT1r0iWAFf2C3BUrz9vHCv8S5dIa2LX1rzNLz
   Rt0vxuBqw8M0Ayx9lt1awg6nCpnBBYurDC/zXDrPbDdVCYfeU0BsWO/8tqtlbgT2
   G9w84FoVxp7Z8VlIMCFlA2zs6SFz7JsDoeA3raAVGI/6ugLOpyypEBMs1OUIJqsi
   l2D4kF501KKaU73yqWjgom7C12yxow+ev+to51byrvLjKzg6CYG1a4XXvi3tPxq3
   smPi9WIsgtRqAEFQ8TmDn5XpNpaYbg==
   -----END CERTIFICATE-----
   ```

6. Click **Create**.
7. Navigate to **Services** and select the service that you need to send logs from.
   ![3](https://dytvr9ot2sszz.cloudfront.net/logz-docs/aiven/aiven3.png)
8. Select **Set up integration**.
   ![4](https://dytvr9ot2sszz.cloudfront.net/logz-docs/aiven/aiven4.png)
9. Scroll down to **Rsyslog** and select **Use integration**.
   ![5](https://dytvr9ot2sszz.cloudfront.net/logz-docs/aiven/aiven5.png)
10. Select **Logz.io** from the **Endpoint name** menu.
   ![6](https://dytvr9ot2sszz.cloudfront.net/logz-docs/aiven/aiven6.png)
11. Click **Enable**. The integration status will appear on the screen.
   ![7](https://dytvr9ot2sszz.cloudfront.net/logz-docs/aiven/aiven7.png)


##### Check Logz.io for your logs

Give your logs some time to get from your system to ours, and then open [Kibana](https://app.logz.io/#/dashboard/kibana/discover?). You can filter for data of type `Aiven` to see the incoming Aiven logs.
  
If you still don't see your logs, see [log shipping troubleshooting](https://docs.logz.io/user-guide/log-shipping/log-shipping-troubleshooting.html).


</div>
 
