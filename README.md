# openssl-nodejs


is a packadge which give you possibility run every command of OpenSSL in Node.js in handy way. Moreover parameters like -in, -keyin, -config and etc can be subtitute by a Buffor.

# Intro


T

# Installation

```javascript
npm install openssl-nodejs
```

# Usage

Import openssl module by the line:

```javascript
const openssl = require('openssl-nodejs')
```
Next invoke openssl and put command with parameters inside a function like presented in exemple below.
```javascript
 openssl(`openssl req -config csr.cnf -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout key.key -out certificate.crt`)
 ```

openssl function can be invoken with single parameter like openssl comand (see example below) or you can put an array where every element is a new word of command
That`s all what you need to start use it.

