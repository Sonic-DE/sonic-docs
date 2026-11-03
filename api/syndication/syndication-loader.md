---
title: "Syndication::Loader Class"
description: "This class is the preferred way of loading feed sources."
---

# Syndication::Loader Class

This class is the preferred way of loading feed sources. [More...](#details)

- **Header:** `#include <Syndication/Loader>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](syndication-loader-members.md)

## Public Functions

- [void abort()](#abort)
- [QUrl discoveredFeedURL() const](#discoveredFeedURL)
- [Syndication::ErrorCode errorCode() const](#errorCode)
- [void loadFrom(const QUrl &url, Syndication::DataRetriever \*retriever)](#loadFrom)
- [int retrieverError() const](#retrieverError)

## Signals

- [void loadingComplete(Syndication::Loader \*loader, Syndication::FeedPtr feed, Syndication::ErrorCode error)](#loadingComplete)

## Static Public Members

- [Syndication::Loader \*create()](#create)
- [Syndication::Loader \*create(QObject \*object, const char \*slot)](#create-1)

## Detailed Description {#details}

Usage is very straightforward:

```cpp
Loader *loader = Loader::create();
connect(loader, SIGNAL(loadingComplete(Loader*, FeedPtr, ErrorCode)),
        this, SLOT(slotLoadingComplete(Loader*, FeedPtr, ErrorCode)));
loader->loadFrom("http://www.blah.org/foobar.rdf");
```

This creates a Loader object, connects it's [loadingComplete](syndication-loader.md#loadingComplete)() signal to your custom slot and then makes it load the file 'http://www.blah.org/foobar.rdf'. You could've done something like this as well:

```cpp
// create the Loader, connect it's signal...
loader->loadFrom("/home/myself/some-script.py", new OutputRetriever);
```

That'd make the Loader use a custom algorithm for retrieving the RSS data; 'OutputRetriever' will make it execute the script '/home/myself/some-script.py' and assume whatever that script prints to stdout is RSS/Azom markup. This is e.g. handy for conversion scripts, which download a HTML file and convert it's contents into RSS markup.

No matter what kind of retrieval algorithm you employ, your 'slotLoadingComplete' method might look like this:

```cpp
void MyClass::slotLoadingComplete(Loader* loader, FeedPtr feed, ErrorCode status)
{
    // Note that Loader::~Loader() is private, so you cannot delete Loader instances.
    // You don't need to do that anyway since Loader instances delete themselves.

    if (status != Syndication::Success)
        return;

    QString title = feed->title();
    // do whatever you want with the information.
}
```

## Member Function Documentation {#member-function-documentation}

### void Loader::abort() {#abort}

aborts the loading process

### \[static\] Syndication::Loader \*Loader::create() {#create}

Constructs a Loader instance.

This is pretty much what the default constructor would do, except that it ensures that all Loader instances have been allocated on the heap (this is required so that Loader's can delete themselves safely after they emitted the [loadingComplete](syndication-loader.md#loadingComplete)() signal.).

Returns a pointer to a new Loader instance.

### \[static\] Syndication::Loader \*Loader::create(QObject \**object*, const char \**slot*) {#create-1}

Convenience method.

Does the same as the above method except that it also does the job of connecting the [loadingComplete](syndication-loader.md#loadingComplete)() signal to the given slot for you.

`object` A [QObject](https://doc.qt.io/qt-6/qobject.html) which features the specified slot

`slot` Which slot to connect to.

### QUrl Loader::discoveredFeedURL() const {#discoveredFeedURL}

returns the URL of a feed discovered in the feed source

### Syndication::ErrorCode Loader::errorCode() const {#errorCode}

Retrieves the error code of the last loading process (if any).

### void Loader::loadFrom(const QUrl &*url*, Syndication::DataRetriever \**retriever*) {#loadFrom}

Loads the feed source referenced by the given URL using the specified retrieval algorithm.

Make sure that you connected to the [loadingComplete](syndication-loader.md#loadingComplete)() signal before calling this method so that you're guaranteed to get notified when the loading finished.

> **Note:** A Loader object cannot load from multiple URLs simultaneously; consequently, subsequent calls to loadFrom will be discarded silently, only the first loadFrom request will be executed.

`url` A URL referencing the input file.

`retriever` A subclass of [DataRetriever](syndication-dataretriever.md) which implements a specialized retrieval behaviour. Note that the ownership of the retriever is transferred to the Loader, i.e. the Loader will delete it when it doesn't need it anymore.

*See also* [DataRetriever](syndication-dataretriever.md), [Loader::loadingComplete](syndication-loader.md#loadingComplete)()

### \[signal\] void Loader::loadingComplete(Syndication::Loader \**loader*, Syndication::FeedPtr *feed*, Syndication::ErrorCode *error*) {#loadingComplete}

This signal gets emitted when the loading process triggered by calling [loadFrom](syndication-loader.md#loadFrom)() finished.

`loader` A pointer pointing to the loader object which emitted this signal; this is handy in case you connect multiple loaders to a single slot.

`feed` In case errortus is Success, this parameter holds the parsed feed. If fetching/parsing failed, feed is NULL.

`error` An error code telling whether there were any problems while retrieving or parsing the data.

*See also* [Feed](syndication-feed.md), [ErrorCode](syndication.md#ErrorCode-enum)

### int Loader::retrieverError() const {#retrieverError}

the error code returned from the retriever. Use this if you use your custom retriever implementation and need the specific error, not covered by [errorCode](syndication-loader.md#errorCode)().
