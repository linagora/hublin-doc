---
title: Janus Gateway
category: Getting started
order: 4
---

* Here is the ToC, this line is needed to generate...
{:toc}

Hublin can be configured to use the [Janus WebRTC Gateway](https://janus.conf.meetecho.com/) to provide more scalability and advanced features. The goal of the current page is to show how to configure Hublin to use Janus. For instructions on how to install and manage Janus, please refer to the Janus documentation or use our [Docker images]({{ site.baseurl }}{% link _docs/getting-started/docker.md %}).

## Configuration

### Local configuration

As described in the [adapters page]({{ site.baseurl }}{% link _docs/getting-started/adapters.md %}), Hublin provides a Janus adapter which can be activated from configuration files:

In `config/default.json`

**1.** set the `webrtc.adapter` value to `hublin.janus.connector`:

```
  "webrtc": {
    "enabled": true,
    "level": "debug",
    "roomNameRegExp": "^.{1,64}$",
    "usernameRegExp": "^(.){1,200}$",
    "adapter": "hublin.janus.connector"
  }
```

**2.** Load the adapter by adding it to the list of modules (replace the `hublin.easyrtc.connector` one by `hublin.janus.connector`):

```
  "modules": [
    "linagora.io.meetings",
    "linagora.esn.yjs-chat",
    "linagora.esn.yjs",
    "linagora.esn.conference.email-invitation",
    "hublin.janus.connector"
  ]
```

### Global configuration

If Janus server is running on the same host as Hublin and on default ports, you have probably nothing to do. If not, you have to tell Hublin and the Web clients where is the Janus endpoint. This is possible by setting configuration in the global configuration (MongoDB `configuration` collection as described [here]({{site.baseurl}} {% link _docs/getting-started/configuration.md %}))

``` javascript
{
    "_id" : "scalability",
    "configuration" : [
        {
            "type": "janus",
            "url" : "http://yourjanushost:8088"
        }
    ]
}
```

or if over HTTPs (recommended)

``` javascript
{
    "_id" : "scalability",
    "configuration" : [
        {
            "type": "janus",
            "url" : "https://yourjanushost:8089"
        }
    ]
}
```

## Run

Once Janus is running, you can start Hublin as usual

``` sh
npm start
```
