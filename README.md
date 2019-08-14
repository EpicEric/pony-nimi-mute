# pony-nimi-mute

A WIP pure Pony implementation of a RegEx engine. The final goal of the repo is to be the new official implementation, packaged with the stdlib, instead of a stand-alone library.

Note that despite also using the `regex` package name, this will not be concerned with exact API parity to the [official library](https://github.com/ponylang/regex) at all.

While the official RegEx library -- which wraps PCRE -- uses backtracking, this repository will use Thompson NFA simulation. As such, this implementation will most likely **not have backreferences**. Instead, the course of action -- once this makes it into the stdlib -- is to rename the other package to something like `pcre`, to provide any extra functionality for users that really need them.

[\[reference\]](https://swtch.com/~rsc/regexp/regexp1.html)

## Status

[![CircleCI](https://circleci.com/gh/EpicEric/pony-nimi-mute.svg?style=svg)](https://circleci.com/gh/EpicEric/pony-nimi-mute)

The following is a rough roadmap of things that I want to be done (coded **and** tested) before a release (mostly copied from the reference above):

* :heavy_check_mark: Create and set-up the repository.
* Compile NFA with basic rules (literal characters, concatenation, alternation (`|`), zero or one (`?`), zero or more (`*`), one or more (`+`), etc.).
* Cache NFA into DFA.
* Add extra rules:
  * Escape sequences.
  * Character classes.
  * Counted repetition.
  * Submatch extraction.
  * Unanchored matches.
  * Non-greedy operators.
  * Assertions.
* Support flags.
* Support UTF-8.
* Anything else from the POSIX standard that's still missing?

## Installation

* Install [pony-stable](https://github.com/ponylang/pony-stable)
* Update your `bundle.json`

```json
{ 
  "type": "github",
  "repo": "epiceric/pony-nimi-mute"
}
```

* `stable fetch` to fetch your dependencies
* `use "regex"` to include this package
* `stable env ponyc` to compile your application
