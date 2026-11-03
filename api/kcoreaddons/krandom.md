---
title: "KRandom Namespace"
description: "Helper to create random data."
---

# KRandom Namespace

Helper to create random data. [More...](#details)

- Header: KRandom
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

This namespace provides methods which generate random data. [KRandom](krandom.md) is not recommended for serious random-number generation needs, like cryptography.

## Function Documentation {#function-documentation}

### QString KRandom::randomString(int *length*) {#randomString}

Generates a random string. It operates in the range \[A-Za-z0-9\]

`length` Generate a string of this length.

Returns the random string

### template \<typename T\> void KRandom::shuffle(T &*container*) {#shuffle}

Reorders the elements of the given container randomly.

The container needs to implement size() and T &operator\[\]

### template \<typename T\> void KRandom::shuffle(T &*container*, QRandomGenerator \**generator*) {#shuffle-1}

Reorders the elements of the given container randomly using the given random number generator.

The container needs to implement size() and T &operator\[\]
