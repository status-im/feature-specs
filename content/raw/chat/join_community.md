---
title: "Community & Channels membership spec"
description: ""
date: 2022-08-16T08:48:57+00:00
lastmod: 2022-08-16T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "chat"
weight: 100
toc: true
---

# Join Community

## Motivation

## Definitions


## Designs

- [Join Community Workflow](https://www.figma.com/file/17fc13UBFvInrLgNUKJJg5/Kuba%E2%8E%9CDesktop?node-id=2312%3A298851)

## Use Cases


## Functional Requirements

### Community Types

- A community MAY require a token to enter
- A community MAY require a manual membership approval

### Community no token is required, no membership approval needed

- A user MAY view channels and messages
- A user CANNOT send messages without joining the community
- A user MAY join the community

**welcome message**
- If a user joins a community a welcome message MUST be displayed
- A user MUST agree with the welcome message to join the community
- The submit button MUST BE labelled "Join [community name]"
- A user MUST appear in the member list after joining the community

### Community no token is required, membership approval is required

- A user MAY view channels and messages
- A user CANNOT send messages without joining the community
- A user MAY request to join the community

**welcome message**
- If a user joins a community a welcome message MUST be displayed
- A user MUST agree with the welcome message to join the community
- The submit button MUST BE labelled "Request to join [community name]"

**membership request**
- If a user requested to join a community the state "Membership Request Pending.." MUST BE displayed
- If a user requested to join a commmunity in ephemeral notication MUST BE displayed with the text "Your Request has been submitted"
- If a user has a membership request pending then they MAY cancel the request

**membership approved**
- A user that made a request to join MUST be approved by a community admin to join the community
- A user MUST appear in the member list after being approved to join the community
- If a membership request is approved it MUST display an ephermal notification with the text "[community name] membership approved"
- If a membership request is approved it MUST be displayed in the activity center

**membership rejected**
- If a membership request is rejected it MUST display an ephermal notification with the text "[community name] membership rejected"
- If a membership request is rejected it MUST be displayed in the activity center
- If a user request to join a community is rejected then the state "Membership Request Rejected" MUST BE displayed

### Community token is required, no membership approval is required

- A user CANNOT view channels and messages without joining the community
- A user CANNOT send messages without joining the community
- A user MAY join the community

**joining requirements**
- The requirements to join the community MUST be displayed
- A user MAY reveal their address to join

**welcome message**
- The welcome message MUST be displayed only if the user meets the requirements to join
- A user MUST agree with the welcome message to join the community
- The submit button MUST BE labelled "Join [community name]"

**membership**
- A user MUST appear in the member list after joining the community

### Community token is required, membership approval is required

- A user CANNOT view channels and messages without joining the community
- A user CANNOT send messages without joining the community
- A user MAY request to join the community

**joining requirements**
- The requirements to join the community MUST be displayed
- A user MAY reveal their address to join

**welcome message**
- If a user requests to join the community a welcome message MUST be displayed
- A user MUST agree with the welcome message to request to join the community
- The submit button MUST BE labelled "Request to join [community name]"

**membership request**
- If a user requested to join a community the state "Membership Request Pending.." MUST BE displayed
- If a user requested to join a commmunity in ephemeral notication MUST BE displayed with the text "Your Request has been submitted"
- If a user has a membership request pending then they MAY cancel the request

**membership approved**
- A user that made a request to join MUST be approved by a community admin to join the community
- A user MUST appear in the member list after being approved to join the community
- If a membership request is approved it MUST display an ephermal notification with the text "[community name] membership approved"
- If a membership request is approved it MUST be displayed in the activity center

**membership rejected**
- If a membership request is rejected it MUST display an ephermal notification with the text "[community name] membership rejected"
- If a membership request is rejected it MUST be displayed in the activity center
- If a user request to join a community is rejected then the state "Membership Request Rejected" MUST BE displayed

### Restricted Channels

- A channel MAY have requirements to send messages
- A channel MAY have requirements to view messages
- If a user does not meet the a channel requirements, the requirements MUST BE displayed
- A user MAY reveal their address to join a restricted channel
- If a channel has requirements for viewing messages a user MUST meet those requirements to view messages
- If a channel has requirements for sending messages a user MUST meet those requirements to send messages

## Notes

