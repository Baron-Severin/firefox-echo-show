# Firefox for Echo Show

Available on all Echo Show devices: *"Alexa, open Firefox!"*

## Getting Involved
Our code is open source and we encourage all positive contributions! We love pull
requests, bug reports, ideas, (security) code reviews and other kinds of contributions.
Before you contribute, please read the [Community Participation
Guidelines](https://www.mozilla.org/en-US/about/governance/policies/participation/).

* [Guide to Contributing][contribute] (**new contributors start here!**)
* Open issues: https://github.com/mozilla-mobile/firefox-echo-show/issues
  * [`good first issues`][good first] | [`help wanted`][help]
  * File a security issue: we're working on getting a space!
* IRC: [#focus (irc.mozilla.org)](https://wiki.mozilla.org/IRC) | [view logs](https://mozilla.logbot.info/focus/);
we're available Monday-Friday, GMT and PST working hours.
* Mailing list:
[firefox-focus-public@](https://mail.mozilla.org/listinfo/firefox-focus-public)

### Project resources
* Project documentation: [docs/](https://github.com/mozilla-mobile/firefox-echo-show/tree/master/docs)
* [Device reference]
* [Telemetry documentation](docs/telemetry.md)

## Build instructions
1. Clone the repository:
```shell
git clone https://github.com/mozilla-mobile/firefox-echo-show.git
```

2. Import the project into Android Studio or build on the command line:

  ```shell
  ./gradlew clean app:assembleAmazonWebviewDebug
  ```
3. Make sure to select the right build variant in Android Studio: **amazonWebviewDebug**

### Running
You can run from Android Studio or adb. You can run on an Android emulator but the
behavior may not be the same: see the [device reference] documentation for
more details on emulator device selection and other changed behaviors.

### Testing
To run a reasonable subset of the unit tests, we recommend:
```sh
./gradlew testAmazonWebViewDebug
```
To generate code coverage reports, run:
```sh
./gradlew -Pcoverage jacocoAmazonWebViewDebugTestReport
```
Reports can be found at
`app/build/jacoco/jacoco<buildVariant>TestReport/html/index.html`

### Pre-push hooks
Since we don't have CI, if you're pushing code, please add a pre-push hook. To use the
recommended hook, run this command from the project root:
```sh
ln -s ../../quality/pre-push-recommended.sh .git/hooks/pre-push
```

To push without running the pre-push hook (e.g. doc updates):
```sh
git push <remote> --no-verify
```

### Signing release builds
To build and sign a release build with our production keys using Autograph, run:
```sh
./tools/sign_release.sh
```

If you're not creating a release but want to create a release build for
local testing, you can append `--test` to ignore some release checks.

See that script's source for further usage.

## License

    This Source Code Form is subject to the terms of the Mozilla Public
    License, v. 2.0. If a copy of the MPL was not distributed with this
    file, You can obtain one at http://mozilla.org/MPL/2.0/

[device reference]: docs/device_reference.md
[contribute]: https://github.com/mozilla-mobile/shared-docs/blob/master/android/CONTRIBUTING.md
[good first]: https://github.com/mozilla-mobile/firefox-echo-show/labels/good%20first%20issue
[help]: https://github.com/mozilla-mobile/firefox-echo-show/labels/help%20wanted
