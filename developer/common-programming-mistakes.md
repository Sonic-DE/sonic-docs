---
title: Common programming mistakes
description: Common C++ and Qt programming mistakes to avoid.
source_url: https://develop.kde.org/docs/getting-started/common-programming-mistakes/
source_authors: [Carl Schwan, Johnny Jazeix, KPaulo Victor, Mark Penner, Matej Starc, Sam Crawford, Thiago Sueto, Tusooa Windy]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: C++ standard ([basic.link], [lex.name], [support.types.nullptr]); Qt 6.11 documentation and headers (QGlobalStatic, QTimer, QString, QDomNode, Q_MOC_INCLUDE); the code snippets marked below were compiled with GCC and Qt 6.11.3
---

# Common programming mistakes

This page collects experience with what to do and what not to do with Qt and the libraries SonicDE builds on. Besides actual mistakes, it covers things that aren't bugs but make code slower or harder to read.

## General C++

Some dusty corners of C++ that tend to be misused or simply gotten wrong.

### Unnamed namespaces and static

If a member function of a class doesn't use any members, and so needs no object, make it `static`. If it is also a private helper that isn't needed outside its file, make it a file-local function, so its symbol isn't visible outside the file.

For file-local functions and variables you can use either `static` or an unnamed namespace: since C++11, everything declared in an unnamed namespace has internal linkage, just like `static`. An unnamed namespace can also hold types, which `static` can't make file-local. Entities with internal linkage can be used as template arguments (also since C++11).

### Null pointers

First of all, deleting a null pointer is fine, so checking for null before deleting is redundant:

```cpp
if (ptr) {
    delete ptr;
}
```

When you delete through a pointer that stays around, set it to null, so a later delete doesn't delete the object twice:

```cpp
delete ptr;
ptr = nullptr;
```

Null pointers are written in four ways: `0`, `0L`, `NULL` and `nullptr`. In C, `NULL` is usually a null `void` pointer. In C++, `NULL` is an implementation-defined null pointer constant: an integer zero, or a compiler built-in such as GCC's `__null`, but not `nullptr`, so it can be passed or assigned where an integer is expected. `nullptr` has its own type, `std::nullptr_t`: it converts to any pointer type and can be tested as `false`, but doesn't convert to an integer. Use `nullptr`.

In pointer context, the integer constant zero means "null pointer", whatever the null pointer's actual bit pattern. But to pass a null pointer as a variadic argument (`...`), cast it to the pointer type: there the compiler assumes an integer, which may not match a pointer.

### Member variables

Besides unmarked members, you will meet four styles of marking member variables in the code SonicDE builds on:

- *m_variable*: lowercase m, underscore, and the name starting with a lowercase letter. This is the most common style, and the one preferred in the frameworks.
- *mVariable*: lowercase m and the name starting with an uppercase letter.
- *variable_*: the name starting with a lowercase letter, then an underscore.
- *_variable*: underscore and the name starting with a lowercase letter. This style is usually frowned upon, because some code uses it for function parameters.

