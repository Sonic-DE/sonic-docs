---
title: "Attica::Provider Class"
description: "The Provider class represents one Open Collaboration Service provider."
---

# Attica::Provider Class

The Provider class represents one Open Collaboration Service provider. [More...](#details)

- **Header:** `#include <Attica/Provider>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-provider-members.md)

## Public Types

- [enum Provider::SortMode](#SortMode-enum)

## Public Functions

- [Provider()](#Provider)
- [QString achievementServiceVersion() const](#achievementServiceVersion)
- [QString activityServiceVersion() const](#activityServiceVersion)
- [Attica::ItemPostJob\<Attica::Achievement\> \*addNewAchievement(const QString &id, const Attica::Achievement &newAchievement)](#addNewAchievement)
- [Attica::ItemPostJob\<Attica::Comment\> \*addNewComment(const Attica::Comment::Type commentType, const QString &id, const QString &id2, const QString &parentId, const QString &subject, const QString &message)](#addNewComment)
- [Attica::ItemPostJob\<Attica::Content\> \*addNewContent(const Attica::Category &category, const Attica::Content &newContent)](#addNewContent)
- [QString additionalAgentInformation() const](#additionalAgentInformation)
- [Attica::PostJob \*approveFriendship(const QString &to)](#approveFriendship)
- [QUrl baseUrl() const](#baseUrl)
- [Attica::PostJob \*becomeFan(const QString &contentId)](#becomeFan)
- [Attica::PostJob \*cancelBuildServiceJob(const Attica::BuildServiceJob &job)](#cancelBuildServiceJob)
- [Attica::PostJob \*cancelFriendship(const QString &to)](#cancelFriendship)
- [Attica::PostJob \*checkLogin(const QString &user, const QString &password)](#checkLogin)
- [QString commentServiceVersion() const](#commentServiceVersion)
- [QString contentServiceVersion() const](#contentServiceVersion)
- [Attica::PostJob \*createBuildServiceJob(const Attica::BuildServiceJob &job)](#createBuildServiceJob)
- [Attica::PostJob \*createProject(const Attica::Project &project)](#createProject)
- [Attica::PostJob \*createRemoteAccount(const Attica::RemoteAccount &account)](#createRemoteAccount)
- [Attica::PostJob \*declineFriendship(const QString &to)](#declineFriendship)
- [Attica::DeleteJob \*deleteAchievement(const QString &contentId, const QString &achievementId)](#deleteAchievement)
- [Attica::PostJob \*deleteContent(const QString &contentId)](#deleteContent)
- [Attica::PostJob \*deleteDownloadFile(const QString &contentId)](#deleteDownloadFile)
- [Attica::PostJob \*deletePreviewImage(const QString &contentId, const QString &previewId)](#deletePreviewImage)
- [Attica::PostJob \*deleteProject(const Attica::Project &project)](#deleteProject)
- [Attica::PostJob \*deleteRemoteAccount(const QString &id)](#deleteRemoteAccount)
- [Attica::ItemJob\<Attica::DownloadItem\> \*downloadLink(const QString &contentId, const QString &itemId = QStringLiteral("1"))](#downloadLink)
- [Attica::PutJob \*editAchievement(const QString &contentId, const QString &achievementId, const Attica::Achievement &achievement)](#editAchievement)
- [Attica::ItemPostJob\<Attica::Content\> \*editContent(const Attica::Category &updatedCategory, const QString &contentId, const Attica::Content &updatedContent)](#editContent)
- [Attica::PostJob \*editProject(const Attica::Project &project)](#editProject)
- [Attica::PostJob \*editRemoteAccount(const Attica::RemoteAccount &account)](#editRemoteAccount)
- [QString fanServiceVersion() const](#fanServiceVersion)
- [QString forumServiceVersion() const](#forumServiceVersion)
- [QString friendServiceVersion() const](#friendServiceVersion)
- [const QString &getRegisterAccountUrl() const](#getRegisterAccountUrl)
- [bool hasAchievementService() const](#hasAchievementService)
- [bool hasActivityService() const](#hasActivityService)
- [bool hasCommentService() const](#hasCommentService)
- [bool hasContentService() const](#hasContentService)
- [bool hasCredentials() const](#hasCredentials)
- [bool hasFanService() const](#hasFanService)
- [bool hasForumService() const](#hasForumService)
- [bool hasFriendService() const](#hasFriendService)
- [bool hasKnowledgebaseService() const](#hasKnowledgebaseService)
- [bool hasMessageService() const](#hasMessageService)
- [bool hasPersonService() const](#hasPersonService)
- [QUrl icon() const](#icon)
- [Attica::PostJob \*inviteFriend(const QString &to, const QString &message)](#inviteFriend)
- [bool isEnabled() const](#isEnabled)
- [bool isValid() const](#isValid)
- [QString knowledgebaseServiceVersion() const](#knowledgebaseServiceVersion)
- [bool loadCredentials(QString &user, QString &password)](#loadCredentials)
- [QString messageServiceVersion() const](#messageServiceVersion)
- [QString name() const](#name)
- [QString personServiceVersion() const](#personServiceVersion)
- [Attica::PostJob \*postActivity(const QString &message)](#postActivity)
- [Attica::PostJob \*postLocation(qreal latitude, qreal longitude, const QString &city = QString(), const QString &country = QString())](#postLocation)
- [Attica::PostJob \*postMessage(const Attica::Message &message)](#postMessage)
- [Attica::PostJob \*postTopic(const QString &forumId, const QString &subject, const QString &content)](#postTopic)
- [Attica::PostJob \*publishBuildJob(const Attica::BuildServiceJob &buildjob, const Attica::Publisher &publisher)](#publishBuildJob)
- [Attica::PostJob \*registerAccount(const QString &id, const QString &password, const QString &mail, const QString &firstName, const QString &lastName)](#registerAccount)
- [Attica::ItemJob\<Attica::AccountBalance\> \*requestAccountBalance()](#requestAccountBalance)
- [Attica::ListJob\<Attica::Achievement\> \*requestAchievements(const QString &contentId, const QString &achievementId, const QString &userId)](#requestAchievements)
- [Attica::ListJob\<Attica::Activity\> \*requestActivities()](#requestActivities)
- [Attica::ItemJob\<Attica::BuildService\> \*requestBuildService(const QString &id)](#requestBuildService)
- [Attica::ItemJob\<Attica::BuildServiceJob\> \*requestBuildServiceJob(const QString &id)](#requestBuildServiceJob)
- [Attica::ItemJob\<Attica::BuildServiceJobOutput\> \*requestBuildServiceJobOutput(const QString &id)](#requestBuildServiceJobOutput)
- [Attica::ListJob\<Attica::BuildServiceJob\> \*requestBuildServiceJobs(const Attica::Project &project)](#requestBuildServiceJobs)
- [Attica::ListJob\<Attica::BuildService\> \*requestBuildServices()](#requestBuildServices)
- [Attica::ListJob\<Attica::Category\> \*requestCategories()](#requestCategories)
- [Attica::ListJob\<Attica::Comment\> \*requestComments(const Attica::Comment::Type commentType, const QString &id, const QString &id2, int page, int pageSize)](#requestComments)
- [Attica::ItemJob\<Attica::Config\> \*requestConfig()](#requestConfig)
- [Attica::ItemJob\<Attica::Content\> \*requestContent(const QString &contentId)](#requestContent)
- [Attica::ListJob\<Attica::Distribution\> \*requestDistributions()](#requestDistributions)
- [Attica::ItemJob\<Attica::Event\> \*requestEvent(const QString &id)](#requestEvent)
- [Attica::ListJob\<Attica::Event\> \*requestEvent(const QString &country, const QString &search, const QDate &startAt, Attica::Provider::SortMode mode, int page, int pageSize)](#requestEvent-1)
- [Attica::ListJob\<Attica::Person\> \*requestFans(const QString &contentId, uint page = 0, uint pageSize = 10)](#requestFans)
- [Attica::ListJob\<Attica::Folder\> \*requestFolders()](#requestFolders)
- [Attica::ListJob\<Attica::Forum\> \*requestForums(uint page = 0, uint pageSize = 10)](#requestForums)
- [Attica::ListJob\<Attica::Person\> \*requestFriends(const QString &id, int page = 0, int pageSize = 20)](#requestFriends)
- [Attica::ListJob\<Attica::HomePageType\> \*requestHomePageTypes()](#requestHomePageTypes)
- [Attica::ItemJob\<Attica::KnowledgeBaseEntry\> \*requestKnowledgeBaseEntry(const QString &id)](#requestKnowledgeBaseEntry)
- [Attica::ListJob\<Attica::License\> \*requestLicenses()](#requestLicenses)
- [Attica::ItemJob\<Attica::Message\> \*requestMessage(const Attica::Folder &folder, const QString &id)](#requestMessage)
- [Attica::ListJob\<Attica::Message\> \*requestMessages(const Attica::Folder &folder)](#requestMessages)
- [Attica::ListJob\<Attica::Message\> \*requestMessages(const Attica::Folder &folder, Attica::Message::Status status)](#requestMessages-1)
- [Attica::ItemJob\<Attica::Person\> \*requestPerson(const QString &id)](#requestPerson)
- [Attica::ListJob\<Attica::Person\> \*requestPersonSearchByLocation(qreal latitude, qreal longitude, qreal distance = 0.0, int page = 0, int pageSize = 20)](#requestPersonSearchByLocation)
- [Attica::ListJob\<Attica::Person\> \*requestPersonSearchByName(const QString &name)](#requestPersonSearchByName)
- [Attica::ItemJob\<Attica::Person\> \*requestPersonSelf()](#requestPersonSelf)
- [Attica::ItemJob\<Attica::PrivateData\> \*requestPrivateData()](#requestPrivateData)
- [Attica::ItemJob\<Attica::PrivateData\> \*requestPrivateData(const QString &app, const QString &key = QString())](#requestPrivateData-1)
- [Attica::ItemJob\<Attica::Project\> \*requestProject(const QString &id)](#requestProject)
- [Attica::ListJob\<Attica::Project\> \*requestProjects()](#requestProjects)
- [Attica::ItemJob\<Attica::Publisher\> \*requestPublisher(const QString &id)](#requestPublisher)
- [Attica::ListJob\<Attica::Publisher\> \*requestPublishers()](#requestPublishers)
- [Attica::ListJob\<Attica::Person\> \*requestReceivedInvitations(int page = 0, int pageSize = 20)](#requestReceivedInvitations)
- [Attica::ItemJob\<Attica::RemoteAccount\> \*requestRemoteAccount(const QString &id)](#requestRemoteAccount)
- [Attica::ListJob\<Attica::RemoteAccount\> \*requestRemoteAccounts()](#requestRemoteAccounts)
- [Attica::ListJob\<Attica::Person\> \*requestSentInvitations(int page = 0, int pageSize = 20)](#requestSentInvitations)
- [Attica::ListJob\<Attica::Topic\> \*requestTopics(const QString &forum, const QString &search, const QString &description, Attica::Provider::SortMode mode, int page, int pageSize)](#requestTopics)
- [Attica::DeleteJob \*resetAchievementProgress(const QString &id)](#resetAchievementProgress)
- [bool saveCredentials(const QString &user, const QString &password)](#saveCredentials)
- [Attica::PostJob \*savePublisherField(const Attica::Project &project, const Attica::PublisherField &field)](#savePublisherField)
- [Attica::ListJob\<Attica::Content\> \*searchContents(const Category::List &categories, const QString &search = QString(), Attica::Provider::SortMode mode = Rating, uint page = 0, uint pageSize = 10)](#searchContents)
- [Attica::ListJob\<Attica::Content\> \*searchContents(const Category::List &categories, const QString &person, const Distribution::List &distributions, const License::List &licenses, const QString &search = QString(), Attica::Provider::SortMode sortMode = Rating, uint page = 0, uint pageSize = 10)](#searchContents-1)
- [Attica::ListJob\<Attica::Content\> \*searchContentsByPerson(const Category::List &categories, const QString &person, const QString &search = QString(), Attica::Provider::SortMode mode = Rating, uint page = 0, uint pageSize = 10)](#searchContentsByPerson)
- [Attica::ListJob\<Attica::KnowledgeBaseEntry\> \*searchKnowledgeBase(const Attica::Content &content, const QString &search, Attica::Provider::SortMode, int page, int pageSize)](#searchKnowledgeBase)
- [Attica::PostJob \*setAchievementProgress(const QString &id, const QVariant &progress, const QDateTime &timestamp)](#setAchievementProgress)
- [void setAdditionalAgentInformation(const QString &additionalInformation)](#setAdditionalAgentInformation)
- [Attica::PostJob \*setDownloadFile(const QString &contentId, const QString &fileName, QIODevice \*payload)](#setDownloadFile)
- [Attica::PostJob \*setDownloadFile(const QString &contentId, const QString &fileName, const QByteArray &payload)](#setDownloadFile-1)
- [void setEnabled(bool enabled)](#setEnabled)
- [Attica::PostJob \*setPreviewImage(const QString &contentId, const QString &previewId, const QString &fileName, const QByteArray &image)](#setPreviewImage)
- [Attica::PostJob \*setPrivateData(const QString &app, const QString &key, const QString &value)](#setPrivateData)
- [Attica::PostJob \*uploadTarballToBuildService(const QString &projectId, const QString &fileName, const QByteArray &payload)](#uploadTarballToBuildService)
- [Attica::PostJob \*voteForComment(const QString &id, uint rating)](#voteForComment)
- [Attica::PostJob \*voteForContent(const QString &contentId, uint rating)](#voteForContent)

## Detailed Description {#details}

Use the [ProviderManager](attica-providermanager.md) to instantiate a Provider.

Accessing functions of the Provider returns a Job class that takes care of accessing the server and parsing the result.

Provider files are xml of the form:

```cpp
<provider>
<id>opendesktop</id>
<location>https://api.opendesktop.org/v1/</location>
<name>openDesktop.org</name>
<icon></icon>
<termsofuse>https://opendesktop.org/terms/</termsofuse>
<register>https://opendesktop.org/usermanager/new.php</register>
<services>
  <person ocsversion="1.3" />
  <friend ocsversion="1.3" />
  <message ocsversion="1.3" />
  <activity ocsversion="1.3" />
  <content ocsversion="1.3" />
  <fan ocsversion="1.3" />
  <knowledgebase ocsversion="1.3" />
  <event ocsversion="1.3" />
  <comment ocsversion="1.2" />
</services>
</provider>
```

The server provides the services specified in the services section, not necessarily all of them.

## Member Type Documentation {#member-type-documentation}

### enum Provider::SortMode {#SortMode-enum}

| Constant |   |
| --- | --- |
| `Attica::Provider::Newest` | `0` |
| `Attica::Provider::Alphabetical` | `1` |
| `Attica::Provider::Rating` | `2` |
| `Attica::Provider::Downloads` | `3` |

## Member Function Documentation {#member-function-documentation}

### Provider::Provider() {#Provider}

Default construct a Provider. Please note that this provider is incomplete and never valid.

### QString Provider::achievementServiceVersion() const {#achievementServiceVersion}

Version of the achievement part of the API

### QString Provider::activityServiceVersion() const {#activityServiceVersion}

Version of the activity part of the API

### Attica::ItemPostJob\<Attica::Achievement\> \*Provider::addNewAchievement(const QString &*id*, const Attica::Achievement &*newAchievement*) {#addNewAchievement}

Add a new achievement.

`id` id of the achievement entry

`achievement` The new Achievement added

Returns item post job for adding the new achievement

### Attica::ItemPostJob\<Attica::Comment\> \*Provider::addNewComment(const Attica::Comment::Type *commentType*, const QString &*id*, const QString &*id2*, const QString &*parentId*, const QString &*subject*, const QString &*message*) {#addNewComment}

Add a new comment.

`commentType` type of the comment CommentType (content / forum / knowledgebase / event)

`id` id of the content entry where you want to get the comments is from

`id2` id of the sub content entry where you want to get the comments is from

`parentId` the id of the parent comment if the new comment is a reply

`subject` title of the comment

`message` text of the comment

Returns item post job for adding the new comment

### Attica::ItemPostJob\<Attica::Content\> \*Provider::addNewContent(const Attica::Category &*category*, const Attica::Content &*newContent*) {#addNewContent}

### QString Provider::additionalAgentInformation() const {#additionalAgentInformation}

The custom identifier sent along with requests

Returns the custom identifier

*See also* [setAdditionalAgentInformation](attica-provider.md#setAdditionalAgentInformation)(const QString&)

### Attica::PostJob \*Provider::approveFriendship(const QString &*to*) {#approveFriendship}

### QUrl Provider::baseUrl() const {#baseUrl}

A url that identifies this provider. This should be used as identifier when referring to this provider but you don't want to use the full provider object.

### Attica::PostJob \*Provider::becomeFan(const QString &*contentId*) {#becomeFan}

### Attica::PostJob \*Provider::cancelBuildServiceJob(const Attica::BuildServiceJob &*job*) {#cancelBuildServiceJob}

Cancel a job. Setting the ID on the build service parameter is enough for it to work.

`job` Buildservicejob to cancel on the server, needs at least id set.

### Attica::PostJob \*Provider::cancelFriendship(const QString &*to*) {#cancelFriendship}

### Attica::PostJob \*Provider::checkLogin(const QString &*user*, const QString &*password*) {#checkLogin}

Test if the server accepts the login/password.

This function does not actually set the credentials. Use [saveCredentials](attica-provider.md#saveCredentials) for that purpose.

`user` the user (login) name

`password` the password

Returns the job that will contain the success of the login as metadata

### QString Provider::commentServiceVersion() const {#commentServiceVersion}

Version of the comments part of the API

### QString Provider::contentServiceVersion() const {#contentServiceVersion}

Version of the content part of the API

### Attica::PostJob \*Provider::createBuildServiceJob(const Attica::BuildServiceJob &*job*) {#createBuildServiceJob}

Create a new job for a given project on a given buildservice for a given target. Those three items are mandatory for the job to succeed.

`job` Buildservicejob to create on the server

### Attica::PostJob \*Provider::createProject(const Attica::Project &*project*) {#createProject}

Post modifications to a Project on the server. The resulting project ID can be found in the Attica::MetaData of the finished() [PostJob](attica-postjob.md). You can retrieve it using Attica::MetaData::resultingProjectId().

`project` Project to create on the server

### Attica::PostJob \*Provider::createRemoteAccount(const Attica::RemoteAccount &*account*) {#createRemoteAccount}

Create a new remote account, an account for a build service instance which is stored in the OCS service in order to authenticate with the build service instance. Type, Type ID, login and password are mandatory.

`account` [RemoteAccount](attica-remoteaccount.md) to create on the server

### Attica::PostJob \*Provider::declineFriendship(const QString &*to*) {#declineFriendship}

### Attica::DeleteJob \*Provider::deleteAchievement(const QString &*contentId*, const QString &*achievementId*) {#deleteAchievement}

Deletes an achievement on the server. The achievement passed as an argument doesn't need complete information as just the id() is used.

`achievementId` Achievement to delete on the server.

### Attica::PostJob \*Provider::deleteContent(const QString &*contentId*) {#deleteContent}

### Attica::PostJob \*Provider::deleteDownloadFile(const QString &*contentId*) {#deleteDownloadFile}

### Attica::PostJob \*Provider::deletePreviewImage(const QString &*contentId*, const QString &*previewId*) {#deletePreviewImage}

### Attica::PostJob \*Provider::deleteProject(const Attica::Project &*project*) {#deleteProject}

Deletes a project on the server. The project passed as an argument doesn't need complete information as just the id() is used.

`project` Project to delete on the server.

### Attica::PostJob \*Provider::deleteRemoteAccount(const QString &*id*) {#deleteRemoteAccount}

Deletes a remote account stored on the OCS server.

`id` The ID of the remote account on the OCS instance.

### Attica::ItemJob\<Attica::DownloadItem\> \*Provider::downloadLink(const QString &*contentId*, const QString &*itemId* = QStringLiteral("1")) {#downloadLink}

### Attica::PutJob \*Provider::editAchievement(const QString &*contentId*, const QString &*achievementId*, const Attica::Achievement &*achievement*) {#editAchievement}

Post modifications to an Achievement on the server

`achievement` Achievement to update on the server

### Attica::ItemPostJob\<Attica::Content\> \*Provider::editContent(const Attica::Category &*updatedCategory*, const QString &*contentId*, const Attica::Content &*updatedContent*) {#editContent}

### Attica::PostJob \*Provider::editProject(const Attica::Project &*project*) {#editProject}

Post modifications to a Project on the server

`project` Project to update on the server

### Attica::PostJob \*Provider::editRemoteAccount(const Attica::RemoteAccount &*account*) {#editRemoteAccount}

Edit an existing remote account.

`account` [RemoteAccount](attica-remoteaccount.md) to create on the server

### QString Provider::fanServiceVersion() const {#fanServiceVersion}

Version of the fan part of the API

### QString Provider::forumServiceVersion() const {#forumServiceVersion}

Version of the forum part of the API

### QString Provider::friendServiceVersion() const {#friendServiceVersion}

Version of the friend part of the API

### const QString &Provider::getRegisterAccountUrl() const {#getRegisterAccountUrl}

### bool Provider::hasAchievementService() const {#hasAchievementService}

Test if the server supports the achievement part of the API

### bool Provider::hasActivityService() const {#hasActivityService}

Test if the server supports the activity part of the API

### bool Provider::hasCommentService() const {#hasCommentService}

Test if the server supports the comments part of the API

### bool Provider::hasContentService() const {#hasContentService}

Test if the server supports the content part of the API

### bool Provider::hasCredentials() const {#hasCredentials}

Test if the provider has user name/password available. This does not yet open kwallet in case the KDE plugin is used. Returns true if the provider has login information

### bool Provider::hasFanService() const {#hasFanService}

Test if the server supports the fan part of the API

### bool Provider::hasForumService() const {#hasForumService}

Test if the server supports the forum part of the API

### bool Provider::hasFriendService() const {#hasFriendService}

Test if the server supports the friend part of the API

### bool Provider::hasKnowledgebaseService() const {#hasKnowledgebaseService}

\* Test if the server supports the knowledgebase part of the API

### bool Provider::hasMessageService() const {#hasMessageService}

Test if the server supports the message part of the API

### bool Provider::hasPersonService() const {#hasPersonService}

Test if the server supports the person part of the API

### QUrl Provider::icon() const {#icon}

An icon used to visually identify this provider Returns a URL for an icon image (or an invalid URL if one was not defined by the provider)

### Attica::PostJob \*Provider::inviteFriend(const QString &*to*, const QString &*message*) {#inviteFriend}

### bool Provider::isEnabled() const {#isEnabled}

Test if the provider is enabled by the settings. The application can choose to ignore this, but the user settings should be respected.

### bool Provider::isValid() const {#isValid}

Returns true if the provider has been set up and can be used.

### QString Provider::knowledgebaseServiceVersion() const {#knowledgebaseServiceVersion}

Version of the knowledgebase part of the API

### bool Provider::loadCredentials(QString &*user*, QString &*password*) {#loadCredentials}

Load user name and password from the store.

Attica will remember the loaded values and use them from this point on.

`user` reference that returns the user name

`password` reference that returns the password

Returns if credentials could be loaded

### QString Provider::messageServiceVersion() const {#messageServiceVersion}

Version of the message part of the API

### QString Provider::name() const {#name}

A name for the provider that can be displayed to the user

### QString Provider::personServiceVersion() const {#personServiceVersion}

Version of the person part of the API

### Attica::PostJob \*Provider::postActivity(const QString &*message*) {#postActivity}

### Attica::PostJob \*Provider::postLocation(qreal *latitude*, qreal *longitude*, const QString &*city* = QString(), const QString &*country* = QString()) {#postLocation}

### Attica::PostJob \*Provider::postMessage(const Attica::Message &*message*) {#postMessage}

### Attica::PostJob \*Provider::postTopic(const QString &*forumId*, const QString &*subject*, const QString &*content*) {#postTopic}

### Attica::PostJob \*Provider::publishBuildJob(const Attica::BuildServiceJob &*buildjob*, const Attica::Publisher &*publisher*) {#publishBuildJob}

Publish the result of a completed build job to a publisher. Returns [ItemJob](attica-itemjob.md) receiving data

### Attica::PostJob \*Provider::registerAccount(const QString &*id*, const QString &*password*, const QString &*mail*, const QString &*firstName*, const QString &*lastName*) {#registerAccount}

### Attica::ItemJob\<Attica::AccountBalance\> \*Provider::requestAccountBalance() {#requestAccountBalance}

### Attica::ListJob\<Attica::Achievement\> \*Provider::requestAchievements(const QString &*contentId*, const QString &*achievementId*, const QString &*userId*) {#requestAchievements}

Get a list of achievements Returns [ListJob](attica-listjob.md) listing Achievements

### Attica::ListJob\<Attica::Activity\> \*Provider::requestActivities() {#requestActivities}

### Attica::ItemJob\<Attica::BuildService\> \*Provider::requestBuildService(const QString &*id*) {#requestBuildService}

Get the information for a specific build service instance. Returns [ItemJob](attica-itemjob.md) receiving data

### Attica::ItemJob\<Attica::BuildServiceJob\> \*Provider::requestBuildServiceJob(const QString &*id*) {#requestBuildServiceJob}

Get the information for a specific build service job, such as status and progress. Returns [ItemJob](attica-itemjob.md) receiving and containing the data

### Attica::ItemJob\<Attica::BuildServiceJobOutput\> \*Provider::requestBuildServiceJobOutput(const QString &*id*) {#requestBuildServiceJobOutput}

Get the build output for a specific build service job Returns [ItemJob](attica-itemjob.md) receiving and containing the output data

### Attica::ListJob\<Attica::BuildServiceJob\> \*Provider::requestBuildServiceJobs(const Attica::Project &*project*) {#requestBuildServiceJobs}

Get a list of build service projects Returns [ListJob](attica-listjob.md) listing BuildServiceJobs

### Attica::ListJob\<Attica::BuildService\> \*Provider::requestBuildServices() {#requestBuildServices}

Get a list of build service build services Returns [ListJob](attica-listjob.md) listing BuildServices

### Attica::ListJob\<Attica::Category\> \*Provider::requestCategories() {#requestCategories}

Get a list of categories (such as wallpaper) Returns the categories of the server

### Attica::ListJob\<Attica::Comment\> \*Provider::requestComments(const Attica::Comment::Type *commentType*, const QString &*id*, const QString &*id2*, int *page*, int *pageSize*) {#requestComments}

Request a list of comments for a content / forum / knowledgebase / event.

`type` of the comment [Comment::Type](attica-comment.md#Type-enum) (content / forum / knowledgebase / event)

`id` id of the content entry where you want to get the comments is from

`id2` id of the content entry where you want to get the comments is from

`page` request nth page in the list of results

`pageSize` requested size of pages when calculating the list of results

Returns list job for the comments results

### Attica::ItemJob\<Attica::Config\> \*Provider::requestConfig() {#requestConfig}

Fetches server config Returns The job responsible for fetching data

### Attica::ItemJob\<Attica::Content\> \*Provider::requestContent(const QString &*contentId*) {#requestContent}

Retrieve a single content.

`contentId` the id of the content

Returns job that retrieves the content object

### Attica::ListJob\<Attica::Distribution\> \*Provider::requestDistributions() {#requestDistributions}

Get a list of distributions (such as Ark, Debian) Returns the licenses available from the server

### Attica::ItemJob\<Attica::Event\> \*Provider::requestEvent(const QString &*id*) {#requestEvent}

### Attica::ListJob\<Attica::Event\> \*Provider::requestEvent(const QString &*country*, const QString &*search*, const QDate &*startAt*, Attica::Provider::SortMode *mode*, int *page*, int *pageSize*) {#requestEvent-1}

### Attica::ListJob\<Attica::Person\> \*Provider::requestFans(const QString &*contentId*, uint *page* = 0, uint *pageSize* = 10) {#requestFans}

### Attica::ListJob\<Attica::Folder\> \*Provider::requestFolders() {#requestFolders}

### Attica::ListJob\<Attica::Forum\> \*Provider::requestForums(uint *page* = 0, uint *pageSize* = 10) {#requestForums}

### Attica::ListJob\<Attica::Person\> \*Provider::requestFriends(const QString &*id*, int *page* = 0, int *pageSize* = 20) {#requestFriends}

### Attica::ListJob\<Attica::HomePageType\> \*Provider::requestHomePageTypes() {#requestHomePageTypes}

Get a list of home page types (such as blog, Facebook) Returns the licenses available from the server

### Attica::ItemJob\<Attica::KnowledgeBaseEntry\> \*Provider::requestKnowledgeBaseEntry(const QString &*id*) {#requestKnowledgeBaseEntry}

### Attica::ListJob\<Attica::License\> \*Provider::requestLicenses() {#requestLicenses}

Get a list of licenses (such as GPL) Returns the licenses available from the server

### Attica::ItemJob\<Attica::Message\> \*Provider::requestMessage(const Attica::Folder &*folder*, const QString &*id*) {#requestMessage}

### Attica::ListJob\<Attica::Message\> \*Provider::requestMessages(const Attica::Folder &*folder*) {#requestMessages}

### Attica::ListJob\<Attica::Message\> \*Provider::requestMessages(const Attica::Folder &*folder*, Attica::Message::Status *status*) {#requestMessages-1}

### Attica::ItemJob\<Attica::Person\> \*Provider::requestPerson(const QString &*id*) {#requestPerson}

### Attica::ListJob\<Attica::Person\> \*Provider::requestPersonSearchByLocation(qreal *latitude*, qreal *longitude*, qreal *distance* = 0.0, int *page* = 0, int *pageSize* = 20) {#requestPersonSearchByLocation}

### Attica::ListJob\<Attica::Person\> \*Provider::requestPersonSearchByName(const QString &*name*) {#requestPersonSearchByName}

### Attica::ItemJob\<Attica::Person\> \*Provider::requestPersonSelf() {#requestPersonSelf}

### Attica::ItemJob\<Attica::PrivateData\> \*Provider::requestPrivateData() {#requestPrivateData}

Fetches all stored private data.

Returns The job responsible for fetching data

### Attica::ItemJob\<Attica::PrivateData\> \*Provider::requestPrivateData(const QString &*app*, const QString &*key* = QString()) {#requestPrivateData-1}

Fetches the a given attribute from an OCS-compliant server.

`app` The application name

`key` The key of the attribute to fetch (optional)

Returns The job that is responsible for fetching the data

### Attica::ItemJob\<Attica::Project\> \*Provider::requestProject(const QString &*id*) {#requestProject}

Get a Project's data Returns [ItemJob](attica-itemjob.md) receiving data

### Attica::ListJob\<Attica::Project\> \*Provider::requestProjects() {#requestProjects}

Get a list of build service projects Returns [ListJob](attica-listjob.md) listing Projects

### Attica::ItemJob\<Attica::Publisher\> \*Provider::requestPublisher(const QString &*id*) {#requestPublisher}

Get the information for a specific publisher. Returns [ItemJob](attica-itemjob.md) receiving data

### Attica::ListJob\<Attica::Publisher\> \*Provider::requestPublishers() {#requestPublishers}

Get a list of publishers Returns [ListJob](attica-listjob.md) listing Publishers

### Attica::ListJob\<Attica::Person\> \*Provider::requestReceivedInvitations(int *page* = 0, int *pageSize* = 20) {#requestReceivedInvitations}

### Attica::ItemJob\<Attica::RemoteAccount\> \*Provider::requestRemoteAccount(const QString &*id*) {#requestRemoteAccount}

Get a remote account by its ID.

`id` The ID of the remote account

### Attica::ListJob\<Attica::RemoteAccount\> \*Provider::requestRemoteAccounts() {#requestRemoteAccounts}

Get a list of remote accounts, account for a build service instance which is stored in the OCS service in order to authenticate with the build service instance. Returns [ListJob](attica-listjob.md) listing RemoteAccounts

### Attica::ListJob\<Attica::Person\> \*Provider::requestSentInvitations(int *page* = 0, int *pageSize* = 20) {#requestSentInvitations}

### Attica::ListJob\<Attica::Topic\> \*Provider::requestTopics(const QString &*forum*, const QString &*search*, const QString &*description*, Attica::Provider::SortMode *mode*, int *page*, int *pageSize*) {#requestTopics}

### Attica::DeleteJob \*Provider::resetAchievementProgress(const QString &*id*) {#resetAchievementProgress}

### bool Provider::saveCredentials(const QString &*user*, const QString &*password*) {#saveCredentials}

Sets (and remembers) user name and password for this provider.

To remove the data an empty username should be passed.

`user` the user (login) name

`password` the password

Returns if credentials could be saved

### Attica::PostJob \*Provider::savePublisherField(const Attica::Project &*project*, const Attica::PublisherField &*field*) {#savePublisherField}

Save the value of a single publishing field Returns [PostJob](attica-postjob.md)\*

### Attica::ListJob\<Attica::Content\> \*Provider::searchContents(const Category::List &*categories*, const QString &*search* = QString(), Attica::Provider::SortMode *mode* = Rating, uint *page* = 0, uint *pageSize* = 10) {#searchContents}

Request a list of Contents.

Note that `categories` is not optional. If left empty, no results will be returned.

An empty search string `search` returns the top n items.

`categories` categories to search in

`search` optional search string (in name/description of the content)

`mode` sorting mode

`page` request nth page in the list of results

`pageSize` requested size of pages when calculating the list of results

Returns list job for the search results

### Attica::ListJob\<Attica::Content\> \*Provider::searchContents(const Category::List &*categories*, const QString &*person*, const Distribution::List &*distributions*, const License::List &*licenses*, const QString &*search* = QString(), Attica::Provider::SortMode *sortMode* = Rating, uint *page* = 0, uint *pageSize* = 10) {#searchContents-1}

Request a list of Contents. More complete version.

Note that `categories` is not optional. If left empty, no results will be returned.

An empty search string `search` returns the top n items.

`categories` categories to search in

`person` the person-id that created the contents

`distributions` list of distributions to filter by, if empty no filtering by distribution is done

`licenses` list of licenses to filter by, if empty no filtering by license is done

`search` optional search string (in name/description of the content)

`mode` sorting mode

`page` request nth page in the list of results

`pageSize` requested size of pages when calculating the list of results

Returns list job for the search results

### Attica::ListJob\<Attica::Content\> \*Provider::searchContentsByPerson(const Category::List &*categories*, const QString &*person*, const QString &*search* = QString(), Attica::Provider::SortMode *mode* = Rating, uint *page* = 0, uint *pageSize* = 10) {#searchContentsByPerson}

Request a list of Contents.

Like [searchContents](attica-provider.md#searchContents), but only contents created by one person.

`person` the person-id that created the contents.

### Attica::ListJob\<Attica::KnowledgeBaseEntry\> \*Provider::searchKnowledgeBase(const Attica::Content &*content*, const QString &*search*, *Attica::Provider::SortMode*, int *page*, int *pageSize*) {#searchKnowledgeBase}

### Attica::PostJob \*Provider::setAchievementProgress(const QString &*id*, const QVariant &*progress*, const QDateTime &*timestamp*) {#setAchievementProgress}

### void Provider::setAdditionalAgentInformation(const QString &*additionalInformation*) {#setAdditionalAgentInformation}

Set a custom identifier for your application (sent along with the requests as the http agent header in addition to the application name and version).

For example, you might have an application named SomeApplication, version 23, and wish to send along the data "lookandfeel.knsrc". Call this function, and the resulting agent header would be:

SomeApplication/23 (+lookandfeel.knsrc)

If you do not set this (or set it to an empty string), the agent string becomes

SomeApplication/23

`additionalAgentInformation` The extra string

*See also* [additionalAgentInformation](attica-provider.md#additionalAgentInformation)()

### Attica::PostJob \*Provider::setDownloadFile(const QString &*contentId*, const QString &*fileName*, QIODevice \**payload*) {#setDownloadFile}

### Attica::PostJob \*Provider::setDownloadFile(const QString &*contentId*, const QString &*fileName*, const QByteArray &*payload*) {#setDownloadFile-1}

### void Provider::setEnabled(bool *enabled*) {#setEnabled}

*See also* [isEnabled](attica-provider.md#isEnabled)()

### Attica::PostJob \*Provider::setPreviewImage(const QString &*contentId*, const QString &*previewId*, const QString &*fileName*, const QByteArray &*image*) {#setPreviewImage}

Upload an image file as preview for the content

`contentId`

`previewId` each content can have previews with the id 1,2 or 3

`payload` the image file

### Attica::PostJob \*Provider::setPrivateData(const QString &*app*, const QString &*key*, const QString &*value*) {#setPrivateData}

Sets the value of an attribute.

`app` The application name

`key` The key of the attribute

`value` The new value of the attribute

Returns The job responsible for setting data

### Attica::PostJob \*Provider::uploadTarballToBuildService(const QString &*projectId*, const QString &*fileName*, const QByteArray &*payload*) {#uploadTarballToBuildService}

Upload a tarball to the buildservice.

`projectId` The ID of the project this source file belongs to

`payload` A reference to the complete file data

Returns A postjob to keep keep track of the upload

### Attica::PostJob \*Provider::voteForComment(const QString &*id*, uint *rating*) {#voteForComment}

Vote a comment item

`id` the comment id which this voting is for

`rating` the rating, must be between 0 (bad) and 100 (good)

Returns the post job for this voting

### Attica::PostJob \*Provider::voteForContent(const QString &*contentId*, uint *rating*) {#voteForContent}

Vote for a content item

`contentId` the content which this voting is for

`rating` - the rating, must be between 0 (bad) and 100 (good)

Returns the post job for this voting
