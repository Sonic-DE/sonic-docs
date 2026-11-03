---
title: "KRunner::RunnerSyntax Class"
description: "Represents a query prototype that the runner accepts."
---

# KRunner::RunnerSyntax Class

Represents a query prototype that the runner accepts. [More...](#details)

- **Header:** `#include <KRunner/RunnerSyntax>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Runner)`  
  `target_link_libraries(mytarget PRIVATE KF6::Runner)`

[List of all members, including inherited members](krunner-runnersyntax-members.md)

## Public Functions

- [RunnerSyntax(const QString &exampleQuery, const QString &description)](#RunnerSyntax)
- [RunnerSyntax(const QStringList &exampleQueries, const QString &description)](#RunnerSyntax-1)
- [QString description() const](#description)
- [QStringList exampleQueries() const](#exampleQueries)

## Detailed Description {#details}

These can be created and registered with [AbstractRunner::addSyntax](krunner-abstractrunner.md#addSyntax) to allow applications to show to the user what the runner is currently capable of doing.

Lets say the runner has a trigger word and then the user can type anything after that. In that case you could use ":q:" as a placeholder, which will get expanded to i18n("search term") and be put in brackets.

```cpp
KRunner::RunnerSyntax syntax(QStringLiteral("sometriggerword :q:"), i18n("Description for this syntax"));
addSyntax(syntax);
```

But if the query the user has to enter is sth. specific like a program, url or file you should use a custom placeholder to make it easier to understand.

```cpp
KRunner::RunnerSyntax syntax(QStringLiteral("sometriggereword <%1>").arg(i18n("program name"))), i18n("Description for this syntax"));
addSyntax(syntax);
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] RunnerSyntax::RunnerSyntax(const QString &*exampleQuery*, const QString &*description*) {#RunnerSyntax}

Constructs a [RunnerSyntax](krunner-runnersyntax.md) with one example query

`exampleQuery` See the class description for examples and placeholder conventions.

`description` A description of what the described syntax does from the user's point of view.

### \[explicit\] RunnerSyntax::RunnerSyntax(const QStringList &*exampleQueries*, const QString &*description*) {#RunnerSyntax-1}

Constructs a [RunnerSyntax](krunner-runnersyntax.md) with multiple example queries

`exampleQueries` See the class description for examples and placeholder conventions.

`description` A description of what the described syntax does from the user's point of view. This description should be true for all example queries. In case they differ, consider using multiple syntaxes.

### QString RunnerSyntax::description() const {#description}

Returns the user visible description of what the syntax does

### QStringList RunnerSyntax::exampleQueries() const {#exampleQueries}

Returns the example queries associated with this Syntax object
