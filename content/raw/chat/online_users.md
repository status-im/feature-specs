---
title: "Online Users spec"
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

# Online Users

## Designs

* [member section](https://www.figma.com/file/Mr3rqxxgKJ2zMQ06UAKiWL/%F0%9F%92%AC-Chat%E2%8E%9CDesktop?node-id=2431%3A28468)

## Use Cases

TODO

## Functional Rrequirements

Users can see in a community channel who is online and who is offline. Users can opt-in or opt-out to transmit their online/offline state to other community users.

preconditions:

- The user must be in a community channel

**Member List**

- The member list sidebar SHALL be titled 'members'
- The member list MUST be grouped by 'online' & 'offline' users
- The users in this member list that are online MUST have the green circle
- The users that are offline MUST be slightly faded out
- Within each online/offline section, users MUST be sorted by
    - 1. Users with ENS name
    - 2. Alphabetical
- The member list SHOULD be toggled on by default

**Status Selector**

- The user MUST be able to select his state as 'online' or 'offline'
- If the user has 'online' as selected, then they MUST be shown online in the communities member list.
- If the user has 'offline' as selected, then they MUST be shown offline for everyone within 5 minutes regardless of activity, even if the user sends new messages.

## Notes

- under the hood: a user that has the online state sends a ping to a special community channel, if the user selects offline state, then they stop sending this ping, and it's assumed by other clients the user went offline if they don't receive another ping within 5 minutes.
