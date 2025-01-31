---
layout: article
title: Sharing links
permalink: /user-guide/tokens/sharing-links.html
image: https://dytvr9ot2sszz.cloudfront.net/logz-docs/social-assets/docs-social.jpg
description: Learn how to use shared tokens to share dashboards and visualizations
flags:
  logzio-plan: community
tags:
  - tokens
  - shared-tokens
contributors:
  - shalper
---

You can use shared tokens to share OpenSearch dashboards and visualizations with
stakeholders who don't have access to your Logz.io account.

This can be useful for communicating with clients outside your organization or internally with other teams in your organization.

#### Sharing dashboards

<div class="tasklist">

##### Decide what to share

Open the dashboard you would like to share.
When you share a dashboard, you can decide whether to share the dashboard with a relative or fixed timeframe.

* **Snapshot** - Converts the time selection to absolute dates. Your recipients will view the same data you are viewing now. For example, if you send out a snapshot when viewing the dashboard for the last 24 hours, your recipients will receive the dashboard with a fixed date range selection.

  Of course, this type of permalink is short lived, as it depends on your log retention policy. Once the logs are too old, they will no longer feed the dashboard and your recipients won't have anything to see.

* **Saved object** - Shares the dashboard with a relative time selection.

  The permalink will load the dashboard with its default time selection and filters. For example, if the dashboard is set for the last 15 minutes, this is the time frame your recipients will also review.

  This option means the sharing link will automatically be updated to reflect any changes made to the dashboard in the future. So if someone saves changes to the dashboard after the sharing link was sent out, your recipients will see the updated version without you having to resend them a new link.

<!-- <video autoplay loop>
  <source src="https://dytvr9ot2sszz.cloudfront.net/logz-docs/dashboards/share-permalink_aug2021.mp4" type="video/mp4" />
</video> -->

![Share your dashboard](https://dytvr9ot2sszz.cloudfront.net/logz-docs/kibana/dashboard-to-share.gif)


##### What your recipients will see

When you choose to **Share Public**, your recipients will receive a link to the dashboard you've shared with them. The dashboard will appear without the top and side navigation bars, and without the OpenSearch Dashboards time filtering options.

However, you can edit the link to **include the time frame** by adding the following string to the end of the link:

`&forceShowQueryBar=true`

For example, if your public link is:

`https://app.logz.io/?embed=true&shareToken=8d90-fbe1c84836d3#/dashboard/kibana/discover/?=&_a=(columns%3A!(message)%2Cfilters%3A!()%2Cindex%3A'logzioCustomerIndex*'%2Cinterval%3Aauto%2Cquery%3A(language%3Alucene%2Cquery%3A'')%2Csort%3A!())&_g=(filters%3A!()%2CrefreshInterval%3A(pause%3A!t%2Cvalue%3A0)%2Ctime%3A(from%3Anow-15m%2Cto%3Anow))`

This is how users will see it:

![public share no time](https://dytvr9ot2sszz.cloudfront.net/logz-docs/sharing-logs/share-public-link.png)


When you add the time frame string to the end of the URL, it changes the view and includes the time frame and search abilities:


`https://app.logz.io/?embed=true&shareToken=8d90-fbe1c84836d3#/dashboard/kibana/discover/?=&_a=(columns%3A!(message)%2Cfilters%3A!()%2Cindex%3A'logzioCustomerIndex*'%2Cinterval%3Aauto%2Cquery%3A(language%3Alucene%2Cquery%3A'')%2Csort%3A!())&_g=(filters%3A!()%2CrefreshInterval%3A(pause%3A!t%2Cvalue%3A0)%2Ctime%3A(from%3Anow-15m%2Cto%3Anow))&forceShowQueryBar=true`

![public share with time](https://dytvr9ot2sszz.cloudfront.net/logz-docs/sharing-logs/share-with-time.png)



##### Testing your permalink

You can open your sharing link in an incognito browser window to test it and verify it's working.
