---
title: Installation
category: Getting started
order: 1
---


We assume that you already have `git` installed on your machine. Run the following commands:

```shell
git clone https://github.com/linagora/hublin.git && cd hublin
```

Install the right version of Node.js (lts/carbon v8.9.4). We encourage to use [nvm](https://github.com/creationix/nvm) and so install and switch to the right version with:

``` sh
nvm use
```

Then install all the required dependencies

``` sh
npm install
```

Once [configured]({{site.baseurl}}{% link _docs/getting-started/configuration.md %}), and all services are up i.e. MongoDB, Redis, Janus (optional based on your requirements, check [Janus documentation]({{site.baseurl}}{% link _docs/getting-started/janus.md %})), you can start Hublin with

``` sh
npm start

# or

node server.js
```

**Note**: For more information on how to install MongoDB, Redis and Janus, please refer to their official documentation.