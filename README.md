# OpenST Developer Guidelines

## General Project Setup

* GitHub pull requests must require at least one review to allow merging
* GitHub pull requests may only be merged using "merge commits" (no squash or rebase)
* All projects should have continuous integration setup using [TravisCI]
  * [TravisCI] must run unit tests and integration tests for every pull request
  * [TravisCI] should run all applicable linters for every pull request
  * GitHub pull requests must require that [TravisCI] passes to allow merging

## Solidity

* Follow our [Solidity style guide]
* Any project with Solidity code should have [ethlint] (formerly solium) installed
  * Use this configuration: [soliumrc]
  * Make sure all changes pass the linter before opening a pull request

## JavaScript

* Follow the [Airbnb style guide]
* Any project with JavaScript code should have [eslint] installed
  * Use this configuration: [eslintrc]
  * Make sure all changes pass the linter before opening a pull request

## Rust

* Format your code using `rustfmt`.

[airbnb style guide]: https://github.com/airbnb/javascript
[eslint]: https://eslint.org/
[eslintrc]: ./.eslintrc.json
[ethlint]: https://github.com/duaraghav8/Ethlint
[solidity style guide]: ./SOLIDITY_STYLE_GUIDE.md
[soliumrc]: ./.soliumrc.json
[travisci]: https://travis-ci.org/
