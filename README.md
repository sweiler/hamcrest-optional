# Hamcrest Optional
[![Travis CI build](https://travis-ci.org/npathai/hamcrest-optional.svg?branch=master)](https://travis-ci.org/npathai/hamcrest-optional)   [![Coverage Status](https://coveralls.io/repos/npathai/hamcrest-optional/badge.svg?branch=master&service=github)](https://coveralls.io/github/npathai/hamcrest-optional?branch=master)

An extension to [Java Hamcrest](https://github.com/hamcrest/JavaHamcrest) which provides matchers for *JDK 8* Optional

## Usage

hamcrest-optional provides four matchers for `Optional`: `isEmpty()`,
`isPresent()`, `hasValue(Object)` and `hasValue(Matcher)`.

### isEmpty()

This matcher matches when the examined `Optional` contains no value.

```java
import static com.github.npathai.hamcrestext.matcher.OptionalMatchers.isEmpty;

Optional<Object> optional = Optional.empty();
assertThat(optional, isEmpty());
```

### isPresent()

This matcher matches when the examined `Optional` contains a value.

```java
import static com.github.npathai.hamcrestext.matcher.OptionalMatchers.isPresent;

Optional<String> optional = Optional.of("dummy value");
assertThat(optional, isPresent());
```

### hasValue(Object)

This matcher matches when the examined `Optional` contains a value that is
logically equal to the specified object.

```java
import static com.github.npathai.hamcrestext.matcher.OptionalMatchers.hasValue;

Optional<String> optional = Optional.of("dummy value");
assertThat(optional, hasValue("dummy value"));
```

### hasValue(Matcher)

This matcher matches when the examined `Optional` contains a value that
satisfies the specified matcher.

```java
import static com.github.npathai.hamcrestext.matcher.OptionalMatchers.hasValue;
import static org.hamcrest.Matchers.startsWith;

Optional<String> optional = Optional.of("dummy value");
assertThat(optional, hasValue(startsWith("dummy")));
```

## Development Guide

hamcrest-optional is build with [Maven](http://maven.apache.org/). If you want
to contribute code then

* Please write a test for your change.
* Ensure that you don't break the build by running `mvn verify -Dgpg.skip`.
* Fork the repo and create a pull request. (See [Understanding the GitHub Flow](https://guides.github.com/introduction/flow/index.html))

hamcrest-optional supports [Travis CI](https://travis-ci.org/) for continuous
integration. Your pull request is automatically build by Travis CI.

## Release Guide

* Select a new version according to the
  [Semantic Versioning 2.0.0 Standard](http://semver.org/).
* Set the new version in `pom.xml`.
* Commit the modified `pom.xml`.
* Push the commit: `git push origin master`
* Run `mvn clean deploy` with JDK 8.
* Add a tag for the release: `git tag hamcrest-optional-X.X.X`
* Push the tag: `git push origin hamcrest-optional-X.X.X`
