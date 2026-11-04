---
title: Using custom types with D-Bus
description: Pass your own types as arguments of D-Bus methods and signals with Qt D-Bus.
source_url: https://develop.kde.org/docs/features/d-bus/using_custom_types_with_dbus/
source_authors: [Alexey Andreev, Carl Schwan, Chris Holland, Engin Karakurt, Mikhail Zolotukhin, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: Qt 6.11.3 (qdbuscpp2xml, qdbusxml2cpp, Qt D-Bus); the example below was built with Qt 6.11.3 and its Message and enum marshaling run between two processes on a session bus
---

# Using custom types with D-Bus

## Write a class

Write the class you want to publish, with its signals, slots and properties, using your own types where you need them.

The example publishes this class (the full example is at the end of the page):

```cpp
class Chat : public QObject
{
    Q_OBJECT

    Q_CLASSINFO("D-Bus Interface", "demo.Chat")
    Q_PROPERTY( QStringList users READ users)

signals:
    void userAdded(const QString& user);
    void userRemoved(const QString& user);

    void messageSent(const Message &message);

public slots:
    void addUser(const QString &user);
    void removeUser(const QString &user);

    void sendMessage(const Message &message);

public:
    Chat(QObject* parent = nullptr);
    virtual ~Chat();

    QStringList users() const;

private:
    QStringList m_users;
};
```

It manages a list of users and sends messages. `Message` is the custom type: it holds a user and a text. The methods could just as well take two `QString` parameters, but then Qt would handle everything by itself, and this page needs something it can't.

The user list is a `QStringList`, to show that Qt handles many types without help, as the next steps make clear.

The header that declares the class must include the header of `Message`, not just forward-declare it: Qt 6's moc needs the complete type of every signal and slot argument.

### Q_CLASSINFO

`Q_CLASSINFO` sets the interface name that the XML tools use.

Interface names usually include the organization's name, for example:

```cpp
Q_CLASSINFO("D-Bus Interface", "com.firm.department.product.interface")
```

## Generate the XML

Generate the XML description of the class with Qt's `qdbuscpp2xml` tool (in Qt's tool directory, `qtpaths6 --query QT_HOST_BINS`).

For the example's `Chat.hpp` it prints:

```xml
<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN" "http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
<node>
  <interface name="demo.Chat">
    <property name="users" type="as" access="read"/>
    <signal name="userAdded">
      <arg name="user" type="s" direction="out"/>
    </signal>
    <signal name="userRemoved">
      <arg name="user" type="s" direction="out"/>
    </signal>
    <method name="addUser">
      <arg name="user" type="s" direction="in"/>
    </method>
    <method name="removeUser">
      <arg name="user" type="s" direction="in"/>
    </method>
  </interface>
</node>
```

and warns `Unregistered input type in parameter list: Message` for the two members it left out. The XML has every member that uses standard Qt types: with an adaptor and interface generated from it you could add and remove users, read the user list and receive `userAdded` and `userRemoved`. Even the `QStringList` is handled automatically.

The members that use `Message` are missing. For an adaptor and interface that handle `Message`, edit the XML.

> **Tip:** You may want to generate the adaptor and interface from this unedited XML too, and compare them with the ones generated below.

## Edit the XML

`qdbusxml2cpp` needs to be told about the custom types, with annotations in the XML:

```xml
<annotation name="org.qtproject.QtDBus.QtTypeName" value="customType"/>
```

The name differs slightly between properties and method or signal arguments: arguments add the direction and position, such as `.In0` for a method's first argument and `.Out0` for a signal's first argument or a method's first return value. Here is an example with `QRect` (unrelated to the chat example):

```xml
<property name="rectangle" type="(iiii)" access="readwrite">
  <annotation name="org.qtproject.QtDBus.QtTypeName" value="QRect"/>
</property>

<signal name="rectangleChanged">
  <arg name="rect" type="(iiii)" direction="out"/>
  <annotation name="org.qtproject.QtDBus.QtTypeName.Out0" value="QRect"/>
</signal>

<method name="changeRectangle">
  <arg name="message" type="(iiii)" direction="in"/>
  <annotation name="org.qtproject.QtDBus.QtTypeName.In0" value="QRect"/>
</method>
```

