# About this document

This is a Work in Progress.

This document describes a format for storing Static Prediction Tables.

It is possible that some of all of this format will be usable as part of
individual compressed source files, to be determined.

# About Static Prediction Tables (SPT)

A Static Prediction Table is a form of external dictionary, shipped either
with the JavaScript VM, or separately, and which may be referenced by any
number of compressed Binary AST Source Files.

Shipping Static Prediction Tables makes it possible to considerably reduce
the size of individual compressed files.

This document does not attempt to document how and when a SPT is loaded,
or how and when an individual compressed file references a SPT.

# Design guidelines

- A SPT must be usable by many compressed source files.
- A VM must be able to manage several SPTs simultaneously.
- As JavaScript is a changing language, a SPT that is complete at a given point in time may not be expected to remain
  complete forever.
- As Binary AST never reuses the same interface name for distinct purposes, a Path in the AST that is valid at a point
  in time will remain valid forever.
- For upgrade purposes, a SPT may be defined as an amendment to another SPT.
- A SPT may define additional strings of various natures.

# Format

## Header

The header:
- specifies the kind of file;
- references the grammar version;
- optionally, references a SPT file it amends.

TBD

## Tables of Strings

These tables add new strings that may be referenced both in the tables of probabilities
and in the compressed files.

### Table of property keys
TBD

### Table of string enum constants

This table adds string enum constants. It is used when updating the JavaScript grammar.

TBD

### Table of interface names

This table adds interface names. It is used when updating the JavaScript grammar.

TBD

### Table of literal strings
TBD

### Table of identifier names
TBD


## Tables of Probabilities

These tables increase or reset to 0 the number of instances of (value) at (path).

Entries with depth N look like:
- list of
  - the Path itself, as a list of exactly N entries of
    - InterfaceName (as a number, exact format to be determined)
    - Field index
  - the distribution at this Path, as a list of
    - Field index
    - Value (format to be determined)
    - Number of instances, where
      - 0 means that we remove this (Path, Field, Value) from the probability table
      - otherwise, if (Path, Field, Value) was in the probability table, we increase its previous number of instances
      - otherwise, we add (Path, Field, Value) to the probability table with `Number of instances` instances.

The table of probabilities contains
- One entry of depth 0, with a single field: the root.
- Entries of depth 1, for possible children of the root.
- Entries of depth 2, for possible grandchildren of the root.
- ...
- Entries of depth D, for all other nodes.


TBD
