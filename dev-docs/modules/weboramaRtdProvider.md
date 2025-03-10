---
layout: page_v2
title: Weborama Real Time Data Provider
display_name: Weborama Real-time Segmentation Module
description: Weborama Real-time Segmentation Module
page_type: module
module_type: rtd
module_code : weboramaRtdProvider
enable_download : true
vendor_specific: true
sidebarType : 1
---

# Weborama RTD Segmentation Module
{:.no_toc}

* TOC
{:toc}

Weborama provides a Semantic AI Contextual API that classifies in Real-time a web page seen by a web user within generic and custom topics. It enables publishers to better monetize their inventory and unlock it to programmatic.

ORTB2 compliant and FPD support for Prebid versions < 4.29

Please contact prebid-support@weborama.com for more information.

## Publisher Usage

### Configure Prebid.js

Compile the Weborama RTD module into your Prebid build:

`gulp build --modules=rtdModule,weboramaRtdProvider`

Add the Weborama RTD provider to your Prebid config.


#### Minimal configuration

```
pbjs.setConfig(
    ...
    realTimeData: {
        auctionDelay: 1000,
        dataProviders: [
            {
                name: "weborama",
                waitForIt: true,
                params: {
			token: "<token-provided-by-weborama>"
                }
            }
        ]
    }
    ...
);
```

### Parameter Descriptions for the Weborama Configuration Section

| Name  |Type | Description   | Notes  |
| :------------ | :------------ | :------------ |:------------ |
| name | String | Real time data module name | Mandatory. Always 'Weborama' |
| waitForIt | Boolean | Mandatory. Required to ensure that the auction is delayed until prefetch is complete | Optional. Defaults to false but recommended to true |
| params | Object | | Optional |
| params.weboCtxConf | Object | Weborama Contextual Configuration | Optional |
| params.weboCtxConf.token | String | Security Token provided by Weborama, unique per client | Mandatory |
| params.weboCtxConf.targetURL | String | Url to be profiled in the contextual api | Optional. Defaults to `document.URL` |
| params.weboCtxConf.defaultProfile | Object | default value of the profile to be used when there are no response from contextual api (such as timeout)| Optional. Default is `{}` |
| params.weboCtxConf.setTargeting|Boolean|If true, will use the contextual profile to set the gam targeting of all adunits managed by prebid.js| Optional. Default is *true*.|
| params.weboCtxConf.setOrtb2|Boolean|If true, will use the contextual profile to set the ortb2 configuration on `site.ext.data`| Optional. Default is *false*.|


### Testing

To view an example of available segments returned by Weborama's backends:

`gulp serve --modules=rtdModule,weboramaRtdProvider,appnexusBidAdapter`

and then point your browser at:

`http://localhost:9999/integrationExamples/gpt/weboramaRtdProvider_example.html`