Qt D-Bus supports `QRect` itself, so `qdbuscpp2xml` writes exactly these annotations for a class that uses `QRect`.

Write the D-Bus type (the `type` attribute) that your streaming operators really produce. Between Qt programs the adaptor and interface still work if it's wrong, because the data sent comes from the operators, not from the XML: the example works the same with `a(ii)` written for `Message`. But other clients read the type through introspection, so a wrong type misleads them. `Message` streams as a structure of two strings, `(ss)`.

`qdbusxml2cpp` also accepts the old annotation name `com.trolltech.QtDBus.QtTypeName`, but use `org.qtproject.QtDBus.QtTypeName`.

The complete interface of the example is:

```xml
<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN" "http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
<node>
  <interface name="demo.Chat">
    <property name="users" type="as" access="read"/>
    <signal name="userAdded">
      <arg name="user" type="s" direction="out"/>
    </signal>
    <signal name="userRemoved">
      <arg name="user" type="s" direction="out"/>
    </signal>
    <signal name="messageSent">
      <arg name="message" type="(ss)" direction="out"/>
      <annotation name="org.qtproject.QtDBus.QtTypeName.Out0" value="Message"/>
    </signal>
    <method name="addUser">
      <arg name="user" type="s" direction="in"/>
    </method>
    <method name="removeUser">
      <arg name="user" type="s" direction="in"/>
    </method>
    <method name="sendMessage">
      <arg name="message" type="(ss)" direction="in"/>
      <annotation name="org.qtproject.QtDBus.QtTypeName.In0" value="Message"/>
    </method>
  </interface>
</node>
```

## Generate the adaptor and interface classes

With the XML complete, generate the adaptor and the interface. Because a custom type is involved, they need to include its header.

Let CMake generate them at build time:

```cmake
set(CMAKE_INCLUDE_CURRENT_DIR ON)

set_source_files_properties(Chat.xml PROPERTIES INCLUDE Message.hpp)
qt_add_dbus_adaptor(dbuschat_SRCS Chat.xml Chat.hpp Chat ChatAdaptor ChatAdaptor)
qt_add_dbus_interface(dbuschat_SRCS Chat.xml ChatInterface)
```

