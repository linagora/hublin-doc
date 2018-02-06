---
title: Build
category: Development
order: 3
---

## Test suite

Build is done at several places, here is the summary:

1. The test suite is launched on each merge by Gitlab runner on [https://ci.linagora.com/linagora/lgs/openpaas/hublin/pipelines](https://ci.linagora.com/linagora/lgs/openpaas/hublin/pipelines). (It is previously launched when the developer pushes on his own repository, no code can be merged without a successful test suite)
2. Once merged, the repository is mirrored on github [https://github.com/linagora/hublin](https://github.com/linagora/hublin)
3. The TravisCI runner detects new commits and also launch the test suite at [https://travis-ci.org/linagora/hublin](https://travis-ci.org/linagora/hublin)
