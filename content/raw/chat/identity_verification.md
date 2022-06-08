---
title: "identity verification spec"
description: ""
date: 2020-11-03T08:48:57+00:00
lastmod: 2020-11-03T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "chat"
weight: 100
toc: true
---

# Identity Verification

## Motivation

Users need a mechanism to verify a contact identity due to impersonation risks. For example someone can set their profile picture and username to be the same as a an individual the user knows. Here we describe one of the mechanisms used to deal with this which involve asking for verification of the identity of the user with a challenge question.

## Designs

- [sending identity verification request](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=670%3A339162)
- [responding to an identity verification request](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=1543%3A341560)

## Use Cases

### Ask to verify identity

prequisite: user has been added as a contact.

1. User selects a contact
2. User prompts to verify identity
3. Users writes a challenge question or request (for e.g something only the real person would know, or some action that only that person would be able to perform)
4. User sends the request to the contact, and waits for a response
5. System notifies the identity verification has received a response (e.g see Activity Center Spec)
6. User selects the identity verification notification item
7. User verifies the response and selects "Confirm Identity"
7.1 alternative: User selects "Mark untrustworthy"
8. System confirms to user that the identity has been verified

### Respond to identity verification request

1. System notifies user of an identity verification request
2. User selects the identity verification notification item
3. System displays contact that is sending request, the verification question & prompts user to respond to the verification question
4. User fills in the verification question and selects "Send Answer"
4.1 alternative: User selects "Refuse Verification"
5. System notifies user that the answer has been sent

### Remove identity verification

prequisite: contact identity has already been verified

1. User selects a contact
2. User selects "Remove Identity Verified status"
3. System asks confirmation
4. User confirms

## Functional Requirements

**general:**

- Any profile MAY BE marked as untrustworthy
- A profile marked as untrustworthy MAY HAVE the untrustworthy mark removed
- A user MUST confirm the removal of an identity verification status
- A profile added as a contact and marked as trusthworthy CANNOT be blocked

**sending identity verification requests:**

- A user MUST only be able to send an identity verification request to a mutual contact
- The challenge question MUST BE at least 1 character
- The challenge question MUST BE at most 280 characters
- The challenge question MUST BE composed of only printable ascii characters
- A user MUST BE able to cancel an ongoing identity verification request
- A user CANNOT confirm identity of an identity verification request that has not received a response

**receive identity verification requests:**

- For a user to receive an identity verification request it MUST BE a mutual contact
- Identity verification requests MUST display the sending user, date, and the challenge question
- The user MUST BE able to reply to an identity verification request
- The reply to challenge question MUST BE at least 1 character
- The reply to challenge question MUST BE at most 280 characters
- The reply to challenge question MUST BE composed of only printable ascii characters
- The user MUST BE able to refuse verification of an identity verification request
- The user MUST BE able to change the answer to a challenge question

## Notes
