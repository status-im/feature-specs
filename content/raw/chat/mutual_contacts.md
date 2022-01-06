---
title: "Mutual Contact Requests spec"
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

# Mutual Contact Requests

## Motivation

To prevent unsolicited messages & invitations and some forms of spam, Users must explicity add each other as contacts.

## Designs

* [designs](https://www.figma.com/file/Mr3rqxxgKJ2zMQ06UAKiWL/%F0%9F%92%AC-Chat%E2%8E%9CDesktop?node-id=5224%3A0)
* [Sending contact request](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=725%3A329626)
* [Receiving contact request](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=1637%3A369041)
* [Pending contact request](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=128%3A28247)
* [notifications](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=2090%3A252386)

## Use Cases

### Sending a Contact Request

1. User selects a profile and asks application sends contact request
2. User fills reason for contact request e.g "Say who you are / why you want to become a contact.."
3. User sends contact request
4. System notifies user `Contact Request Send`
4.1 alternative: System notifies user `Contact Request Rejected`
5. System opens A 1 on 1 chat with that user, it displays that a contact request to that user is pending. The user cannot send messages on the 1 on 1 while the request is pending.

### Receiving Contact Request

1. System notifies user of a contact request (note: see activity center spec)
2. User checks pending contact requests
3. system displays the username of the requester, time of request, and the motivation text for the request
4. User accepts contact request
4.1 alternative: User rejects contact request
5. system makes contact request as accepted or rejected

## Functional Requirements

User A wants to chat with User B and so adds User B as a contact, User B receives a contact request with a message and can either accept or reject. User A can only chat with User B if User B accepts the contact request.

### User A that sends contact request
- User A CANNOT send messages to User B if User B has not accepted the contact request
- User A MAY send a contact request to User B containing a message
- The message for the contact request MUST NOT exceeed 280 characters
- If User A has sent a contact request they MUST see that the contact request is pending and the message they have sent
- If User A has sent a contact request they MUST be able to cancel the contact request
- if User A has sent a contact request and it was rejected then the user MUST not be able to send another contact request

### User B that receives contact request
- A User CANNOT receive messages from users that are not in their contact list
- A User MAY receive contact requests from users that are not in their contact list
- A User CANNOT receive contact requests from users that are already in their contact list
- A User CANNOT receive contact requests from users that were already rejected
- A User MUST be able to see a list of contact requests previously rejected
- A User MAY accept a contact request that was previously rejected
- If a User has pending contact requests the contact requests section MUST be displayed
- If a User has no pending contact requests the contact requests section MUST NOT be displayed
- If a User receives a contact request the counter of message requests MUST increase

### Contact Requests Section

- A pending contact request MUST display the username, date, and message of the request
- A User MAY Decline ALL pending contact requests
- A User MAY Accept ALL pending contact requests
- The user MUST be able to accept a contact request directly
- The user MUST be able to decline & block a contact request directly in this type of activity item
- Clicking the context menu of a contact request item MUST show 2 options: "view profile" and "Decline and Block"
- If a contact request item is rejected it MUST disapear from the UI
- If a contact request item is accepted it MUST disapear from the UI
- Clicking on this type of activity item MUST open that chat and jump to that message
- Contact Requests MUST appear in the activity center and in the contact area of the settings

## Notes

* In the desktop app the "Contact Requests section" is a section in the Activity Center. There is currently a dedicated contact request section that will be removed.
