# french-numbers

[![Unix build Status](https://travis-ci.org/samueltardieu/french-numbers.svg?branch=master)](https://travis-ci.org/samueltardieu/french-numbers)
[![Windows build Status](https://ci.appveyor.com/api/projects/status/github/samueltardieu/french-numbers?branch=master&svg=true)](https://ci.appveyor.com/project/samueltardieu/french-numbers)
[![Current Version](https://img.shields.io/crates/v/french-numbers.svg)](https://crates.io/crates/french-numbers)
[![License: Apache-2.0/MIT](https://img.shields.io/crates/l/french-numbers.svg)](#license)

This crate transforms a number into its French representation.

## Using this crate

In your `Cargo.toml`, put:

``` ini
[dependencies]
french-numbers = "0.1"
```

You can then use the `french_number` function from the `french_numbers` crate
to format any integer into the beautiful French romance language:

``` rust
use french_numbers::french_number;

assert_eq!(french_number(&71), "soixante-et-onze");
assert_eq!(french_number(&1001), "mille-et-un");
assert_eq!(french_number(&-200001), "moins deux-cent-mille-et-un");
assert_eq!(french_number(&-200000001), "moins deux-cents-millions-un");
assert_eq!(french_number(&-204000001), "moins deux-cent-quatre-millions-un");
```