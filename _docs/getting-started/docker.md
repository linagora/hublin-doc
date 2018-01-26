---
title: Get started with Docker
category: Getting started
order: 2
---

* Here is the ToC, this line is needed to generate...
{:toc}

## Docker Compose

The easiest way to try Hubl.in on your local machine is to use [Docker Compose](https://docs.docker.com/compose/).
We assume that you already have Docker Compose installed on your machine. Run the following commands:

```shell
# grab the docker-compose file
wget https://raw.githubusercontent.com/linagora/hublin/master/docker-compose.yml
# or
git clone --depth=1 https://github.com/linagora/hublin.git && cd hublin

# launch it!
docker-compose up --no-build
```

Launching the application may take some time if you do not have the required Docker images locally, grab a cup of ☕️ and when
it is ready you can access to the application at [http://localhost:8080](http://localhost:8080).

## Images

- [hublin](https://hub.docker.com/r/linagora/hublin/) Hublin image, does not provide Mongo, Redis and all the required services but the runtime.
- [janus-gateway](https://hub.docker.com/r/linagora/janus-gateway/) A Janus gateway image configured with everything needed to work with Hublin.