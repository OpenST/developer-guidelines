# OpenST Developer Guidelines

## General Project Setup

* GitHub pull requests must require at least one review to allow merging
* GitHub pull requests may only be merged using "merge commits" (no squash or rebase)
* All projects should have continuous integration setup using [TravisCI]
  * [TravisCI] must run unit tests and integration tests for every pull request
  * [TravisCI] should run all applicable linters for every pull request
  * GitHub pull requests must require that [TravisCI] passes to allow merging
* All projects should have a `.gitignore` file that includes at least all build artifacts and auto-generated code (like `./build` or some generated content of `./lib`) and all dependencies (like `./node_modules`)
* Documentation should be in markdown format
* Sign all your git commits and tags with your private key (and add the public key to your GitHub account)

Branches:

* `master` is the latest stable release
* `develop` is the main branch and always reflects the latest development
* `release-x.y` branches follow their respective release

Every project must have the following files:

* `README.md`
  * For a layout of the readme see this [readme example]
  * Content should include (in this order):
    * Title followed by relevant badges using shields.io
    * Introductory text
    * *Instructions* section with help on installation and usage
    * *Related Work* section
    * *Contributing* section with
      * help on setup and testing
      * a link to this guide
      * links to [discourse] and [gitter]
* `LICENSE`
* `CHANGELOG.md`
  * For the layout of the changelog see this [changelog example]
  * Notable changes should link to their pull request(s) using absolute links

## Releases

Version identifiers follow [Semantic Versioning 2] without a leading `v`.
A valid version identifier would be for example `0.10.3` or `0.5.1-alpha.3`.

Every **MINOR** version must have its dedicated git branch.
For example, versions `0.10.x` would go into the release branch `release-0.10` whereas versions `1.2.x` would go into release branch `release-1.2`.
Release branches must start with `release-` followed by **MAJOR** and **MINOR** version identifier separated by a period.

Every release that shall be published must be tagged in git (on GitHub).
Pre-releases (e.g. `-alpha.3`) must only have an annotated tag.
Releases (e.g. `0.10.0`) must have an accompanying GitHub release with release notes.

Before merging the latest changes from `develop` into a release branch:

* Every release and pre-release must make sure that the `CHANGELOG` reflects all relevant changes and is up-to-date.
* Every release and pre-release must make sure that the version listed in `package.json` is correct.

## Solidity

* Follow our [Solidity style guide]
* Any project with Solidity code should have [ethlint] (formerly solium) installed
  * Use this configuration: [soliumrc]
  * Make sure all changes pass the linter before opening a pull request
* `package.json` should include all required build steps in `scripts.prepack`
* Provide at least the following `package.json` scripts:
  * `test`
  * `test:integration`
  * `build`
  * `lint`

### Directory Structure

* All contract source code should be below the directory `./contracts`
* All unit test and related code should be below the directory `./test`
* All integration test and related code should be below the directory `./test_integration`
* All build artifacts of a library project should be in the directory `./lib`
* All documentation should be below the directory `./docs`

## JavaScript

* Follow the [Airbnb style guide]
* Any project with JavaScript code should have [eslint] installed
  * Use this configuration: [eslintrc]
  * Make sure all changes pass the linter before opening a pull request

### Directory Structure

* All source code should be below the directory `./src`
* All unit test and related code should be below the directory `./test`
* All integration test and related code should be below the directory `./test_integration`
* All build artifacts of a library project should be in the directory `./lib`
* All documentation should be below the directory `./docs`

## `package.json`

This section applies to Solidity and JavaScript projects alike.

* `package.json` should include all required build steps in `scripts.prepack`
* Provide at least the following `package.json` scripts:
  * `test`
  * `test:integration`
  * `build`
  * `lint`
* Define `files` to minimize the size of the published package
* `main` should point to `./lib/index.js`

## Rust

* Format your code using `rustfmt`.

[airbnb style guide]: https://github.com/airbnb/javascript
[changelog example]: https://github.com/OpenSTFoundation/mosaic-contracts/blob/develop/CHANGELOG.md
[discourse]: https://discuss.openst.org/
[eslint]: https://eslint.org/
[eslintrc]: ./.eslintrc.json
[ethlint]: https://github.com/duaraghav8/Ethlint
[gitter]: https://gitter.im/OpenSTFoundation/SimpleToken
[readme example]: https://github.com/OpenSTFoundation/mosaic.js/blob/develop/README.MD
[semantic versioning 2]: https://semver.org/
[solidity style guide]: ./SOLIDITY_STYLE_GUIDE.md
[soliumrc]: ./.soliumrc.json
[travisci]: https://travis-ci.org/