Unmarked members are more common in classes that use [d-pointers](https://community.kde.org/Policies/Library_Code_Policy#D-Pointers).

There is no single right way: follow the style of the application or library you contribute to. In a new file, follow the style of the library or module you add it to.

Names that start with an underscore followed by an uppercase letter, and names that contain a double underscore, are reserved everywhere; names that start with an underscore are also reserved in the global namespace. A member called `_variable` is allowed, but it is safer to avoid leading underscores altogether.

### Static variables

Keep the number of static variables in your code small, especially in a library: constructing and initializing many static objects really hurts startup time.

Don't use class-static objects, especially not in libraries and loadable modules, and preferably not in applications either: static objects cause problems such as hard-to-debug crashes from the undefined order of construction and destruction.

Instead, use `Q_GLOBAL_STATIC` from `<QGlobalStatic>`, which creates the object on first use:

```cpp
class A { ... };

Q_GLOBAL_STATIC(A, globalA)

void doSomething()
{
    A *a = globalA;
    ...
}

void doSomethingElse() {
    if (globalA.isDestroyed()) {
        return;
    }
    A *a = globalA;
    ...
}
```

`isDestroyed()` tells you whether the object has already been destroyed, which can happen during program exit. See the [Q_GLOBAL_STATIC documentation](https://doc.qt.io/qt-6/qglobalstatic.html) for more.

### Constant data

If you need constant data of simple types in several places, define it once in a central place. That avoids typos in one of the copies, and if the value changes, there is only one place to edit.

Even if you use it only once, defining it separately avoids unexplained "magic numbers" in the code (compare 42). Usually this is done at the top of the file, so it is easy to find.

Define constants with C++ language features, not preprocessor macros as in plain C, so the compiler can check their types:

```cpp
// Correct!
static constexpr int AnswerToAllQuestions = 42;

// Wrong!
#define AnswerToAllQuestions 42
```

For a constant array, don't use a pointer type. Use the element type with `[]` after the name. Otherwise you also define a variable pointing to the constant data, which could accidentally be assigned another pointer without the compiler complaining, and every access goes through the variable first.

```cpp
// Correct!
static const char SomeString[] = "Example";

// Wrong!
static const char* SomeString = "Example";

// Wrong!
#define SomeString "Example"
```

### Forward declarations

Forward-declaring classes instead of including their headers reduces compile time. The rules for when a type may be used without its definition are subtle, but roughly: if only the class's name matters, not its implementation, a forward declaration is enough. Two examples are pointers to the class and function parameters of the class's type.

For example:

```cpp
#include <QWidget>     // slow
#include <QStringList> // slow
#include <QString>     // slow
#include <QIcon>       // slow

class SomeClass
{
public:
    virtual void widgetAction(QWidget *widget) = 0;
    virtual void stringAction(const QString &str) = 0;
    virtual void stringListAction(const QStringList &strList) = 0;
private:
    QIcon *icon = nullptr;
};
```

should be written like this:

```cpp
class QWidget;     // fast
class QStringList; // fast
class QString;     // fast
class QIcon;       // fast

class SomeClass
{
public:
    virtual void widgetAction(QWidget *widget) = 0;
    virtual void stringAction(const QString &str ) = 0;
    virtual void stringListAction( const QStringList& strList ) = 0;
private:
    QIcon *icon = nullptr;
};
```

In Qt 6, if a `Q_INVOKABLE` function (including signals and slots) or a property of a `QObject` subclass uses a pointer or reference to a forward-declared type, you may need [Q_MOC_INCLUDE()](https://doc.qt.io/qt-6/qobject.html#Q_MOC_INCLUDE), because moc needs the complete type. See Qt's [porting notes on type registration](https://doc.qt.io/qt-6/qtcore-changes-qt6.html#type-registration).

## Iterators

### Prefer const iterators and cache end()

Prefer `const_iterator`s to normal iterators where you can. Implicitly shared containers, such as [QList](https://doc.qt.io/qt-6/qlist.html), often detach when you call their non-const `begin()` or `end()`. With a `const_iterator`, make sure the const versions of `begin()` and `end()` are really called: unless the container itself is const, they probably aren't, which may detach the container needlessly. So initialize const iterators with `constBegin()` and `constEnd()` to be safe.

Store the result of `end()` (or `constEnd()`) before iterating over large containers, so it isn't called again on every pass:

```cpp
QList<SomeClass> container;

// code which inserts a large number of elements to the container

QList<SomeClass>::ConstIterator end = container.constEnd();
QList<SomeClass>::ConstIterator itr = container.constBegin();

for (; itr != end; ++itr ) {
    // use *itr here
}
```

With iterators, use pre-increment and pre-decrement (`++itr`) unless you have a reason not to: post-increment and post-decrement (`itr++`) create a temporary object.

### Take care when erasing elements in a loop

To erase some elements from a container, you might write:

```cpp
QMap<int, Job *>::iterator it = m_activeTimers.begin();
QMap<int, Job *>::iterator itEnd = m_activeTimers.end();

for(; it != itEnd ; ++it) {
    if(it.value() == job) {
        // A timer for this job has been found. Let's stop it.
        killTimer(it.key());
        m_activeTimers.erase(it);
    }
}
```

This can crash: after `erase()`, `it` is a dangling iterator. Write it like this instead:

```cpp
QMap<int, Job *>::iterator it = m_activeTimers.begin();
while (it != m_activeTimers.end()) {
    if(it.value() == job) {
        // A timer for this job has been found. Let's stop it.
        killTimer(it.key());
        it = m_activeTimers.erase(it);
        continue;
    }
    ++it;
}
```

The [QMap::iterator documentation](https://doc.qt.io/qt-6/qmap-iterator.html#details) discusses this too, but it applies to **all** Qt iterators.

## Memory leaks

A very "popular" mistake is a `new` without a `delete`, as in this program:

```cpp
class t {
public:
    t() {}
};

void pollute() {
    t* polluter = new t();
}

int main() {
    while (true) {
        pollute();
    }
}
```

`pollute()` creates a new `t` object on the heap. The local variable `polluter` goes away, but the object stays on the heap. This program can make a computer unusable within seconds.

Solutions:

- Keep the object on the stack instead of the heap:

  ```cpp
  t* polluter = new t();
  ```

  becomes

  ```cpp
  t polluter;
  ```

- Delete it with the counterpart of `new`:

  ```cpp
  delete polluter;
  ```

- Put it in a [std::unique_ptr](https://en.cppreference.com/w/cpp/memory/unique_ptr), which deletes it automatically when the function returns:

  ```cpp
  std::unique_ptr<t> polluter = std::make_unique<t>();
  ```

There are also `std::shared_ptr` and `QSharedPointer`. Smart pointers are the generally preferred way in modern C++; avoid explicit memory management where you can.

Qt code with QObjects usually uses parent and child relations to free memory: a QObject (a widget, for example) can be given a parent when it is created, and when the parent is deleted it deletes all its children. Adding a widget to a layout also sets its parent.

[Valgrind](https://community.kde.org/Guidelines_and_HOWTOs/Debugging/Valgrind) finds memory leaks like this one.

## dynamic_cast

You can only `dynamic_cast` to type T from type T2 if:

- T is defined in a library you link to (otherwise you get a linker error, because its vtable or RTTI information isn't found);
- T is "well anchored" in that library: its vtable isn't a COMMON symbol that the dynamic linker merges at run time. In other words, the class's first virtual function must exist and must not be inline: it must be defined in a `.cpp` file;
- T and T2 are exported.

KDE developers once ran into hard-to-track problems with non-KDE C++ code they linked with (NMM, a multimedia framework) because of this:

- libphonon loaded the NMM plugin;
- the NMM plugin linked to NMM;
- NMM loaded its own plugins;
- NMM's own plugins linked to NMM.

Some NMM classes had no well-anchored vtables, so `dynamic_cast` failed in the Phonon NMM plugin for objects created in NMM's own plugins.

SonicDE's CMake settings (`KDECompilerSettings`) build with hidden symbol visibility by default, so only exported classes have visible type information across libraries.

## Program design

Common problems in the design of Qt applications.

## Delayed initialization

Even complex applications can show their window quickly by delaying initialization. The technique is simple and useful at every stage of an interactive program.

A typical `main()` creates the main window before starting the event loop:

```cpp
int main(int argc, char **argv) {
    QApplication app(argc, argv);

    QCommandLineParser parser;
    // ... add options
    parser.process(app);

    auto window = new MainWindow(parser);
    window->show();

    return app.exec();
}
```

`window` is created before `app.exec()` starts the event loop. So avoid doing anything expensive in the main window's constructor: it runs before the window can even be shown.

The solution is to delay everything except building the user interface until the event loop has started. The main window's constructor could look like this:

```cpp
MainWindow::MainWindow()
{
    initGUI();
    QTimer::singleShot(0, this, &MainWindow::initObject);
}

void MainWindow::initGUI()
{
    /* Construct your widgets here.  Note that the widgets you
     * construct here shouldn't require complex initialization
     * either, or you've defeated the purpose.
     * All you want to do is create your GUI objects and
     * QObject::connect
     * the appropriate signals to their slots. */
}

void MainWindow::initObject() {
    /* This slot will be called as soon as the event loop starts.
     * Put everything else that needs to be done, including
     * restoring values, reading files, session restoring, etc here.
     * It will still take time, but at least your window will be
     * on the screen, making your app look active. */
}
```

This may not save any time overall, but the application **seems** faster to the user starting it: they see quickly that it has started.

Only when startup can't be made fast enough, consider a [QSplashScreen](https://doc.qt.io/qt-6/qsplashscreen.html).

## Data structures

Some of the most common problems with the data structures of Qt applications.

### Passing non-trivial types

Pass types other than the basic ones (such as `char` and `int`) by const reference where you can.

[QString](https://doc.qt.io/qt-6/qstring.html), for example, should always be passed as `const QString &`. Even though QString is implicitly shared, a const reference is more efficient (and safer) than passing it by value.

So the usual signature of a function taking QString arguments is:

```cpp
void myMethod(const QString &foo, const QString &bar);
```

### QObject

To delete a QObject subclass from one of its own member functions, never do this:

```cpp
delete this;
```

Sooner or later it crashes, because the event loop may still call a function of the object, through signals and slots, after it is deleted.

Always use [QObject::deleteLater()](https://doc.qt.io/qt-6/qobject.html#deleteLater) instead, which does the same safely.

### Empty QStrings

To check whether a [QString](https://doc.qt.io/qt-6/qstring.html) is empty:

```cpp
// Correct
if (mystring.isEmpty()) { }

// Correct
if (mystring == QString()) { }

// Wrong! ""
if (mystring == "") { }
```

Qt distinguishes null and empty strings for historical reasons; for most code what matters is whether the string contains any data, which `isEmpty()` tells you. Don't build new code on the difference.

### QString and reading files

When reading a file, it is faster to convert its content to Unicode (a [QString](https://doc.qt.io/qt-6/qstring.html)) in one go than line by line. So [QIODevice::readAll()](https://doc.qt.io/qt-6/qiodevice.html#readAll) followed by a single conversion to QString is often a good solution.

For larger files, read a block of lines at a time and convert it, so you can update your user interface in between: return to the event loop and read the next block from a timer, or use a local event loop.

`qApp->processEvents()` also works, but is discouraged: it easily leads to subtle but often fatal problems.

### QString and QByteArray

QString is the tool of choice for most string handling, but one case is particularly inefficient: if you work on data in [QByteArray](https://doc.qt.io/qt-6/qbytearray.html)s, don't pass it through functions that take QString parameters only to turn it into QByteArrays again.

For example:

```cpp
QByteArray myData;
QString myNewData = mangleData(myData);

QString mangleData(const QString &data)
{
    QByteArray str = data.toLatin1();
    // mangle return QString(str);
}
```

The expensive part is the conversion to QString, which converts to Unicode. It is wasted, because the function immediately converts back with `toLatin1()`. If you know the Unicode conversion isn't needed, don't go through QString.

Write the example like this instead:

```cpp
QByteArray myData;
QByteArray myNewData = mangleData(myData);

QByteArray mangleData( const QByteArray& data )
```

## QDomElement

When parsing an XML document you often need to go through all the elements. You might write:

```cpp
for (QDomElement e = baseElement.firstChild().toElement(); !e.isNull(); e = e.nextSibling().toElement() ) {
    ...
}
```

That's wrong: the loop stops early at the first [QDomNode](https://doc.qt.io/qt-6/qdomnode.html) that isn't an element, such as a comment.

Either go through all nodes and skip the others:

```cpp
for (QDomNode n = baseElement.firstChild(); !n.isNull(); n = n.nextSibling()) {
    QDomElement e = n.toElement();
    if (e.isNull()) {
        continue;
    }
    ...
}
```

or use the element functions, which skip other nodes for you:

```cpp
for (QDomElement e = baseElement.firstChildElement(); !e.isNull(); e = e.nextSiblingElement()) {
    ...
}
```
