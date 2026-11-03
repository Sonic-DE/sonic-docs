---
title: "KCodecs::Encoder Class"
description: "Stateful encoder class."
---

# KCodecs::Encoder Class

Stateful encoder class. [More...](#details)

- **Header:** `#include <KCodecs>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Codecs)`  
  `target_link_libraries(mytarget PRIVATE KF6::Codecs)`

[List of all members, including inherited members](kcodecs-encoder-members.md)

## Public Functions

- [bool encode(const char \*&scursor, const char \*const send, char \*&dcursor, const char \*const dend)](#encode)
- [bool finish(char \*&dcursor, const char \*const dend)](#finish)

## Protected Functions

- [Encoder(KCodecs::Codec::NewlineType newline = Codec::NewlineLF)](#Encoder)
- [bool flushOutputBuffer(char \*&dcursor, const char \*const dend)](#flushOutputBuffer)
- [bool write(char ch, char \*&dcursor, const char \*const dend)](#write)
- [bool writeCRLF(char \*&dcursor, const char \*const dend)](#writeCRLF)

## Detailed Description {#details}

Stateful encoder class, modeled after [QTextEncoder](https://doc.qt.io/qt-6/qtextencoder.html).

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] Encoder::Encoder(KCodecs::Codec::NewlineType *newline* = Codec::NewlineLF) {#Encoder}

Protected constructor. Use [KCodecs::Codec::makeEncoder](kcodecs-codec.md#makeEncoder) if you want one.

`newline` whether make new lines using CRLF, or LF (default is LF).

### \[pure virtual\] bool Encoder::encode(const char \*&*scursor*, const char \*const *send*, char \*&*dcursor*, const char \*const *dend*) {#encode}

Encodes a chunk of data, maintaining state information between calls. See [KCodecs::Codec](kcodecs-codec.md) for calling conventions.

`scursor` is a pointer to the start of the input buffer.

`send` is a pointer to the end of the input buffer.

`dcursor` is a pointer to the start of the output buffer.

`dend` is a pointer to the end of the output buffer.

Returns true on success

### \[pure virtual\] bool Encoder::finish(char \*&*dcursor*, const char \*const *dend*) {#finish}

Call this method to finalize the output stream. Writes all remaining data and resets the encoder. See [KCodecs::Codec](kcodecs-codec.md) for calling conventions.

`dcursor` is a pointer to the start of the output buffer.

`dend` is a pointer to the end of the output buffer.

Returns true on success.

### \[protected\] bool Encoder::flushOutputBuffer(char \*&*dcursor*, const char \*const *dend*) {#flushOutputBuffer}

Writes characters from the output buffer to the output stream. Implementations of encode and finish should call this at the very beginning and for each iteration of the while loop.

`dcursor` is a pointer to the start of the output buffer.

`dend` is a pointer to the end of the output buffer.

Returns true if all chars could be written, false otherwise

### \[protected\] bool Encoder::write(char *ch*, char \*&*dcursor*, const char \*const *dend*) {#write}

Writes character `ch` to the output stream or the output buffer, depending on whether or not the output stream has space left.

`ch` is the character to write.

`dcursor` is a pointer to the start of the output buffer.

`dend` is a pointer to the end of the output buffer.

Returns true if written to the output stream; else false if buffered.

### \[protected\] bool Encoder::writeCRLF(char \*&*dcursor*, const char \*const *dend*) {#writeCRLF}

Convenience function. Outputs LF or CRLF, based on the state of mWithCRLF.

`dcursor` is a pointer to the start of the output buffer.

`dend` is a pointer to the end of the output buffer.

Returns true on success
