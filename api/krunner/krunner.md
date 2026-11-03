---
title: "KRunner Namespace"
description: "Framework for Plasma runners."
---

# KRunner Namespace

Framework for Plasma runners. [More...](#details)

- Header: KRunner
- CMake: find\_package(KF6 REQUIRED COMPONENTS Runner) target\_link\_libraries(mytarget PRIVATE KF6::Runner)

## Detailed Description {#details}

## Classes {#classes}

### class [AbstractRunner](krunner-abstractrunner.md)

An abstract base class for Plasma Runner plugins.

### class [Action](krunner-action.md)

This class represents an action that will be shown next to a match.

### class [QueryMatch](krunner-querymatch.md)

A match returned by an [AbstractRunner](krunner-abstractrunner.md) in response to a given [RunnerContext](krunner-runnercontext.md).

### class [ResultsModel](krunner-resultsmodel.md)

A model that exposes and sorts results for a given query.

### class [RunnerContext](krunner-runnercontext.md)

The [RunnerContext](krunner-runnercontext.md) class provides information related to a search, including the search term and collected matches.

### class [RunnerManager](krunner-runnermanager.md)

The [RunnerManager](krunner-runnermanager.md) class decides what installed runners are runnable, and their ratings. It is the main proxy to the runners.

### class [RunnerSyntax](krunner-runnersyntax.md)

Represents a query prototype that the runner accepts.
