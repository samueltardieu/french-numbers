# french-numbers

[![Build Status](https://travis-ci.org/samueltardieu/french-numbers.svg?branch=master)](https://travis-ci.org/samueltardieu/french-numbers)
[![Current Version](https://img.shields.io/crates/v/french-numbers.svg)](https://crates.io/crates/french-numbers)
[![Documentation](https://docs.rs/french-numbers/badge.svg)](https://docs.rs/french-numbers)
[![License: Apache-2.0/MIT](https://img.shields.io/crates/l/french-numbers.svg)](#license)

This crate transforms a number into its French representation.

## Using this crate

In your `Cargo.toml`, put:

``` ini
[dependencies]
french-numbers = "1.1.1"
```

You can then use the `french_number` function from the `french_numbers` crate
to format any integer into the beautiful French romance language:

``` rust
use french_numbers::french_number;

assert_eq!(french_number(&71), "soixante-et-onze");
assert_eq!(french_number(&1001), "mille-un");
assert_eq!(french_number(&-200001), "moins deux-cent-mille-un");
assert_eq!(french_number(&-200000001), "moins deux-cents-millions-un");
assert_eq!(french_number(&-204000001), "moins deux-cent-quatre-millions-un");
```

You can also request the use of the feminine form, or prefer the previous way of writing
numbers predating the 1990 orthographic reform:

```rust
use french_numbers::*;

assert_eq!(french_number_options(&37251061, &POST_REFORM_MASCULINE),
           "trente-sept-millions-deux-cent-cinquante-et-un-mille-soixante-et-un");
assert_eq!(french_number_options(&37251061, &POST_REFORM_FEMININE),
           "trente-sept-millions-deux-cent-cinquante-et-un-mille-soixante-et-une");
assert_eq!(french_number_options(&37251061, &PRE_REFORM_FEMININE),
           "trente-sept millions deux cent cinquante et un mille soixante et une");
assert_eq!(french_number_options(&37251061, &PRE_REFORM_MASCULINE),
           "trente-sept millions deux cent cinquante et un mille soixante et un")
```

An example program can dump particular number, with different options:

``` bash
% cargo run --example french-number -- --help
Print number(s) in French

USAGE:
    french-number [FLAGS] <LOW> [HIGH]

FLAGS:
    -f, --feminine     use the feminine declination
    -h, --help         Prints help information
    -r, --no-reform    use the pre-1990 orthographic reform writing
    -p, --prefix       prefix output with the numerical representation
    -V, --version      Prints version information

ARGS:
    <LOW>     number (or low bound) to use
    <HIGH>    optional high bound
```
