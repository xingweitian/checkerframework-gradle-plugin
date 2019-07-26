## Making a release of the Checker Framework Gradle plugin

This document describes how to make a release of the Checker Framework
Gradle plugin, which this repository contains.

### Prequisites

* Copy the publishing credentials to your `~/.gradle/gradle.properties` file.
The credentials are stored in the same place as the credentials used to make
a Checker Framework release, in a `gradle.properties` file.
To gain access to the credentials, contact one of the maintainers privately.

### Release process

1. Ensure that you have checked out the `master` branch of the project. Do
not make releases from other branches.
2. Update the plugin to use the latest version of the Checker Framework.
Search for its current version number and replace it by the
[latest version](https://github.com/typetools/checker-framework/blob/master/changelog.txt).
Also run: `(cd src/test/resources/maven/org/checkerframework && update.sh NEW_VERSION_NUMBER)`
3. Ensure that the
[Travis build](https://travis-ci.com/kelloggm/checkerframework-gradle-plugin/branches)
is passing on the `master` branch before beginning the release process.
4. Choose a new version string. Please try to respect
[semantic versioning](https://semver.org/). Do not augment the major
version without explicit approval from all the maintainers.
5. Change the version of the plugin. Search for the current plugin version
in the directory containing this file, and replace all instances of it
with the new version string.
6. Commit your changes: `git commit -m "Update version number to X.Y.Z"`
7. Run `./gradlew publishPlugins` from the top-level project directory
(which should also contain this file).