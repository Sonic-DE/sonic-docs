---
title: "KRunner C++ Classes"
description: "Framework for Plasma runners."
---

# KRunner C++ Classes

Framework for Plasma runners. [More...](#details)

## Namespaces {#namespaces}

- [KRunner](krunner.md)

## Classes {#classes}

- [KRunner::AbstractRunner](krunner-abstractrunner.md): An abstract base class for Plasma Runner plugins.
- [KRunner::Action](krunner-action.md): This class represents an action that will be shown next to a match.
- [KRunner::QueryMatch](krunner-querymatch.md): A match returned by an AbstractRunner in response to a given RunnerContext.
- [KRunner::ResultsModel](krunner-resultsmodel.md): A model that exposes and sorts results for a given query.
- [KRunner::RunnerContext](krunner-runnercontext.md): The RunnerContext class provides information related to a search, including the search term and collected matches.
- [KRunner::RunnerManager](krunner-runnermanager.md): The RunnerManager class decides what installed runners are runnable, and their ratings. It is the main proxy to the runners.
- [KRunner::RunnerSyntax](krunner-runnersyntax.md): Represents a query prototype that the runner accepts.

## Detailed Description {#details}
