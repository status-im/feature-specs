---
title: "Group Chat spec"
description: ""
date: 2022-06-09T08:48:57+00:00
lastmod: 2022-06-09T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "chat"
weight: 100
toc: true
---

# Group Chat

## Motivation

To have privacy preserved ad-hoc groups, where every added member is mutual contact of the inviter.

## Designs

* [Creating group and managing members](https://www.figma.com/file/17fc13UBFvInrLgNUKJJg5/Kuba%E2%8E%9CDesktop?node-id=1875%3A214228)
* [Editing group properties](https://www.figma.com/file/17fc13UBFvInrLgNUKJJg5/Kuba%E2%8E%9CDesktop?node-id=1875%3A214232)

## Use Cases

### Creating group
1. User starts chat
2. User selects more than one member from the Contacts list
  2.1. alternative: System notifies user "You can only send direct messages to your Contacts"
3. User confirms group creation
4. System opens created group chat

### Adding group members
1. User opens members list editor and trigger add member action
2. User selects members from the Contacts list
3. User confirms changes to members list
4. System notifies user through group chat system message "{{me}} has added {{members}}"

### Removing group members
1. User opens members list editor and trigger remove member action
2. User confirms changes to members list
4. System notifies user through group chat system message "{{me}} has removed {{members}}"

### Editing group name
1. User opens group properties editor
2. User edits group name
3. User confirms changes
4. System notifies user through group chat system message "{{me}} changed the group's name to {{name}}"

### Editing group image
1. User opens group properties editor
2. User selects new image from local storage
3. User crops the image
4. User confirms changes
5. System notifies user through group chat system message "{{me}} changed the group's image"

### Editing group color
1. User opens group properties editor
2. User selects new color from predefined colors
3. User confirms changes
4. System notifies user through group chat system message "{{me}} changed the group's color"

## Functional Requirements

Group creator creates the group where all Members are its mutual contacts. Group creator is the only Admin of the group.

### Group creator creates the group
- Group creator MUST add at least two Members
- All Members added by Group creator MUST be its mutual contacts
- Group creator MUST become the only Admin of the group
- Default name of the group MUST follow given pattern:
   - 3 Members: "{$AddedMember1Name}&{$AddedMember2Name}"
   - \>3 Members: "{$AddedMember1Name}, ..., {$AddedMemberNName}"

### Member adds another member
- All Members added by Member MUST be its mutual contact

### Admin removes another member
- Admin MUST be the only one who can remove members

### Member leaves the group
- Any Member MAY leave the group
- If Admin leaves the group, the group MUST stay intact

### Member sends message to the group
- Any Member in the group MUST see that message
- Any User removed from the group MUST NOT see that message

### Member changes the name of the group
- Group name MUST NOT be empty
- Group name MUST NOT be longer than 30 characters

### Member changes the image of the group
- Selected image MUST be one of JPG, PNG, TIFF, HEIF
- Selected image MUST NOT be larger than 450kb

## Notes

 * Link invitations (deprecated Mobile feature). This feature is going to be removed after breaking change adaptation period (3-6 months from now).
    * Admin MAY share group chat invitation link
    * Any Status User MAY request access to the group through the invitation link
    * Only Admin MAY approve or reject User's invitation request
