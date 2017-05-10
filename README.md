# Protocol Buffer loader module for webpack

Converts .proto files into JSON so they can be [loaded without a parser](https://github.com/dcodeIO/ProtoBuf.js/wiki/Builder#using-json-without-the-proto-parser). For use with [webpack](http://webpack.github.io/docs/) and [ProtoBuf.js](https://github.com/dcodeIO/ProtoBuf.js)

## Fork Alert!
Since the original [proto-loader](https://github.com/brianchirls/proto-loader) hasn't been updated or accepted pull requests in over a year this package was forked off of @cessationoftime's [fork](https://github.com/cessationoftime/proto-loader) and published to npm under [@elliotchong/proto-loader](https://www.npmjs.com/package/@elliotchong/proto-loader). Some minor improvements have been made around dependencies along the way, but all credit for the original library goes to @brianchirls.

## Installation
`npm install protobufjs json-loader proto-loader`

## Usage

[Documentation: Using loaders](http://webpack.github.io/docs/using-loaders.html)

``` javascript
var protobuf = require('protobufjs');

var protoDefinition = require('json!proto!./message.proto');
// => returns json object converted from message.proto, resolves imports

var root = protobuf.Root.fromJSON(protoDefinition);
//...
```

### webpack config

``` javascript
module.exports = {
  module: {
    loaders: [
      {
        test: /\.proto$/,
        loaders: ['json-loader', "proto-loader"]
      }
    ]
  }
};
```

Then you only need to write: `require("./message.proto")`

## Run example with

```
webpack
node ./out/bundle.js
```


## License
MIT (http://www.opensource.org/licenses/mit-license.php)
