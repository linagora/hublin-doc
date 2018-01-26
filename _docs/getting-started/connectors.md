---
title: Connectors
category: Getting started
order: 4
---

Hublin is built on top of a modular system where modules can be plugged on both frontend and backend sides to customize and add new features to the platform. Connectors are modules which are implementing the interface to manage communications between peers. Based on this modular system, we developped several connectors based on differents WebRTC clients to be able to provide features which best fit deployments and constraints:

- [hublin-easyrtc-connector](https://github.com/linagora/hublin-easyrtc-connector) is based on the [easyRTC](https://easyrtc.com/products/easyrtc/) library on both backend and frontend. It provides a fully P2P conference system.
- [hublin-janus-connector](https://github.com/linagora/hublin-janus-connector) is using [Janus WebRTC Gateway](https://janus.conf.meetecho.com/). It provides more features, allow more users to join a conference but is more complex to deploy and configure.
