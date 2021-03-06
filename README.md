# csgo-float

> Retrieve CS:GO float values in JavaScript

    npm i -S csgo-float

#### Usage

Only one request can be done at a time by each client. You'll have to wait for the first request to be processed before sending another one.

###### Client

```javascript
new FloatClient(clientAuth, debug)
```

`clientAuth` {Object} SteamUser credentials to login / SteamClient

`debug` {Boolean} Print some useful informations

```javascript
// Init a client using a credentials object
const client = new FloatClient({
  account_name: 'yeah',
  password: 'this-is',
  auth_code: 'definitely',
  sha_sentryfile: 'right'
}, true)

// Or by passing an existing SteamClient instance
// that should be connected and logged.
const steamClient = new SteamClient()
const client = new FloatClient(steamClient)
```

###### Methods

```javascript
client.requestFloat(url)
```

Returns a Promise.

Where url is a string formatted like `S76561198190349706A4757476613D16467978012840927110`.

```javascript
client.requestFloat('S76561198190349706A4757476613D16467978012840927110')
  .then(floatValue => console.log(floatValue))
  .catch(err => console.log(err))
```

###### Events

`ready` Emitted once the client is ready to receive float requests

`sentry` The user is authenticated and the account sentry is sent, should be saved somewhere

`error` Once an error is triggered

#### Thanks

This would not exists without the help of [@Twewki](https://github.com/Tewki).
