---
title: "activity center spec"
description: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "chat"
weight: 100
toc: true
---

# Activity Center

## Designs

- [designs](https://www.figma.com/file/Mr3rqxxgKJ2zMQ06UAKiWL/%F0%9F%92%AC-Chat%E2%8E%9CDesktop?node-id=5358%3A5666)
- [updated designs](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=1466%3A343105)

## Use Cases

TODO

## Functional Requirements

### General

* The Activity Center MUST support filtering by 5 categories: "All", "Mentions", "Replies", "Contact Requests", "Identity Checks"
* The Activity Center MAY contain the following type of items:
    * contact request
    * mention in a community
    * mention in public chat
    * mention in a group
    * mentions in a 1:1
    * reply to a message from the user
    * identity check request
* Clicking the "Mark all as read" MUST mark all activity items read of the selected category
* The activity items MUST be grouped by day sections and sorted by most recent
* The day sections and their items MUST displayed according to the following criteria
    * The section with items from today MUST be displayed as "Today"
    * The section with items from yesterday MUST be displayed as "Yesterday"
    * The section with items from this year MUST be displayed in the format "Weekday, Day Month" section example: "Mon, 21 April"
    * The section with items from previous years MUST be displayed in the format "Day Month Year" section example: "Mon, 21 April 2020"
* Clicking the context menu MUST display the following options:
    * "Show read notifications", if selected before it MUST toogle to "Hide read notifications"
    * "Notification settings", if Click it MUST open the notifications settings in profile section

### Contact Requests

* If the user receives a contact request it MUST appear in the "All" and "Contact Requests" sections.
* The user MAY accept or reject a contact request in the activity center
* The user MUST be able to accept a contact request directly in this type of activity item
* The user MUST be able to decline & block a contact request directly in this type of activity item
* Clicking the context menu of this type of activity item MUST show 2 options: "view profile" and "Decline and Block"
* If a contact request item is rejected it MUST display "Declined"
* If a contact request item is accepted it MUST display "Accepted"
* Clicking on this type of activity item MUST open that chat and jump to that message

### Mentions

* If the user is mentioned the message containing the message MUST appear in the "All" and "Mentions" sections.
* The user MUST be able to mark this type of item as read
* Clicking the context menu of this type of activity item MUST show 2 options: "view profile" and "Decline and Block"

### Replies

* If the user receives a reply to a message they have posted then the reply MUST appear in the "All" and "Replies" sections.
* The user MUST be able to mark this type of item as read
* Clicking on this type of activity item MUST open that chat and jump to that message

## Notes

* At time of writing the "Identity Checks" section is new and has not been implemented yet
