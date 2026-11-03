---
title: "Attica::AccountBalance Class"
description: "Represents the money in the account of the user."
---

# Attica::AccountBalance Class

Represents the money in the account of the user. [More...](#details)

- **Header:** `#include <Attica/AccountBalance>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-accountbalance-members.md)

## Public Types

- [AccountBalance::List](#List-typedef)

## Public Functions

- [AccountBalance()](#AccountBalance)
- [QString balance() const](#balance)
- [QString currency() const](#currency)
- [void setBalance(const QString &name)](#setBalance)
- [void setCurrency(const QString &currency)](#setCurrency)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### AccountBalance::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### AccountBalance::AccountBalance() {#AccountBalance}

Creates an empty [AccountBalance](attica-accountbalance.md)

### QString AccountBalance::balance() const {#balance}

Returns the amount of money in the account

*See also* [setBalance](attica-accountbalance.md#setBalance)()

### QString AccountBalance::currency() const {#currency}

Returns the currency.

*See also* [setCurrency](attica-accountbalance.md#setCurrency)()

### void AccountBalance::setBalance(const QString &*name*) {#setBalance}

Sets the balance.

`balance`

*See also* [balance](attica-accountbalance.md#balance)()

### void AccountBalance::setCurrency(const QString &*currency*) {#setCurrency}

Sets the currency in use.

`currency` the new currency (Euro, US Dollar)

*See also* [currency](attica-accountbalance.md#currency)()
