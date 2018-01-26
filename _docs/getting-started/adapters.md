---
title: WebRTC Adapters
category: Getting started
order: 4
---

* Here is the ToC, this line is needed to generate...
{:toc}

## About

Hublin is built on top of a modular system where modules can be plugged on both frontend and backend sides to customize and add new features to the platform. **Adapters** are modules which are implementing the interface to manage communications between peers. Based on this modular system, we developped several connectors based on differents WebRTC clients to be able to provide features which best fit deployments and constraints:

- [hublin-easyrtc-connector](https://github.com/linagora/hublin-easyrtc-connector) is based on the [easyRTC](https://easyrtc.com/products/easyrtc/) library on both backend and frontend. It provides a fully P2P conference system.
- [hublin-janus-connector](https://github.com/linagora/hublin-janus-connector) is using [Janus WebRTC Gateway](https://janus.conf.meetecho.com/). It provides more features, allow more users to join a conference but is more complex to deploy and configure.

Both modules are available in the Hublin platform but they are not both activated/configured. You can choose the connector to use with local configuration as defined [here](/getting-started/configuration) and customize them as defined below.

## Using easyRTC

Once configured in the local configuration, there is nothing more to do! You should be able to create fully peer to peer videoconferences up to almost 6 attendees. This limitation is due to your current browser and machine since it will need to send and receive video and audio streams to all other peers.

If this number of attendees is too low, you should consider deploying a solution based on Janus adapter as described below.

## Using Janus

Using Janus adapter is more complex but provides more features and more attendees. This comes from the fact that Janus will act as a 'gateway' to avoid to create as many streams as there are attendees in the conference.

### Installation

Janus adapter is already provided in Hublin. you 'just' have to define that you want to use it from [local configuration](/getting-started/configuration).

Instructions to install Janus are out of scope, please refer to the official Janus documentation for this or use [Docker and our Janus image](/getting-started/docker).

### Configuration

Hublin will need to know the endpoint to reach to contact the Janus instance. If running locally or on a local network, it should work as is. If not, you will have to configure it from the global configuration.