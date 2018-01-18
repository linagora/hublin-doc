---
title: Build
category: Development
order: 3
---

## Test suite

Build is done at several places, here is the summary:

1. The test suite is launched on each merge by Gitlab runner on [](). (It is previously launched when the developer pushes on his own repository, no code can be merged without a successful test suite)
2. Once merged, the repository is mirrored on []()
3. The TravisCI runner detects new commits and also launch the test suite at []()

## Docker images

A Docker Hub automated build is launched on each required branch at [https://hub.docker.com/r/linagora/hublin/](https://hub.docker.com/r/linagora/hublin/). The master branch will produce a `linagora/hublin:latest` image, each other branch will produce a `linagora/hublin:BRANCH_NAME` image.
