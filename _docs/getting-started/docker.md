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

## Docker Compose with Janus

You can launch all services including Janus from the root of the repository like:

``` shell
git clone --depth=1 https://github.com/linagora/hublin.git && cd hublin

# launch it!
DOCKER_IP=<YOUR DOCKER IP> docker-compose -f docker-compose.yml -f docker-compose.janus.yml up
```

Additional information about how we use Docker is available in the [Docker Development page]({{site.baseurl}} {% link _docs/dev/docker.md %})