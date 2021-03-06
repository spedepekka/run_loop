[![GitHub version](https://badge.fury.io/gh/calabash%2Frun_loop.svg)](http://badge.fury.io/gh/calabash%2Frun_loop) [![Build Status](https://travis-ci.org/calabash/run_loop.svg?branch=master)](https://travis-ci.org/calabash/run_loop) [![Dependency Status](https://gemnasium.com/calabash/run_loop.svg)](https://gemnasium.com/calabash/run_loop) [![License](https://go-shields.herokuapp.com/license-MIT-blue.png)](http://opensource.org/licenses/MIT)

## Run Loop

### Supported Xcode Versions

* Xcode >= 5.1.1
* Xcode 6.0, 6.0.1
* Xcode 6.1

### License

Run Loop is available under the MIT license. See the LICENSE file for more info.

### Versioning

Run Loop follows the spirit of Semantic Versioning. [1]  However, the semantic versioning spec is incompatible with RubyGem's patterns for pre-release gems. [2]

_"But returning to the practical: No release version of SemVer is compatible with Rubygems."_ - David Kellum

- [1] http://semver.org/
- [2] http://gravitext.com/2012/07/22/versioning.html

## For Run Loop Gem Developers

### IMPORTANT note to devs RE: udidetect submodule

The current head of the udidetect head does not include the udidetect binary.

If you are compelled to update, you _must rebuild and replace the scripts/udidetect_ binary.

At this time, there is no reason to update.

- [1] https://github.com/vaskas/udidetect/pull/3

### new Xcode 6 programs

* simctl
* sim
* projectInfo

### Tests

###### Failing Tests

```
1) RunLoop regression: injecting a dylib targeting the simulator with Xcode 6.0
```

###### Unstable Tests

```
2) RunLoop regression: running on physical devices Xcode 6.0
```

#### CI

* https://travis-ci.org/calabash/calabash-ios
* https://travis-ci.org/calabash/run_loop
* https://travis-ci.org/calabash/calabash-ios-server
* Calabash iOS toolchain testing - http://ci.endoftheworl.de:8080/

To simulate CI locally:

```
[run-loop] $ scripts/ci/travis/local-run-as-travis.rb
```

#### Rspec

Take a break because these test launch and quit the simulator multiple times which hijacks your machine.  You have enough time to take some deep breaths and do some stretching.  You'll feel better afterward.  For continuous TDD/BDD see the Guard section below (most simulator tests are disabled in Guard).

```
[run-loop] $ be rake spec
```

#### Device Testing

Each connected device running iOS 6.0 <= iOS < 8.0 is targeted with one test.

##### Regression vs. Xcode version

If you have alternative Xcode installs that look like this:

```
/Xcode/5.1/Xcode.app
/Xcode/5.1.1/Xcode.app
/Xcode/6b6/Xcode6-Beta6.app
```

The rspec tests will do regression testing against each version.

##### Guard

Requires MacOS Growl - available in the AppStore.

```
$ bundle exec guard  start --no-interactions
```

Most of the tests that involve launching the simulator are not run in Guard.