The `INCLUDE` property adds `#include "Message.hpp"` to the generated interface ([qt_add_dbus_interface()](https://doc.qt.io/qt-6/qtdbus-cmake-qt-add-dbus-interface.html)). The adaptor includes `Chat.hpp` ([qt_add_dbus_adaptor()](https://doc.qt.io/qt-6/qtdbus-cmake-qt-add-dbus-adaptor.html)), which includes `Message.hpp`. `CMAKE_INCLUDE_CURRENT_DIR` lets the generated files, which are in the build directory, find the headers in the source directory.

You can also run the tool yourself; `-i` adds the include:

```bash
qdbusxml2cpp Chat.xml -i Message.hpp -a ChatAdaptor
qdbusxml2cpp Chat.xml -i Message.hpp -p ChatInterface
```

## Qt meta-object setup

The adaptor and interface still need the custom type to be known to Qt's meta-object system and to Qt D-Bus.

### Register the type

Declare the type as a Qt meta-type with

```cpp
Q_DECLARE_METATYPE(Message)
```

in the header that defines it.

Then register it with `qRegisterMetaType()` and `qDBusRegisterMetaType()`. The example's `Message` class has a static function for this:

```cpp
void Message::registerMetaType()
{
    qRegisterMetaType<Message>("Message");
    qDBusRegisterMetaType<Message>();
}
```

> **Important:** Register the type in the application that publishes the object and in the application that uses it: both have to handle it. Register it before calling any adaptor or interface method that needs it. Qt prints errors when it meets types it can't handle (yet), but don't rely on noticing them.

### Provide QDBusArgument streaming operators

When a D-Bus call uses a custom type, Qt has to marshal (serialize) and unmarshal (deserialize) it. It does that with the [QDBusArgument](https://doc.qt.io/qt-6/qdbusargument.html) streaming operators, which you implement for your type.

For `Message`, which only holds two strings, they are simple:

```cpp
QDBusArgument &operator<<(QDBusArgument &argument, const Message& message)
{
    argument.beginStructure();
    argument << message.m_user;
    argument << message.m_text;
    argument.endStructure();

    return argument;
}

const QDBusArgument &operator>>(const QDBusArgument &argument, Message &message)
{
    argument.beginStructure();
    argument >> message.m_user;
    argument >> message.m_text;
    argument.endStructure();

    return argument;
}
```

QDBusArgument handles much more complex types as well; its documentation has examples for structures, arrays and maps.

## Use the adaptor and interface classes

Now the adaptor and interface handle the custom type for you.

### Publishing an object with an adaptor

To publish an object, create an adaptor for it and register the object on the bus.

The example publishes its Chat object like this:

```cpp
Chat* pChat = new Chat(&a);
ChatAdaptor* pChatAdaptor = new ChatAdaptor(pChat);

if (!connection.registerService(CHAT_SERVICE))
{
    qFatal("Could not register service!");
}

if (!connection.registerObject(CHAT_PATH, pChat))
{
    qFatal("Could not register Chat object!");
}
```

The ChatAdaptor handles the D-Bus requests for the Chat object: when a method is called, it calls the matching slot of the Chat object, and when the Chat object emits a signal, the adaptor sends it on D-Bus.

### Talking to a remote object with an interface

To talk to a remote object, create the matching interface with the service name and object path.

The example connects to a remote Chat object like this:

```cpp
demo::Chat chatInterface(CHAT_SERVICE, CHAT_PATH, connection);
```

### Using the remote object

With the interface you use the remote object like any other QObject.

The example's ChatWindow adds a user by calling

```cpp
m_chatInterface.addUser(m_userName);
```

and reacts to the Chat object's signals by connecting to the interface like to any QObject:

```cpp
connect(&m_chatInterface, SIGNAL(userAdded(QString)), SLOT(chat_userAdded(QString)));
connect(&m_chatInterface, SIGNAL(userRemoved(QString)), SLOT(chat_userRemoved(QString)));
connect(&m_chatInterface, SIGNAL(messageSent(Message)), SLOT(chat_messageSent(Message)));
```

The generated interface declares these signals in C++, so function-pointer connections work as well, for example `connect(&m_chatInterface, &demo::Chat::messageSent, this, &ChatWindow::chat_messageSent)`.

## More

### Automation

Some of this is manual work, but using an adaptor and interface is still much more convenient than building D-Bus calls and reading their replies by hand.

`qdbuscpp2xml` and `qdbusxml2cpp` could be extended to handle custom types by analysing the whole source tree instead of single headers, so they could recognize the custom types and write their members into the XML themselves. One idea for extending `qdbuscpp2xml` with plugins is described in [Cpp2XmlPlugins](https://techbase.kde.org/Development/Tutorials/D-Bus/Cpp2XmlPlugins) on KDE TechBase; the `qdbuscpp2xml` of Qt 6.11 has no plugin support.

Qt Creator could also automate the approach shown here, since it already knows the custom types of a project; that may be easier than changing the D-Bus tools.

### Adventurous serialization of enumerations

If you send many enumerations over D-Bus, you end up writing QDBusArgument streaming operators for each. A basic implementation casts the enum to and from `int`:

```cpp
QDBusArgument &operator<<(QDBusArgument &argument, const EnumerationType& source)
{
    argument.beginStructure();
    argument << static_cast<int>(source);
    argument.endStructure();
    return argument;
}

const QDBusArgument &operator>>(const QDBusArgument &argument, EnumerationType &dest)
{
    int a;
    argument.beginStructure();
    argument >> a;
    argument.endStructure();
    dest = static_cast<EnumerationType>(a);
    return argument;
}
```

This code is the same for every enumeration except for `EnumerationType`.

A template can do it once. But it must apply only to enumerations, not to the other custom types you send: otherwise every custom type would be cast to and from an integer, which is wrong for anything more complex.

The C++ standard library helps here: `std::is_enum` lets a template choose its implementation by a condition, so the marshaling code is used only for enumerations:

```cpp
template<typename T, typename TEnum>
class QDBusEnumMarshal;

template<typename T>
class QDBusEnumMarshal<T, std::true_type>
{
public:
    static QDBusArgument &marshal(QDBusArgument &argument, const T &source)
    {
        argument.beginStructure();
        argument << static_cast<int>(source);
        argument.endStructure();
        return argument;
    }

    static const QDBusArgument &unmarshal(const QDBusArgument &argument, T &source)
    {
        int a;
        argument.beginStructure();
        argument >> a;
        argument.endStructure();

        source = static_cast<T>(a);

        return argument;
    }
};
```

The implementation for a type `T` is then called with:

```cpp
QDBusEnumMarshal<T, typename std::is_enum<T>::type>::marshal(argument, source);
```

A little glue connects it to the QDBusArgument streaming operators:

```cpp
template<typename T>
QDBusArgument &operator<<(QDBusArgument &argument, const T &source)
{
    return QDBusEnumMarshal<T, typename std::is_enum<T>::type>::marshal(argument, source);
}

template<typename T>
const QDBusArgument &operator>>(const QDBusArgument &argument, T &source)
{
    return QDBusEnumMarshal<T, typename std::is_enum<T>::type>::unmarshal(argument, source);
}
```

Put all of it in a header and include that where you declare the enumerations you send over D-Bus; the compiler then finds the operators by itself. Each enumeration still has to be declared as a meta-type and registered (`Q_DECLARE_METATYPE` and `qDBusRegisterMetaType`). An enumeration sent this way appears on the bus as a structure holding an integer, `(i)`.

#### enumDBus.hpp

This is the whole header needed to marshal and unmarshal any enumeration:

```cpp
#ifndef ENUMDBUS_HPP
#define ENUMDBUS_HPP

#include <QDBusArgument>

#include <type_traits>

template<typename T, typename TEnum>
class QDBusEnumMarshal;

template<typename T>
class QDBusEnumMarshal<T, std::true_type>
{
public:
    static QDBusArgument &marshal(QDBusArgument &argument, const T &source)
    {
        argument.beginStructure();
        argument << static_cast<int>(source);
        argument.endStructure();
        return argument;
    }

    static const QDBusArgument &unmarshal(const QDBusArgument &argument, T &source)
    {
        int a;
        argument.beginStructure();
        argument >> a;
        argument.endStructure();

        source = static_cast<T>(a);

        return argument;
    }
};

template<typename T>
QDBusArgument &operator<<(QDBusArgument &argument, const T &source)
{
    return QDBusEnumMarshal<T, typename std::is_enum<T>::type>::marshal(argument, source);
}

template<typename T>
const QDBusArgument &operator>>(const QDBusArgument &argument, T &source)
{
    return QDBusEnumMarshal<T, typename std::is_enum<T>::type>::unmarshal(argument, source);
}

#endif // ENUMDBUS_HPP
```

## Example

These are the sources of the chat example. `Chat` is the published interface; CMake generates `ChatAdaptor` and `ChatInterface` from `Chat.xml`.

Put the files in one directory and run:

```bash
cmake -S . -B build -G Ninja
cmake --build build
./build/dbuschat
```

Start it twice to chat between the two windows.

### CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.16)
project(dbuschat)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
# The generated adaptor and interface are in the build directory and include headers from the sources.
set(CMAKE_INCLUDE_CURRENT_DIR ON)

find_package(Qt6 6.11 REQUIRED COMPONENTS Widgets DBus)

# The generated classes need the Message type.
set_source_files_properties(Chat.xml PROPERTIES INCLUDE Message.hpp)
qt_add_dbus_adaptor(dbuschat_SRCS Chat.xml Chat.hpp Chat ChatAdaptor ChatAdaptor)
qt_add_dbus_interface(dbuschat_SRCS Chat.xml ChatInterface)

add_executable(dbuschat
    main.cpp
    Chat.cpp Chat.hpp
    ChatWindow.cpp ChatWindow.hpp ChatWindow.ui
    Message.cpp Message.hpp
    ${dbuschat_SRCS}
)
target_link_libraries(dbuschat Qt6::Widgets Qt6::DBus)
```

### Chat.hpp

```cpp
#ifndef CHAT_HPP
#define CHAT_HPP

#include <QObject>
#include <QStringList>

#include "Message.hpp"

class Chat : public QObject
{
    Q_OBJECT

    Q_CLASSINFO("D-Bus Interface", "demo.Chat")
    Q_PROPERTY( QStringList users READ users)

signals:
    void userAdded(const QString& user);
    void userRemoved(const QString& user);

    void messageSent(const Message &message);

public slots:
    void addUser(const QString &user);
    void removeUser(const QString &user);

    void sendMessage(const Message &message);

public:
    Chat(QObject* parent = nullptr);
    virtual ~Chat();

    QStringList users() const;

private:
    QStringList m_users;
};
#endif // CHAT_HPP
```

### Chat.cpp

```cpp
#include "Chat.hpp"

Chat::Chat(QObject* parent) :
        QObject(parent)
{
}

Chat::~Chat()
{
}

void Chat::addUser(const QString &user)
{
    if (!m_users.contains(user))
    {
        m_users.append(user);

        emit userAdded(user);
    }
}

void Chat::removeUser(const QString &user)
{
    if (m_users.contains(user))
    {
        m_users.removeOne(user);

        emit userRemoved(user);
    }
}

void Chat::sendMessage(const Message &message)
{
    Q_EMIT messageSent(message);
}

QStringList Chat::users() const
{
    return m_users;
}
```

### Chat.xml

```xml
<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN" "http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
<node>
  <interface name="demo.Chat">
    <property name="users" type="as" access="read"/>
    <signal name="userAdded">
      <arg name="user" type="s" direction="out"/>
    </signal>
    <signal name="userRemoved">
      <arg name="user" type="s" direction="out"/>
    </signal>
    <signal name="messageSent">
      <arg name="message" type="(ss)" direction="out"/>
      <annotation name="org.qtproject.QtDBus.QtTypeName.Out0" value="Message"/>
    </signal>
    <method name="addUser">
      <arg name="user" type="s" direction="in"/>
    </method>
    <method name="removeUser">
      <arg name="user" type="s" direction="in"/>
    </method>
    <method name="sendMessage">
      <arg name="message" type="(ss)" direction="in"/>
      <annotation name="org.qtproject.QtDBus.QtTypeName.In0" value="Message"/>
    </method>
  </interface>
</node>
```

### Message.hpp

```cpp
#ifndef MESSAGE_HPP
#define MESSAGE_HPP

#include <QtDBus>

class Message
{
public:
    Message();
    Message(const QString& user, const QString &message);
    Message(const Message &other);
    Message& operator=(const Message &other);
    ~Message();

    friend QDBusArgument &operator<<(QDBusArgument &argument, const Message &message);
    friend const QDBusArgument &operator>>(const QDBusArgument &argument, Message &message);

    QString getUser() const;
    QString getText() const;

    //register Message with the Qt type system
    static void registerMetaType();

private:
    QString m_user;
    QString m_text;
};

Q_DECLARE_METATYPE(Message)

#endif // MESSAGE_HPP
```

### Message.cpp

```cpp
#include "Message.hpp"

Message::Message() :
        m_user(),
        m_text()
{
}

Message::Message(const QString &user, const QString &text) :
        m_user(user),
        m_text(text)
{
}

Message::Message(const Message &other) :
        m_user(other.m_user),
        m_text(other.m_text)
{
}

Message& Message::operator=(const Message &other)
{
    m_user = other.m_user;
    m_text = other.m_text;

    return *this;
}

Message::~Message()
{
}

QString Message::getUser() const
{
    return m_user;
}

QString Message::getText() const
{
    return m_text;
}

void Message::registerMetaType()
{
    qRegisterMetaType<Message>("Message");

    qDBusRegisterMetaType<Message>();
}

QDBusArgument &operator<<(QDBusArgument &argument, const Message& message)
{
    argument.beginStructure();
    argument << message.m_user;
    argument << message.m_text;
    argument.endStructure();

    return argument;
}

const QDBusArgument &operator>>(const QDBusArgument &argument, Message &message)
{
    argument.beginStructure();
    argument >> message.m_user;
    argument >> message.m_text;
    argument.endStructure();

    return argument;
}
```

### main.cpp

```cpp
#include <QtDBus/QDBusConnection>
#include <QtDBus/QDBusConnectionInterface>
#include <QApplication>

#include "Chat.hpp"
#include "ChatAdaptor.h"
#include "ChatInterface.h"
#include "ChatWindow.hpp"
#include "Message.hpp"

#define CHAT_SERVICE "demo.dbus.chat"
#define CHAT_PATH "/chat"

int main(int argc, char *argv[])
{
    /*
      Register the Message type first thing, so Qt knows how to handle
      it before an Adaptor/Interface is even constructed.

      It should be ok to register it further down, as long as no
      Message marshaling or unmarshaling takes place, but this is
      definitely the safest way of doing things.
    */
    Message::registerMetaType();

    QApplication a(argc, argv);
    Chat* pChat = NULL;
    ChatAdaptor* pChatAdaptor = NULL;

    /*
      Create a Chat instance and register it with the session bus only if
      the service isn't already available.
    */
    QDBusConnection connection = QDBusConnection::sessionBus();
    if (!connection.interface()->isServiceRegistered(CHAT_SERVICE))
    {
        pChat = new Chat(&a);
        pChatAdaptor = new ChatAdaptor(pChat);

        if (!connection.registerService(CHAT_SERVICE))
        {
            qFatal("Could not register service!");
        }

        if (!connection.registerObject(CHAT_PATH, pChat))
        {
            qFatal("Could not register Chat object!");
        }
    }

    demo::Chat chatInterface(CHAT_SERVICE, CHAT_PATH, connection);

    ChatWindow w(chatInterface);
    w.show();

    int ret = a.exec();

    //cleanup
    if (pChat)
    {
        delete pChat;
    }
    if (pChatAdaptor)
    {
        delete pChatAdaptor;
    }

    return ret;
}
```

### ChatWindow.hpp

```cpp
#ifndef CHATWINDOW_HPP
#define CHATWINDOW_HPP

#include <QMainWindow>
#include <QStringListModel>

#include "ChatInterface.h"

namespace Ui
{
    class ChatWindow;
}

class QCloseEvent;

class ChatWindow : public QMainWindow
{
    Q_OBJECT

public:
    ChatWindow(demo::Chat& chatInterface, QWidget *parent = nullptr);
    virtual ~ChatWindow();

protected:
    virtual void closeEvent(QCloseEvent *event);

private:
    ChatWindow(const ChatWindow &other);
    ChatWindow& operator=(const ChatWindow &other);

    Ui::ChatWindow *ui;

    QString m_userName;

    QStringListModel m_users;

    demo::Chat &m_chatInterface;

private slots:
    void sendMessage();

    void chat_userAdded(const QString &user);
    void chat_userRemoved(const QString &user);
    void chat_messageSent(const Message &message);
};

#endif // CHATWINDOW_HPP
```

### ChatWindow.cpp

```cpp
#include "ChatWindow.hpp"
#include "ui_ChatWindow.h"

#include <QtGui/QCloseEvent>
#include <QInputDialog>
#include <QMessageBox>

#include "Message.hpp"

ChatWindow::ChatWindow(demo::Chat& chatInterface, QWidget *parent) :
    QMainWindow(parent),
    ui(new Ui::ChatWindow),
    m_userName(),
    m_users(),
    m_chatInterface(chatInterface)
{
    ui->setupUi(this);

    QStringList userList = chatInterface.users();
    m_users.setStringList(userList);
    m_users.sort(0);

    connect(&m_chatInterface, SIGNAL(userAdded(QString)), SLOT(chat_userAdded(QString)));
    connect(&m_chatInterface, SIGNAL(userRemoved(QString)), SLOT(chat_userRemoved(QString)));
    connect(&m_chatInterface, SIGNAL(messageSent(Message)), SLOT(chat_messageSent(Message)));

    connect(ui->lneMessage, SIGNAL(returnPressed()), SLOT(sendMessage()));
    connect(ui->btnSend, SIGNAL(released()), SLOT(sendMessage()));

    bool ok;
    m_userName = QInputDialog::getText(this, "Username?", "User name:", QLineEdit::Normal, QDir::home().dirName(), &ok, Qt::Dialog);

    if (!ok)
    {
        QApplication::exit();
        qFatal("Cancelled");
    }

    if (userList.contains(m_userName))
    {
        QMessageBox::critical(this, "Invalid Username", "Username " + m_userName + " is already taken");
        QApplication::exit();
        qFatal("Duplicate username");
    }

    m_chatInterface.addUser(m_userName);

    setWindowTitle("Chat -- " + m_userName);

    ui->lstUsers->setModel(&m_users);
}

ChatWindow::~ChatWindow()
{
    delete ui;
}

void ChatWindow::closeEvent(QCloseEvent *event)
{
    QMainWindow::closeEvent(event);

    if (event->isAccepted())
    {
        m_chatInterface.removeUser(m_userName);
    }
}

void ChatWindow::sendMessage()
{
    Message message(m_userName, ui->lneMessage->text());
    m_chatInterface.sendMessage(message);

    ui->lneMessage->clear();
}

void ChatWindow::chat_userAdded(const QString &user)
{
    QStringList users = m_users.stringList();
    users.append(user);
    users.sort();
    m_users.setStringList(users);
}

void ChatWindow::chat_userRemoved(const QString &user)
{
    QStringList users = m_users.stringList();
    users.removeOne(user);
    m_users.setStringList(users);
}

void ChatWindow::chat_messageSent(const Message &message)
{
    ui->txtChat->appendPlainText(message.getUser() + " : " + message.getText());
}
```

### ChatWindow.ui

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ui version="4.0">
 <class>ChatWindow</class>
 <widget class="QMainWindow" name="ChatWindow">
  <property name="geometry">
   <rect>
    <x>0</x>
    <y>0</y>
    <width>600</width>
    <height>400</height>
   </rect>
  </property>
  <property name="windowTitle">
   <string>ChatWindow</string>
  </property>
  <widget class="QWidget" name="centralWidget">
   <layout class="QVBoxLayout" name="verticalLayout">
    <item>
     <widget class="QWidget" name="widget_2" native="true">
      <layout class="QHBoxLayout" name="horizontalLayout_2">
       <item>
        <widget class="QListView" name="lstUsers">
         <property name="maximumSize">
          <size>
           <width>150</width>
           <height>16777215</height>
          </size>
         </property>
         <property name="focusPolicy">
          <enum>Qt::NoFocus</enum>
         </property>
         <property name="editTriggers">
          <set>QAbstractItemView::NoEditTriggers</set>
         </property>
         <property name="selectionMode">
          <enum>QAbstractItemView::NoSelection</enum>
         </property>
        </widget>
       </item>
       <item>
        <widget class="QPlainTextEdit" name="txtChat">
         <property name="focusPolicy">
          <enum>Qt::NoFocus</enum>
         </property>
        </widget>
       </item>
      </layout>
     </widget>
    </item>
    <item>
     <widget class="QWidget" name="widget" native="true">
      <layout class="QHBoxLayout" name="horizontalLayout">
       <item>
        <widget class="QLineEdit" name="lneMessage"/>
       </item>
       <item>
        <widget class="QPushButton" name="btnSend">
         <property name="text">
          <string>Send</string>
         </property>
        </widget>
       </item>
      </layout>
     </widget>
    </item>
   </layout>
  </widget>
  <widget class="QMenuBar" name="menuBar">
   <property name="geometry">
    <rect>
     <x>0</x>
     <y>0</y>
     <width>600</width>
     <height>25</height>
    </rect>
   </property>
  </widget>
  <widget class="QToolBar" name="mainToolBar">
   <attribute name="toolBarArea">
    <enum>TopToolBarArea</enum>
   </attribute>
   <attribute name="toolBarBreak">
    <bool>false</bool>
   </attribute>
  </widget>
  <widget class="QStatusBar" name="statusBar"/>
 </widget>
 <layoutdefault spacing="6" margin="11"/>
 <resources/>
 <connections/>
</ui>
```

