
# Testing nodejs REST


## Why testing?

- Does not prove the absence of bugs
- Can help identify existing bugs
- Can avoid introducing new bugs
- Repeated testing necessary in agile development
- Automated as far as possible
- It's in the assignment ...


## Basic Approaches

- Using browser (manual)
- Using Postman (partly automatic)
- Using test scripts (automatic)


## Browser-based testing

- GET is easy: just type in URL
- POST is slightly harder: build HTML form
- Other http methods more difficult


## Postman

- Originally a chrome plugin
- Now a [web application](https://www.postman.com/) with Desktop Agent
- Define a set of requests in a collection
- Choose GET or POST (or other)
- Include body parameters for POST
- Use raw/JSON for JSON
- Can specify expected responses


## Test scripts

- There are very many JavaScript unit testing frameworks (mocha, jasmine, ava)
- I recommend using [Jest](https://jestjs.io/)
- Read a [2020 review](hhttps://medium.com/welldone-software/an-overview-of-javascript-testing-7ce7298b9870)
- Read about [tools in demand in 2020](https://blog.logrocket.com/most-in-demand-javascript-testing-tools-in-2020/)
  - Developed from [StateofJS](https://2019.stateofjs.com/)
- `npm install --save-dev jest`
- Tests are js programs (as in jUnit)
- Put tests in test directory or name .test.js


## Running tests

- Get it going first
- Use nodemon to auto-restart server
- Add test script to your package.json
- run test with npm test
- see some [example tests for thing](https://github.com/stevenaeola/gitpitch/blob/master/prog/nodejs_testing/app.test.js) 


## Separate out app from server

So that running tests does not launch the server

e.g. app.js file
```
const express = require('express');
const app = express();
// ... add routes
module.exports = app;

```
e.g. server.js file
```
const app = require('./app');
app.listen(8090);

```


## Test coverage

- In testing we try to improve quality
- Coverage measures how much functionality has been tested
- Could measure this in terms of
  - the space of possible inputs (black box)
  - the code that has been executed (white box)
- Unit testing combines the two
- Need to think about  valid and invalid inputs


## Mocking

- You want to avoid accessing live systems during tests
- Reading may be brittle
- Writing may be dangerous
- Real system may not be developed yet
- Replace access to live data using [mocking](https://en.wikipedia.org/wiki/Mock_object)
- There are [specific jest functions for this](https://jestjs.io/docs/en/mock-functions.html)
- If you intend to use a remote web service you should use mocking
- Same for a remote database (e.g. Firebase) 

