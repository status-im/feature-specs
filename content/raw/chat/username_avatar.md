---
title: "Username & profile spec"
description: ""
date: 2020-12-06T08:48:57+00:00
lastmod: 2020-12-06T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "chat"
weight: 100
toc: true
---

# Username & Profile Spec

## Motivation

Users need a mechanism to identity themselves to other users that is easy to use and at the same time somewhat resistant to impersonation attacks. At the time of writing Status uses deterministic 3 word usernames and ENS usernames. Unfortunately 3 word usernames have shown to be quite confusing for new users as they are used to set their own usernames in any chat app.
Here we introduce support for users to set their own display name and introduce at least 3 mechanics to minimize the risk of impersonation attacks. The first mechanism is the use of deterministic sequence of emojis to uniquely identity a profile. The second mechanism is the use of a deterministic sequence of colors around the profile image to differentiate it from other profiles which effectively replaces the 3 word usernames and identicons with a similar deterministic identifier. The third mechanism involves preventing duplicate display names from joining the same community. There is also an identity verification mechanism that is used to ensure that the user is who they say they are described in the Identity Verification Spec.

## Definitions

- 3 word usernames - A 3 word username is a deterministic sequence of words that uniquely identifies a profile. see [spec](https://specs.status.im/spec/2#3-word-pseudonym--whisperwaku-key-fingerprint)
- display name - A username choosen by the user to be displayed in the chat.
- local nickname - An alias for a profile choosen by the User. Only visible to the user.
- verified identity - A profile that went through the Identity Verification process. See [Identity Verification Spec](https://github.com/status-im/feature-specs/blob/98bedea29b871783e4f75dd2b99d9ff205748ed2/content/raw/chat/identity_verification.md).
- profile emblem - an icon next to a profile that is used to qualify that profile.
- emoji hash -  A deterministic sequence of emojis that uniquely identifies a profile.
- identicon ring - A deterministic sequence of colors around a profile avar that is used to differentiate it from other profiles.

## Designs

- [designs](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=1837%3A335126)
- [identicon ring](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=1837%3A335130)

## Use Cases

### Setting up a profile

Prerequisites: User is in onboarding process or has already set up a profile and has chosen to rename her username. Existing users that update their client to a version that support this spec must also setup their display name before being able to use the app

1. User fills their intended display name
2. User presses Save or Next
3. System saves the new display name
3.1 alternative: System warns user that the display name is invalid

### Joining a community

1. User selects a community to join
2. System detects that another user with the same display name has already joined that community
3. System warns user that the display name is already taken in that community
4. System displays conflicting profiles display name, avatar, identicon ring, emoji hash and chat key
5. User selects "Change Your display name"
6. User fills in a new display name
7. Systems adds user to the community
7.1 alternative: System warns user that the display name is invalid

## Functional Requirements

**Profile Emblems**

- If a profile is a mutual contact then it MUST display a mutual contact emblem (e.g a profile icon)
- If a profile is a verified identity then it MUST display a verified emblem (e.g a tick icon)
- If a profile is marked as untrusthworthy then it MUST display a untrustworthy emblem (e.g a exclamation mark icon)
- If a profile is a mutual contact then it MAY display another emblem
- If a profile is not a mutual contact then it MUST NOT display other emblems

**Profile usernames**

- Users MUST be able to set a display name for their own profile
- Display names MUST be at least 5 characters long
- Display names MUST be composed of alphanumeric characters, underscores, spaces and/or hyphens, but they cannot contain spaces at the beggining or end
- Display names MUST NOT be longer than 24 characters
- Display names MUST NOT be "3 word names"
- Display names MUST NOT end in "_eth" or ".eth" or "-eth"
- Profiles containing 3 word names as their display name that does not deterministically correspond to their chatkey MUST display a warning icon to indicate that the username is not deterministic
- A user MUST be able to set a local nickname for any profile other than their own
- A local nickname MUST be visible only to the user who set it
- If profile has a local set username set then it MUST show the original display name (e.g if the local nickname is 'intimidating guy' and the original display name is 'Jotaro' then show `intimidating guy (Jotaro)`)
- If a profile has a registered ENS username, then it MUST end in .eth
- If a profile has a registered ENS stateofus.eth username, then it MUST end in stateofus.eth
- If a profile has a registered ENS username, then it MAY NOT display the chat key next to the username
- If a profile does not have a registered ENS username, then it MUST display the chat key next to the username

**Profile avatar**

- If a profile does not have a profile photo set it MUST use a 2 letter avatar
- A 2 letter avatar MUST be the first two letters of the display name

- Users MUST be able to set a profile photo for their profile
- Profile photos MUST be visible to all users

- Unless a profile has a registered ENS username, it MUST show the identicon ring around the profile avatar
- A identicon ring MUST be composed of no more than 11 color segments
- A identicon ring segment MAY be one of 32 distinctive colors
- A identicon ring segment MAY be of different lengths and MUST be composed of 1 to 5 units (unit represents physical entity with color assigned, e.g. pixel)
- A identicon ring MAY contain non-consecutive same color segments

**EmojiHash**

- An Emoji Hash MUST be a sequence of 14 emojis determined by the profile's chat key. See [2/ACCOUNT spec](https://github.com/status-im/specs/blob/17ab4b313c55bc7c4ad672e0d06c6cb02fba00a7/docs/spec/2-account.md#emoji-hash) for details
- An Emoji Hash MUST be composed of [immutable emoji set](https://github.com/status-im/status-go/blob/develop/static/emojis.txt)
- A profile detailed view MUST show that profiles emoji hash

**Profile actions**

- If a profile is not a contact AND is not marked then
    - The user MUST be able to mark that profile as untrustworthy
    - The user MUST be able to block that profile
- If a profile is not a contact AND is marked as untrusthworthy then
    - The user MUST be able to remove the untrustworthy mark
    - The user MUST be able to block that profile
- if a profile is a contact AND is not marked then
    - The user MUST be able to remove the untrustworthy mark
    - The user MUST NOT be able to block or unblock that profile
- if a profile is a contact AND is marked as untrusthworthy then
    - The user MUST be able to remove the untrustworthy mark
    - The user MUST NOT be able to block or unblock that profile
- if a profile is a contact AND has the identity verified then
    - The user MUST NOT be able to mark that profile as untrustworthy or trusthworthy
    - The user MUST NOT be able to block or unblock that profile

**Usernames in Communities**

- A community MUST prevent duplicate display names

**Messages**
- If a message is received from an account that does not have a display name, the three word alias must be displayed. (This can happen if the author of the message has not updated their Status client)

## Notes

- This spec implies that identicons & 3 word usernames features are to be removed from the app, they are still supported for backwards compatibility
- see emojihash for an example https://github.com/0kok0/emojihash
