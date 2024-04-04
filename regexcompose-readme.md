# RegExCompose

RegExCompose is a library that allows the composition of regular expressions from multiple others, using a special syntax.

## See:
- [Process](#process) for information on how the main interface works and what it does
- [Terminology](#terminology) if you get confused by terminology in docstrings and this doc
- [Syntax](#syntax) for information on how these expressions are written
- [Documentation](#documentation) for documentation of the interface
  - [Exceptions](#exceptions) for information on exceptions specific to this package
  - [Functions](#functions) for information on the functions that are not part of a `PatternComposer`
  - [PatternComposer](#patterncomposer) for information on the main interface of this package

# Terminology
A "reference"-pattern refers to a pattern that contains references to other patterns (contains a `(?~<name>)`)  
A "reference"-pattern *part* refers to the `<name>` in a pattern containing `(?~<name>)`

[Pattern "compilation"](#pattern-compilation) refers to the process of filling a pattern's "parts" with values, A.E. replacing `(?~name)` in a pattern with the pattern named "name". A "partial compilation" refers to a compilation that has some `(?~name)` parts left in due to missing patterns.

# Syntax
In this file, all examples and information given will presume the default pattern is being used (`REFPATT_PATT`). All procedures and initializers that have a `refpatt_patt` parameter will accept an alternative pattern that can change this.  
The default pattern matches `(?~name)`, where `name` is the pattern to be used.

# Process
This section contains information on both what the main interface (namely, [`PatternComposer`](#patterncomposer)) does, as well as why/how it does it.

## Adding a pattern
When a pattern, usually with `PatternComposer.add()` or `PatternComposer.multiadd()` with name `name` and pattern `patt` is added (or replaced), `PatternComposer.patterns[name]` is set to `patt`. Then, the pattern is [updated](#)

# Documentation
Also see docstrings in `__init__.py` for (possibly) more detailed/up-to-date information

## Exceptions

[`PatternComposeException(Exception)`](#patterncomposexception)
 ├──[`exceptions.PatternExistsError`](#exceptionspatternexistserror)
 ├──[`exceptions.PatternNotFoundError(KeyError)`](#exceptionspatternnotfound)
 ├──[`exceptions.RequiredPatternError`](#exceptionsrequiredpatternerror)
 └──[`exceptions.IncompletePatternError`](#exceptionsincompletepatternerror)
 
### `PatternComposeException`

The base exception class

Note that this exception is both in the module's global namespace, as well as in the `exceptions` namespace

### `exceptions.PatternExistsError`
Raised when a pattern could not be added due to its name already being taken

Raised by:
- [`PatternComposer.add()`](#add) and [`PatternComposer.multiadd()`](#multiadd)

### `exceptions.PatternNotFoundError`
Raised when a pattern was directly needed, but not defined

Raised by:
- [`compile_refpatt()`](#compile_refpatt) *(only when its `allow_partial` is false)*
- [`PatternComposer.update()`](#update) and [`PatternComposer.multiupdate()`](#multiupdate)
- [`PatternComposer.__getitem__()`](#__getitem__) / [`PatternComposer[]`](#__getitem__)

In addition to inheriting from [`PatternComposeException`](#patterncomposeexception), this exception also inherits from `KeyError`

### `exceptions.IncompletePatternError`
Raised when a fully compiled non-partial pattern is required, but it couldn't be fully resolved

Raised by:
- [`PatternComposer.__getitem__()`](#__getitem__) / [`PatternComposer[]`](#__getitem__)

## Functions
Functions that do not need the state provided by `PatternComposer`

### `get_refpatt_parts()`

### `compile_refpatt()`

# PatternComposer
The main interface of this package

## Instance variables
- `.patterns`: `dict`
  - Keys: `str`, the name of the pattern
  - Vals: `str`, the uncompiled pattern
- `.references`: `dict`
  - Keys: `str`, the name of the referrer pattern
  - Vals: `frozenset[str]`, the reference-pattern parts that the pattern contains, as returned by [`get_refpatt_parts()`](get_refpatt_parts)
- `.compiled`: `dict`
  - Keys: `str`, the name of the pattern
  - Vals: `str`, the value of the pattern, constructed through

Note that the only one of these that is probably safe(r) to mutate is `refpatt_patt`, modifying any of the rest is considered undefined behavior when not following [Process](#process)

## Initializer Parameters

## Methods

### `__getitem__()` `[]`
Params:
- `patt`: `str`

Returns the compiled pattern with the name `patt`, but raises a [`exceptions.IncompletePatternError`] if the pattern is incomplete ([`.is_complete(patt)`](#iscomplete) is false)

Raises a [`exceptions.PatternNotFoundError`](#exceptionspatternnotfounderror) if `patt` isn't a known pattern

### `.add()`
Params:
- `name`: `str`
- `patt`: `str`
- (kw-only) `replace`: `bool` = `False`

[Adds a new pattern](#adding-a-pattern), but raises a [`exceptions.PatternExistsError`](#exceptionspatternexistserror) if `name` already specifies a pattern and `replace` is false

#### `.multiadd()`
Params:
- `patts`: `dict` (`str` -> `str`)
- (kw-only) `replace`: `bool` = `False`


### `.update()`
#### `.multiupdate()`
### `.remove()`
### `.is_complete()`
#### `.list_incomplete()`
### `.find_referrers()`
#### `.find_referrers_recursive()`
