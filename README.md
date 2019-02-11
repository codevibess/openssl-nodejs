# openssl-nodejs

is a package which gives you a possibility to run every [OpenSSL](https://www.openssl.org/) command in [Node.js](https://nodejs.org/en/) in a handy way. Moreover, parameters like -in, -keyin, -config and etc can be replaced by a raw data ([Buffor](https://nodejs.org/dist/latest-v10.x/docs/api/buffer.html)).

# Installation &amp; Usage

```javascript
npm install openssl-nodejs
```

Import openssl module:
```javascript
const openssl = require('openssl-nodejs')
```

Next, invoke openssl function and put command with parameters inside a function like presented in the example below.
```javascript
openssl('openssl req -config csr.cnf -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout key.key -out certificate.crt')
```
To get access to the result of execution specify callback function as the last parameter of openssl function (with arguments err and buffer).

openssl function can be invoked with a single parameter like OpenSSL command (see example above) or within an array with command name and parameters itself.
```javascript
openssl(['req', '-config', 'csr.conf', '-out', 'CSR.csr', '-new', '-newkey', 'rsa:2048', '-nodes', '-keyout', 'privateKey.key', function (err, buffer) {
console.log(err.toString(), buffer.toString());
});
```

If you want to specify Buffer text instead of the file as an input/output or whatever you need, use the version with an array as a function parameter.
And put an object with keys: name: (specify a name of file which will be created to handle this command), and buffer: (your buffer variable)
Example of object:

```javascript
{ name:'csr.conf', buffer: BufferVariable }
```
Command example:
```javascript
openssl(['req', '-config', { name:'csr.conf', buffer: BufferVariable }, '-out', 'CSR.csr', '-new', '-newkey', 'rsa:2048', '-nodes', '-keyout', 'privateKey.key'], function (err, buffer) {
console.log(err.toString(), buffer.toString());
});
```

When you used a command which generates additional output in file format this package will create a folder openssl/ in the directory where the command was invoked. All output files will appear in this folder (openssl).

Note: 
> If u want to use a command which needs additional interaction use parameter -config and specify pass to file with configuration.
---
That's all that you need to start using it.

For any information, improvements or bug fixes please contact me.
If it's package was useful for you please give a star in [GitHub](https://github.com/codevibess). (really inspiring me to new ones)