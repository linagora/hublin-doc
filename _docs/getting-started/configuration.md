---
title: Configuration
category: Getting started
order: 3
---

* Here is the ToC, this line is needed to generate...
{:toc}

- Database configuration (MOngoDB connection) can be updated in the `config/db.json` file
- Local configuration can be updated in the `config` folder
- Global configuration (shared between nodes), can be updated in the `configuration` collection in the MongoDB database

## Database configuration

Hublin needs MongoDB to run. The MongoDB connection can be configured from the `config/db.json` file.

First, copy `db.json.sample` to `db.json`

```
cp db.json.sample db.json
```

Update the JSON document to fit your needs. By default, it is configured to connect to default host and port with a `hublin` database as defined in:

``` json
{
  "connectionString": "mongodb://localhost:27017/hublin"
}
```

## Local configuration

All the configuration which is related to the current hublin instance can be changed from the [config/default.json](https://github.com/linagora/hublin/blob/master/config/default.json) file.

### WebRTC

WebRTC settings can be changed from the `webrtc` sub document defined like:

```
"webrtc": {
  "enabled": true,
  "level": "debug",
  "roomNameRegExp": "^.{1,64}$",
  "usernameRegExp": "^(.){1,200}$",
  "adapter": "hublin.janus.connector"
}
```

While most of the settings can be kept as is, the `adapter`one is the most important. It allows to choose the adapter to use to provide the WebRTC communication channels. Possible values are:

- **hublin.easyrtc.connector**
- **hublin.janus.connector**

For more details about adapters, take a look at the [adapters page]({% link _docs/getting-started/adapters.md %})

### Loggers

Loggers can be configured in the config/default.*.json file:

- In the loggers array: Configure the core logger.
- In the loggers array of the webserver: Configure the webserver layer logger.

Note: Loggers are following the [Winston](https://github.com/winstonjs/winston) logger format.

A logger must have a name and a hash of options to use.

```
    {
      "name": "File",
      "enabled": true,
      "options": {
        "filename": "./log/application.log",
        "level": "info",
        "handleExceptions": true,
        "json": false,
        "prettyPrint": true,
        "colorize": false
      }
    }
```

A logger can be enabled or not (a logger added to the array without the enabled flag will not be active).

Winston allows to use external 'transports'. In order to use it, you must:

1. Install it locally using 'npm install'
2. Add it to the array
3. Define which is the module to be loaded to use this transport by setting the 'module' value
4. Use the right name. The name is used to build the function to be used as transport.

For example, if you want to use the [Mail Transport](https://github.com/winstonjs/winston#mail-transport), you will have to define it in the configuration like:

```
    {
      "name": "Mail",
      "enabled": "true",
      "module": "winston-mail",
      "options": {
        "to": "fail@hubl.in",
        "host": "smtp@hubl.in",
        "port": 587,
        "username": "admin",
        "password": "secret",
        "ssl": {
          "key": "",
          "ca": "",
          "cert": ""
        },
        "level": "error",
        "silent": true
      }
    }
```

Based on this configuration, Hubl.in will build the transport to add to Winston instance like:

```
const mail = require('winston-mail');
const Transports = mail[logger.name];

// Which is equivalent to
const Mail = require('winston-mail').Mail;
```

## Global configuration

### Mail

  To configure the mail feature, you need to create a document in the mongo collection configuration, as below:

```javascript
  {
    "_id" : "mail",
    "mail" : {
        "noreply" : "noreply@yourserver.com"
    },
    "transport" : {
        "type" : "SMTP",
        "config" : {
            "host" : "smtp.yourserver.com",
            "secureConnection" : false,
            "port" : 25
        }
    },
    "feedback" : {
        "rcpt" : [
            "hublin@yourserver.com"
        ]
    }
  }
```

  "smtp.yourserver.com" must be replaced by an actual SMTP server that you have access to, optionally defining an authentication if required by the SMTP server.
  hubl.in is actually using nodemailer to send emails, you'll find all possible confifuration settings on the project page at https://github.com/andris9/nodemailer-smtp-transport.

### i18n

You can configure what default language hubl.in will use, when the client browser requests an unsupported language. To do this, create a new document in the mongo **configuration** collection, as below:

```javascript
{
  _id: 'i18n',
  defaultLocale: 'en'
}
```

### webserver URL

Hubl.in allows sending invites using an email. In such cases, the system will try to detect the server URL using client HTTP headers. However, you can force the URL of your hubl.in instance by creating a web document in the configuration collection. The document looks like this:

```javascript
{
  _id: 'web',
  base_url: 'https://your.domain.com/'
}
```

### Ice servers

Hubl.in allows to configure the Ice servers to be used when launching conferences. In order to define them, you will need to add a document in mongo collection like:

- servers is an array of [RTCIceServer objects](https://developer.mozilla.org/en-US/docs/Web/API/RTCIceServer)

``` javascript
{
  _id: 'iceservers',
  servers: [
    {
      urls: 'turn:hublin.foo.bar.baz.com:3478',
      username: 'foo',
      credential: 'bar'
    },
    {
      urls: [
        'stun:stun.foo.bar.baz.com',
        'stun:stun-1.foo.bar.baz.com'
      ],
    }
  ]
}
```
