---
title: "KNSCore Namespace"
description: "The KNewStuff core."
---

# KNSCore Namespace

The KNewStuff core. [More...](#details)

- Header: KNSCore
- CMake: find\_package(KF6 REQUIRED COMPONENTS NewStuff) target\_link\_libraries(mytarget PRIVATE KF6::NewStuff)

## Detailed Description {#details}

## Namespaces {#namespaces}

### namespace KNSCore::ErrorCode

## Classes {#classes}

### class [Author](knscore-author.md)

KNewStuff author information.

### class [CategoryMetadata](knscore-categorymetadata.md)

Describes a category.

### class [CommentsModel](knscore-commentsmodel.md)

A model which takes care of the comments for a single Entry.

### class [EngineBase](knscore-enginebase.md)

KNewStuff engine.

### class [Entry](knscore-entry.md)

KNewStuff data entry container.

### class [ProvidersModel](knscore-providersmodel.md)

A model which holds information on all known Providers for a specific Engine.

### class [Question](knscore-question.md)

A way to ask a user a question from inside a GUI-less library (like [KNewStuffCore](knewstuffcore-module.md)).

### class [QuestionListener](knscore-questionlistener.md)

Implementation-side handler class for questions sent from [KNewStuffCore](knewstuffcore-module.md).

### class [QuestionManager](knscore-questionmanager.md)

The central class handling Question redirection.

### class [ResultsStream](knscore-resultsstream.md)

The [ResultsStream](knscore-resultsstream.md) is returned by EngineBase::search. It is used to communicate the different entries in response to a request using the signal `entriesFound`.

### class [TagsFilterChecker](knscore-tagsfilterchecker.md)

Apply simple filtering logic to a list of tags.

### class [Transaction](knscore-transaction.md)

KNewStuff Transaction.

## Function Documentation {#function-documentation}

### QString KNSCore::replaceBBCode(const QString &*unformattedText*) {#replaceBBCode}

function to remove bb code formatting that opendesktop sends
