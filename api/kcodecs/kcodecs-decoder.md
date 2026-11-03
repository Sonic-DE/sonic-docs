---
title: "KCodecs::Decoder Class"
description: "Stateful CTE decoder class."
---

# KCodecs::Decoder Class

Stateful CTE decoder class. [More...](#details)

- **Header:** `#include <KCodecs>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Codecs)`  
  `target_link_libraries(mytarget PRIVATE KF6::Codecs)`

[List of all members, including inherited members](kcodecs-decoder-members.md)

## Public Functions

- [bool decode(const char \*&scursor, const char \*const send, char \*&dcursor, const char \*const dend)](#decode)
- [bool finish(char \*&dcursor, const char \*const dend)](#finish)

## Protected Functions

- [Decoder(KCodecs::Codec::NewlineType newline = Codec::NewlineLF)](#Decoder)

## Detailed Description {#details}

Stateful decoder class, modelled after [QTextDecoder](https://doc.qt.io/qt-6/qtextdecoder.html).

### Overview {#overview}

[KCodecs](kcodecs-module.md) decoders are designed to be able to process encoded data in chunks of arbitrary size and to work with output buffers of also arbitrary size. They maintain any state necessary to go on where the previous call left off.

The class consists of only two methods of interest: see decode, which decodes an input block and finalize, which flushes any remaining data to the output stream.

Typically, you will create a decoder instance, call decode as often as necessary, then call finalize (most often a single call suffices, but it might be that during that call the output buffer is filled, so you should be prepared to call finalize as often as necessary, i.e. until it returns `true`).

### Return Values {#return-values}

Both methods return `true` to indicate that they've finished their job. For decode, a return value of `true` means that the current input block has been finished (`false` most often means that the output buffer is full, but that isn't required behavior. The decode call is free to return at arbitrary times during processing).

For finalize, a return value of `true` means that all data implicitly or explicitly stored in the decoder instance has been flushed to the output buffer. A `false` return value should be interpreted as "check if the output buffer is full and call me again", just as with decode.

### Usage Pattern {#usage-pattern}

Since the decoder maintains state, you can only use it once. After a sequence of input blocks has been processed, you finalize the output and then delete the decoder instance. If you want to process another input block sequence, you create a new instance.

Typical usage (`in` contains the (base64-encoded) input data), taking into account all the conventions detailed above:

```cpp
KCodecs::Codec *codec = KCodecs::Codec::codecForName("base64");
if (!codec) {
    qFatal() << "No codec found for base64!";
}
KCodecs::Decoder *dec = codec->makeDecoder();
Q_ASSERT(dec); // should not happen
QByteArray out(256); // small buffer is enough ;-)
QByteArray::Iterator iit = in.begin();
QByteArray::Iterator oit = out.begin();
// decode the chunk
while (!dec->decode(iit, in.end(), oit, out.end()))
  if (oit == out.end()) { // output buffer full, process contents
    do_something_with(out);
    oit = out.begin();
  }
// repeat while loop for each input block
// ...
// finish (flush remaining data from decoder):
while (!dec->finish(oit, out.end()))
  if (oit == out.end()) { // output buffer full, process contents
    do_something_with(out);
    oit = out.begin();
  }
// now process last chunk:
out.resize(oit - out.begin());
do_something_with(out);
// _delete_ the decoder, but not the codec:
delete dec;
```

## Member Function Documentation {#member-function-documentation}

### \[protected\] Decoder::Decoder(KCodecs::Codec::NewlineType *newline* = Codec::NewlineLF) {#Decoder}

Protected constructor. Use [KCodecs::Codec::makeDecoder](kcodecs-codec.md#makeDecoder) to create an instance.

`newline` whether make new lines using CRLF, or LF (default is LF).

### \[pure virtual\] bool Decoder::decode(const char \*&*scursor*, const char \*const *send*, char \*&*dcursor*, const char \*const *dend*) {#decode}

Decodes a chunk of data, maintaining state information between calls. See class decumentation for calling conventions.

`scursor` is a pointer to the start of the input buffer.

`send` is a pointer to the end of the input buffer.

`dcursor` is a pointer to the start of the output buffer.

`dend` is a pointer to the end of the output buffer.

Returns true on success

### \[pure virtual\] bool Decoder::finish(char \*&*dcursor*, const char \*const *dend*) {#finish}

Call this method to finalize the output stream. Writes all remaining data and resets the decoder. See [KCodecs::Codec](kcodecs-codec.md) for calling conventions.

`dcursor` is a pointer to the start of the output buffer.

`dend` is a pointer to the end of the output buffer.

Returns true on success
