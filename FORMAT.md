# Caveat

This is a very early WIP.

# About this file

The container format for the JavaScript Binary AST.

The container format is mostly neutral wrt the underlying grammar.
The grammar itself is defined and maintained separately, at
[https://github.com/binast/ecmascript-binary-ast](https://github.com/binast/ecmascript-binary-ast).

In this file, we attempt to discuss both the binary layout
and the algorithms used to map the grammar to the layout.

# About this format

**TBD**

# The file format

## Header

The header serves to indicate:
- that it's a binast file;
- which version of the container format we're using;
- which version of the language/grammar we're referring to;
- which static dictionaries we're referring to.

### Format

**TBD**

## Packet

This is a streaming format. The encoder + server sends packets. The decoder receives packets.
The size of packets is variable and picked by the encoder.

Each packet is processed sequentially by the decoder. Some packets may (temporarily) be skipped,
if they contain lazy data that is not necessary yet.

Packets contain:
- updates to the dictionaries (e.g. new strings);
- ast nodes;
- **TBD** what else?

### Format

**TBD**
