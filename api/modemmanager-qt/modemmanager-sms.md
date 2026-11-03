---
title: "ModemManager::Sms Class"
description: "Provides an interface to manipulate and control an SMS."
---

# ModemManager::Sms Class

Provides an interface to manipulate and control an SMS. [More...](#details)

- **Header:** `#include <ModemManagerQt/Sms>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](modemmanager-sms-members.md)

## Public Types

- [Sms::List](#List-typedef)
- [Sms::Ptr](#Ptr-typedef)

## Public Functions

- [Sms(const QString &path, QObject \*parent = nullptr)](#Sms)
- [QString SMSC() const](#SMSC)
- [QByteArray data() const](#data)
- [bool deliveryReportRequest() const](#deliveryReportRequest)
- [MMSmsDeliveryState deliveryState() const](#deliveryState)
- [QDateTime dischargeTimestamp() const](#dischargeTimestamp)
- [uint messageReference() const](#messageReference)
- [QString number() const](#number)
- [MMSmsPduType pduType() const](#pduType)
- [QDBusPendingReply\<\> send()](#send)
- [MMSmsCdmaServiceCategory serviceCategory() const](#serviceCategory)
- [void setTimeout(int timeout)](#setTimeout)
- [int smsClass() const](#smsClass)
- [MMSmsState state() const](#state)
- [MMSmsStorage storage() const](#storage)
- [QDBusPendingReply\<\> store(MMSmsStorage storage = MM\_SMS\_STORAGE\_UNKNOWN)](#store)
- [MMSmsCdmaTeleserviceId teleserviceId() const](#teleserviceId)
- [QString text() const](#text)
- [int timeout() const](#timeout)
- [QDateTime timestamp() const](#timestamp)
- [QString uni() const](#uni)
- [ModemManager::ValidityPair validity() const](#validity)

## Signals

- [void SMSCChanged(const QString &smsc)](#SMSCChanged)
- [void dataChanged(const QByteArray &data)](#dataChanged)
- [void deliveryReportRequestChanged(bool deliveryReportRequest)](#deliveryReportRequestChanged)
- [void deliveryStateChanged(MMSmsDeliveryState newDeliveryState)](#deliveryStateChanged)
- [void dischargeTimestampChanged(const QDateTime &dischargeTimestamp)](#dischargeTimestampChanged)
- [void messageReferenceChanged(uint messageReference)](#messageReferenceChanged)
- [void numberChanged(const QString &number)](#numberChanged)
- [void pduTypeChanged(MMSmsPduType pduType)](#pduTypeChanged)
- [void serviceCategoryChanged(MMSmsCdmaServiceCategory serviceCategory)](#serviceCategoryChanged)
- [void smsClassChanged(int smsClass)](#smsClassChanged)
- [void stateChanged(MMSmsState newState)](#stateChanged)
- [void storageChanged(MMSmsStorage storage)](#storageChanged)
- [void teleserviceIdChanged(MMSmsCdmaTeleserviceId teleserviceId)](#teleserviceIdChanged)
- [void textChanged(const QString &text)](#textChanged)
- [void timestampChanged(const QDateTime &timestamp)](#timestampChanged)
- [void validityChanged(const ModemManager::ValidityPair &validity)](#validityChanged)

## Detailed Description {#details}

> **Note:** MMSmsStorage, MMSmsState, MMSmsPduType and MMSmsDeliveryState enums are defined in \<[ModemManager](modemmanager.md)/[ModemManager](modemmanager.md)-enums.h\> See http://www.freedesktop.org/software/[ModemManager](modemmanager.md)/api/1.0.0/[ModemManager](modemmanager.md)-Flags-and-Enumerations.html .

## Member Type Documentation {#member-type-documentation}

### Sms::List {#List-typedef}

### Sms::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Sms::Sms(const QString &*path*, QObject \**parent* = nullptr) {#Sms}

### QString Sms::SMSC() const {#SMSC}

This method returns the SMS service center number

### \[signal\] void Sms::SMSCChanged(const QString &*smsc*) {#SMSCChanged}

### QByteArray Sms::data() const {#data}

This method returns the SMS message data. [text](modemmanager-sms.md#text)() and data() are not valid at the same time

### \[signal\] void Sms::dataChanged(const QByteArray &*data*) {#dataChanged}

### bool Sms::deliveryReportRequest() const {#deliveryReportRequest}

Returns `true` if a delivery report is requested, `false` otherwise

### \[signal\] void Sms::deliveryReportRequestChanged(bool *deliveryReportRequest*) {#deliveryReportRequestChanged}

### MMSmsDeliveryState Sms::deliveryState() const {#deliveryState}

This method returns the delivery state of the SMS

### \[signal\] void Sms::deliveryStateChanged(MMSmsDeliveryState *newDeliveryState*) {#deliveryStateChanged}

This signal is emitted when the delivery state of the SMS has changed

`newDeliveryState` the new delivery state of the SMS

### QDateTime Sms::dischargeTimestamp() const {#dischargeTimestamp}

Time when the SMS left the SMSC

### \[signal\] void Sms::dischargeTimestampChanged(const QDateTime &*dischargeTimestamp*) {#dischargeTimestampChanged}

### uint Sms::messageReference() const {#messageReference}

This method returns the message reference of the last PDU sent/received in the SMS. The message reference is the number used to identify the SMS in the SMSC. If the PDU type is MM\_SMS\_PDU\_TYPE\_STATUS\_REPORT, this field identifies the Message Reference of the PDU associated to the status report

### \[signal\] void Sms::messageReferenceChanged(uint *messageReference*) {#messageReferenceChanged}

### QString Sms::number() const {#number}

This method returns the phone number to which the SMS is addressed to

### \[signal\] void Sms::numberChanged(const QString &*number*) {#numberChanged}

### MMSmsPduType Sms::pduType() const {#pduType}

This method returns the Protocol Data Unit (PDU) type of the SMS

### \[signal\] void Sms::pduTypeChanged(MMSmsPduType *pduType*) {#pduTypeChanged}

### QDBusPendingReply\<\> Sms::send() {#send}

Send the SMS

### MMSmsCdmaServiceCategory Sms::serviceCategory() const {#serviceCategory}

Returns service category for CDMA SMS, as defined in 3GPP2 C.R1001-D (section 9.3).

### \[signal\] void Sms::serviceCategoryChanged(MMSmsCdmaServiceCategory *serviceCategory*) {#serviceCategoryChanged}

### void Sms::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-sms.md#timeout)()

### int Sms::smsClass() const {#smsClass}

This method returns the 3GPP class of the SMS

### \[signal\] void Sms::smsClassChanged(int *smsClass*) {#smsClassChanged}

### MMSmsState Sms::state() const {#state}

This method returns the state of the SMS

### \[signal\] void Sms::stateChanged(MMSmsState *newState*) {#stateChanged}

This signal is emitted when the state of the SMS has changed

`newState` the new state of the SMS

### MMSmsStorage Sms::storage() const {#storage}

This method returns the storage area/location of the SMS

### \[signal\] void Sms::storageChanged(MMSmsStorage *storage*) {#storageChanged}

### QDBusPendingReply\<\> Sms::store(MMSmsStorage *storage* = MM\_SMS\_STORAGE\_UNKNOWN) {#store}

Store the SMS

`storage` the storage location of the SMS (empty for default storage)

### MMSmsCdmaTeleserviceId Sms::teleserviceId() const {#teleserviceId}

Returns teleservice IDs supported for CDMA SMS, as defined in 3GPP2 X.S0004-550-E (section 2.256) and 3GPP2 C.S0015-B (section 3.4.3.1)

### \[signal\] void Sms::teleserviceIdChanged(MMSmsCdmaTeleserviceId *teleserviceId*) {#teleserviceIdChanged}

### QString Sms::text() const {#text}

This method returns the text of the SMS. text() and [data](modemmanager-sms.md#data)() are not valid at the same time

### \[signal\] void Sms::textChanged(const QString &*text*) {#textChanged}

### int Sms::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-sms.md#setTimeout)()

### QDateTime Sms::timestamp() const {#timestamp}

Time when the SMS arrived at the SMSC

### \[signal\] void Sms::timestampChanged(const QDateTime &*timestamp*) {#timestampChanged}

### QString Sms::uni() const {#uni}

### ModemManager::ValidityPair Sms::validity() const {#validity}

This method returns the validity of the SMS

Returns A [ValidityPair](modemmanager.md#ValidityPair-typedef) struct composed of a MMSmsValidityType type and a value indicating the validity of the SMS

### \[signal\] void Sms::validityChanged(const ModemManager::ValidityPair &*validity*) {#validityChanged}
