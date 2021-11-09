---
title: "Notifications spec"
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

# Notifications

## Designs

TODO

## Use Cases

TODO

## Functional Requirements

TODO

to take into account:
- notification preferences: All Messages, just @mentions, Nothing
- type of chat: Group, 1 on 1, public chat, community channel
- type of notification: reply, mention, contact request
- to play or not a sound
- OS Notifications or custom ones
- Style of notifications: Anonymous, Name only, Name & Message
- chats that are muted or not
- users that are muted or not

## Notes

**Event:**
- **SM** - Simple Message - message without mentions
- **MM** - Mention Message
- **RM** - Reply Message - reply to the any of my messages
- **NR** - New Request

**Action:**
- **ADChI** - **A**dd **D**ot to **Ch**at Nav Bar **I**con - only if Chat Nav Bar is not active
- **ACChI** - **A**dd **C**ount to **Ch**at Nav Bar **I**con - only if Chat Nav Bar is not active _(contact request for this section are counted also in total count)_
- **AD1:1C** - **A**dd **D**ot to **1:1** **C**hat List Item - only if 1:1 Chat List Item is not active
- **AC1:1C** - **A**dd **C**ount to **1:1** **C**hat List Item - only if 1:1 Chat List Item is not active
- **ADPC** - **A**dd **D**ot to **P**ublic **C**hat List Item - only if Public Chat List Item is not active
- **ACPC** - **A**dd **C**ount to **P**ublic **C**hat List Item - only if Public Chat List Item is not active
- **ADGC** - **A**dd **D**ot to **G**roup **C**hat List Item - only if Group Chat List Item is not active
- **ACGC** - **A**dd **C**ount to **G**roup **C**hat List Item - only if Group Chat List Item is not active
- **ADCoI** - **A**dd **D**ot to **Co**mmunity Nav Bar **I**con - only if Community Nav Bar is not active
- **ACCoI** - **A**dd **C**ount to **Co**mmunity Nav Bar **I**con - only if Community Nav Bar is not active _(contact request for this community are counted also in total count)_
- **ADCC** - **A**dd **D**ot to **C**hannel **C**hat List Item - only if Channel List Item is not active
- **ACCC** - **A**dd **C**ount to **C**hannel **C**hat List Item - only if Channel List Item is not active
- **AIAC** - **A**dd **I**tem to **A**ctivity **C**enter
- **ACACI** - **A**dd **C**ount to **A**ctivity **C**enter **I**con
- **AOSPN** - **A**dd **O**perating **S**ystem **P**ush **N**otification

_The following table should determine whether and where we need to add notification **we imply that appropriate chat/channel is not active in the moment when any of above mentioned events is happening**_:
<table> 
<tr> 
<th colspan="3">Set Notification:</th> 
<th colspan="4">All messages</th> 
<th colspan="4">Just mentions</th> 
<th colspan="4">Nothing</th> 
<th colspan="4">New requests</th>  
</tr> 
<tr> 
<th colspan="3">&nbsp;</th> 
<th>SM</th><th>MM</th><th>RM</th><th>NR</th>  
<th>SM</th><th>MM</th><th>RM</th><th>NR</th>  
<th>SM</th><th>MM</th><th>RM</th><th>NR</th>  
<th>SM</th><th>MM</th><th>RM</th><th>NR</th>  
</tr>
<tr>
<th rowspan="6">Chat<br>Nav<br>Bar<br>Section</th>
<th rowspan="2">1:1 chat</th>
<th>unmuted</th>

<td>AD1:1C<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>AC1:1C<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>AD1:1C<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>AC1:1C<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>AD1:1C<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
</tr>
<tr>
<th>muted</th>
<td>/</td>
<td>AC1:1C<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>AD1:1C<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>AC1:1C<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>AD1:1C<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
</tr>
<th rowspan="2">group chat</th>
<th>unmuted</th>
<td>ADGC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACGC<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADGC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>ACGC<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADGC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td></tr>
<tr>
<th>muted</th>
<td>/</td>
<td>ACGC<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADGC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>ACGC<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADGC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
</tr>
<th rowspan="2">public chat</th>
<th>unmuted</th>
<td>ADPC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACPC<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADPC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>ACPC<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADPC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
</tr>
<tr>
<th>muted</th>
<td>/</td>
<td>ACPC<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADPC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>ACPC<br>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADPC<br>ADChI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACChI<br>AIAC<br>ACACI<br>AOSPN</td>
</tr>
<th rowspan="2">Community<br>Nav<br>Bar<br>Section</th>
<th rowspan="2">channel</th>
<th>unmuted</th>
<td>ADCC<br>ADCoI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACCC<br>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADCC<br>ADCoI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>ACCC<br>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADCC<br>ADCoI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>
</tr>
<tr>
<th>muted</th>
<td>/</td>
<td>ACCC<br>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADCC<br>ADCoI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>ACCC<br>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ADCC<br>ADCoI<br>AIAC<br>ACACI<br>AOSPN</td>
<td>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>

<td>/</td>
<td>/</td>
<td>/</td>
<td>ACCoI<br>AIAC<br>ACACI<br>AOSPN</td>
</tr>
</table>


**_And now an example how should we read the table:_**

```
IF (user has enabled "All messages" in his profile settings > notification panel AND
    "MM" mention message comes in "Chat Nav Bar Section" in "1:1 Chat" which is "unmuted")
THEN
    we need to take these actions:
    - AC1:1C - add dot to 1:1 chat list Item only if 1:1 chat list Item is not active
    - ACChI - add count to chat nav bar icon only if chat nav bar is not active (contact request for this section are counted also in total count)
    - AIAC - add Item to activity center
    - ACACI - add count to activity center icon
    - AOSPN - add operating system push notification
```
