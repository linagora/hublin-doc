---
title: Docker
category: Development
order: 4
---

* Here is the ToC, this line is needed to generate...
{:toc}

## Images

- [linagora/hublin](https://hub.docker.com/r/linagora/hublin/) Hublin image, does not provide Mongo, Redis and all the required services but the runtime.
- [linagora/hublin:janus](https://hub.docker.com/r/linagora/hublin/) Hublin image as above but configured for Janus.
- [linagora/janus-gateway](https://hub.docker.com/r/linagora/janus-gateway/) A Janus gateway image configured with everything needed to work with Hublin.

## Build Images

Images are built on commit by Docker Hub or by TravisCI, but if you need to build them manually:

``` sh
# build the default hublin image with easyrtc
docker build -t linagora/hublin .

# build the hublin image configured with Janus, needs the previous one to be build first
docker build -t linagora/hublin:janus -f Dockerfile.janus .
```