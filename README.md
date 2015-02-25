### rl-socket-client: the readline socket client

we ought to just pretend it stands for [rocketlauncher](http://ioquake3.org/wp/wp-content/themes/ioq3-deboy/explodedView.png)-socket-client. that's way cooler, right?

this module was designed for applications requiring a tty context along-side a tcp socket context (a tcp chat client, for instance) it provides a custom prompt, line ending value and tab-completion command list.

##### api

- `#connect()`: initiate a connection to the given `host` and `port`
- `#on(event)`: currently the only event emitted is `connected`
- `#write(text)`: programmatically send `text` over the wire

##### usage

```js
var rlsc = require('rl-socket-client');

new rlsc({
    host: '192.168.128.100',
    port: 1829,
    prompt: '% ',
    lineEnding: '\n',
    autoConnect: true,
    completions: ['ls', 'pwd', 'cat', 'echo']
});

// or

var client = new rlsc({
    host: '192.168.128.100',
    port: 1829
}).connect();

client.on('connected', function() {
    client.write('blah blah...');
});
```
