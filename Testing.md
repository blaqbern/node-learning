# Testing

There three things to think about here:

1. Expect library
- Testing framework
- Test runner
- Coverage

## Expectation library

1. `should.js`
- `expect.js`
- `chai`

`should` and `expect` differ slightly. As far as I can tell this is mostly about which you find more readable. Both are designed to be more readable--by being more colloquial--than traditional `assert`-style testing commands. `Chai` allows for either `should`- or `expect`-style statements and even `assert`-style as well. You can look at the [documentation](http://chaijs.com/guide/styles/) for some insight into the differences between these approaches.

## Testing Frameworks

1. Mocha
- Jasmine

These seem to be the main competitors. Mocha requires an expectation library like the ones mentioned above. Jasmine does not; it has its own expectation library (most similar to `expect`) built in. It can also also provide a "Test Double" (a `spy` in Jasmine's terminology), right out of the box. This feature allows you to replace an object with a different one during a test. Mocha requires you to include a separate library for this functionality. Sinon is such a library, and it actually provides some extra functionality in addition to test doubles. For example, Sinon allows you to create fake server responses for particular endpoints, which could be handy. My feeling here is that Sinon may be something we would want to include whether we chose Mocha or Jasmine. The overlap it has with some of the built-in functionality of Jasmine is a win for Mocha, in my opinion.

Mocha has its own CLI that lets you run your tests from the command line, and includes a `--watch` options which will run your tests each time a file in the `cwd` changes. Jasmine does not have this functionality out of the box, but does have a [CLI tool](https://github.com/jasmine/jasmine-npm) that can be `requie`d from npm.

## Test Runners
 1. Karma
 - tape
 - tape, node-tap, AVA
 - Wallaby

Karma runs "on real browsers". I'm not sure exactly what that means. There doesn't seem to be much else that distinguishes it from any other test runner. It can be used with Mocha, Jasmine or any other testing framework.

`tape` is a minimal test framework that seems a bit different from the other `RSpec`-style frameworks (Mocha and Jasmine). It is a [TAP](http://testanything.org) producer. I'm still trying to figure out what that means exactly, but it's been around a long time. It has its roots in the PERL community. The syntax is not as colloquial as the aforementioned frameworks, but the [developer](https://github.com/substack) is a certainly one whom I trust. He is the creator of [Browserify](https://github.com/substack/node-browserify). Some other options along these same lines are:
- [node-tap](http://www.node-tap.org). The [developer](https://github.com/isaacs) of this library is also a heavy-hitter. He was one of the main early contributors to the [node](http://nodejs.org) project. Code coverage is built in.
- AVA similar to node-tap and tape, but allows for concurrent execution of tests. No code coverage, but [nyc](https://github.com/istanbuljs/nyc) (which is basically instanbul that allows for concurrent test running) can be used for code coverage reporting.

Wallaby seems to be geared mostly toward editors and IDEs. I don't quite understand how this works, but it probably doesn't matter, because it is not open source and not free, so those are two major knocks on it, in my opinion.
