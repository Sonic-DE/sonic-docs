---
title: "KNSCore::Question Class"
description: "A way to ask a user a question from inside a GUI-less library (like KNewStuffCore)."
---

# KNSCore::Question Class

A way to ask a user a question from inside a GUI-less library (like [KNewStuffCore](knewstuffcore-module.md)). [More...](#details)

- **Header:** `#include <Question>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knscore-question-members.md)

## Public Types

- [enum Question::QuestionType](#QuestionType-enum)
- [enum Question::Response](#Response-enum)

## Public Functions

- [KNSCore::Question::Response ask()](#ask)
- [KNSCore::Entry entry() const](#entry)
- [QStringList list() const](#list)
- [QString question() const](#question)
- [KNSCore::Question::QuestionType questionType() const](#questionType)
- [QString response() const](#response)
- [void setEntry(const KNSCore::Entry &entry)](#setEntry)
- [void setList(const QStringList &newList)](#setList)
- [void setQuestion(const QString &newQuestion)](#setQuestion)
- [void setQuestionType(KNSCore::Question::QuestionType newType = YesNoQuestion)](#setQuestionType)
- [void setResponse(KNSCore::Question::Response response)](#setResponse)
- [void setResponse(const QString &response)](#setResponse-1)
- [void setTitle(const QString &newTitle)](#setTitle)
- [QString title() const](#title)

## Detailed Description {#details}

Rather than using a message box (which is a UI thing), when you want to ask your user a question, create an instance of this class and use that instead. The consuming library (in most cases KNewStuff or KNewStuffQuick) will listen to any question being asked, and act appropriately (that is, KNewStuff will show a dialog with an appropriate dialog box, and KNewStuffQuick will either request a question be asked if the developer is using the plugin directly, or ask the question using an appropriate method for Qt Quick based applications)

The following is an example of a question asking the user to select an item from a list.

```cpp
QStringList choices() << "foo" << "bar";
Question question(Question::SelectFromListQuestion);
question.setTitle("Pick your option");
question.setQuestion("Please select which option you would like");
question.setList(choices);
question.setEntry(entry);
if (question.ask() == Question::OKResponse) {
    QString theChoice = question.response();
}
```

## Member Type Documentation {#member-type-documentation}

### enum Question::QuestionType {#QuestionType-enum}

Defines the type of question to be presented to the user.

| Constant | Value | Description |
| --- | --- | --- |
| `KNSCore::Question::YesNoQuestion` | `0` | The question can be answered with either yes or no. |
| `KNSCore::Question::ContinueCancelQuestion` | `1` | The question can be answered with either continue or cancel. |
| `KNSCore::Question::InputTextQuestion` | `2` | Answering the question requires text input from the user. |
| `KNSCore::Question::SelectFromListQuestion` | `3` | Answering the question requires selecting from a list of choices. |
| `KNSCore::Question::PasswordQuestion` | `4` | Answering the question requires the user to input a password. |

*See also* [Response](knscore-question.md#Response-enum)

### enum Question::Response {#Response-enum}

Defines how the user responded to the question.

| Constant | Value | Description |
| --- | --- | --- |
| `KNSCore::Question::InvalidResponse` | `0` | The user did not provide a valid response. |
| `KNSCore::Question::YesResponse` | `1` | The user selected yes. |
| `KNSCore::Question::NoResponse` | `2` | The user selected no. |
| `KNSCore::Question::ContinueResponse` | `3` | The user selected continue. |
| `KNSCore::Question::CancelResponse` | `4` | The user selected cancel. |
| `KNSCore::Question::OKResponse` | `YesResponse` | The user selected OK. |

*See also* [QuestionType](knscore-question.md#QuestionType-enum)

## Member Function Documentation {#member-function-documentation}

### KNSCore::Question::Response Question::ask() {#ask}

Returns the user's reponse to the question.

*See also* [setResponse](knscore-question.md#setResponse)

### KNSCore::Entry Question::entry() const {#entry}

Returns the configured entry.

*See also* [setEntry](knscore-question.md#setEntry)()

### QStringList Question::list() const {#list}

Returns the list of choices to present to the user, if any.

*See also* [setList](knscore-question.md#setList)()

### QString Question::question() const {#question}

Returns the question message to be presented to the user.

*See also* [setQuestion](knscore-question.md#setQuestion)()

### KNSCore::Question::QuestionType Question::questionType() const {#questionType}

Returns the configured question type.

*See also* [setQuestionType](knscore-question.md#setQuestionType)()

### QString Question::response() const {#response}

Returns the response data provided by the user, if any.

*See also* [setResponse](knscore-question.md#setResponse)()

### void Question::setEntry(const KNSCore::Entry &*entry*) {#setEntry}

Sets the data `entry` container this question refers to.

*See also* [entry](knscore-question.md#entry)()

### void Question::setList(const QStringList &*newList*) {#setList}

Sets the list of optional choices to present to the user to `newList` for a [SelectFromListQuestion](knscore-question.md#QuestionType-enum).

*See also* [list](knscore-question.md#list)()

### void Question::setQuestion(const QString &*newQuestion*) {#setQuestion}

Sets the question to be presented to the user.

`newQuestion` is the question message

*See also* [question](knscore-question.md#question)()

### void Question::setQuestionType(KNSCore::Question::QuestionType *newType* = YesNoQuestion) {#setQuestionType}

Sets the type of question presented to the user.

`newType` is the question type

*See also* [questionType](knscore-question.md#questionType)()

### void Question::setResponse(KNSCore::Question::Response *response*) {#setResponse}

When the user makes a choice on a question, that is a response. This is the return value in [ask](knscore-question.md#ask)().

`response` This will set the response, and mark the question as answered

*See also* [response](knscore-question.md#response)()

### void Question::setResponse(const QString &*response*) {#setResponse-1}

If the user has any way of inputting data to go along with the response above, consider this a part of the response. As such, you can set, and later get, that response as well. This does NOT mark the question as answered.

`response` This sets the string response for the question

*See also* [setResponse](knscore-question.md#setResponse)

### void Question::setTitle(const QString &*newTitle*) {#setTitle}

Sets the title of the UX element presented to the user.

`newTitle` is the title text

*See also* [title](knscore-question.md#title)()

### QString Question::title() const {#title}

Returns the title of the UX element.

*See also* [setTitle](knscore-question.md#setTitle)()
