# API Gateway Lambda Compat

Compat layer between Next.js serverless page and AWS/Yandex.Cloud Api Gateway => Lambda/Serverless functions Proxy integration.

Lambda Proxy Integration event structure documentation can be found [here](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-lambda-proxy-integrations.html).

This is a fork of [next-aws-lambda](https://www.npmjs.com/package/next-aws-lambda)

## Installation

`npm install next-aws-compat`

## Usage

```js
const compat = require("next-aws-compat");
const page = require(".next/serverless/pages/somePage.js");

// using callback

module.exports.render = (event, context, callback) => {
  compat(page)(event, context, callback);
};

// using async promise

module.exports.render = async (event, context) => {
  const responsePromise = compat(page)(event, context); // don't pass the callback parameter
  return responsePromise;
};
```
