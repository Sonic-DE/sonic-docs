---
title: "KWordMacroExpander Class"
description: "Abstract base class for simple word macro substitutors."
---

# KWordMacroExpander Class

Abstract base class for simple word macro substitutors. [More...](#details)

- **Header:** `#include <KMacroExpander>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [KMacroExpanderBase](kmacroexpanderbase.md)

[List of all members, including inherited members](kwordmacroexpander-members.md)

## Public Functions

- [KWordMacroExpander(QChar c = QLatin1Char('%'))](#KWordMacroExpander)

## Protected Functions

- [bool expandMacro(const QString &str, QStringList &ret)](#expandMacro)

## Detailed Description {#details}

Use this instead of the functions in the [KMacroExpander](kmacroexpander.md) namespace if speculatively pre-filling the substitution map would be too expensive.

A typical application:

```cpp
class MyClass {
...
  private:
    QString m_str;
...
  friend class MyExpander;
};

class MyExpander : public KWordMacroExpander {
  public:
    MyExpander( MyClass *_that ) : KWordMacroExpander(), that( _that ) {}
  protected:
    virtual bool expandMacro( const QString &str, QStringList &ret );
  private:
    MyClass *that;
};

bool MyExpander::expandMacro( const QString &str, QStringList &ret )
{
  if (str == "macro") {
    ret += complexOperation( that->m_str );
    return true;
  }
  return false;
}

... MyClass::...(...)
{
  QString str;
  ...
  MyExpander mx( this );
  mx.expandMacrosShellQuote( str );
  ...
}
```

Alternatively MyClass could inherit from [KWordMacroExpander](kwordmacroexpander.md) directly.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KWordMacroExpander::KWordMacroExpander(QChar *c* = QLatin1Char('%')) {#KWordMacroExpander}

Constructor.

`c` escape char indicating start of macros, or QChar::null for none

### \[pure virtual protected\] bool KWordMacroExpander::expandMacro(const QString &*str*, QStringList &*ret*) {#expandMacro}

Return substitution list `ret` for string macro `str`.

`str` the macro to expand

`ret` return variable reference. It is guaranteed to be empty when expandMacro is entered.

Returns true iff `str` was a recognized macro name
