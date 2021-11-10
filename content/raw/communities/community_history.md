---
title: "Community History"
description: "test"
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "communities"
weight: 100
toc: true
---

_Author: Pascal Precht <<pascal@status.im>>_

### Objective
This document outlines the support for preserving community related history data in Status Desktop. The feature will go through a various iterations. This spec focuses on the first to create an an MVP that matches the needs under certain assumptions.

### The Community History Problem
Due to Status decentralized nature and the way it has been designed, there are various cases where users run into unexpected behaviour when it comes to message data retrieval in Community channels. There have been various discussions and research about this problem and it's recommended to read these to get a full understanding of the problem space. A great starting point is the [Feasibility Discussion](https://github.com/vacp2p/rfc/issues/420).

The problem can be broken down into smaller problem areas. For a full break-down write up have a look at the [Community history problem break-down](https://github.com/vacp2p/research/issues/82). Beyond that, there are problems that need to be solved, which are outside of the scope of this specification that focuses on the MVP.

Further information on those problems can be found in these documents:

- [Waku V2 Usage for Community History](https://github.com/vacp2p/research/issues/83)
- [Capturing messages order and dependency](https://github.com/vacp2p/research/issues/76)
- [Access Control Management](https://github.com/vacp2p/research/issues/79)
- [Store synchronization/consensus in Waku V2 store protocol](https://github.com/vacp2p/research/issues/80)
- [Offline/long-term storage](https://github.com/vacp2p/research/issues/81)
- [Resource throttling](https://github.com/vacp2p/research/issues/84)
- [Edit/remove messages](https://github.com/vacp2p/research/issues/77)


#### A TLDR; problem description (MVP)
A quick summary of the problem space of the MVP:

1. **Message Ordering** - Messages are ordered using sender generated timestamp + message hash. Assumes nodes have synchronized clocks and max. +- 20 seconds asynchrony. This is covered by [WAKU2-FTSTORE](https://rfc.vac.dev/spec/21/).
2. **State synchronization/consensus** - Store nodes listen to network and store all communities messages. At least one node has to be online at any given time. Nodes can recover message gaps by performing time-based queries to other nodes. This is covered by [WAKU2-FTSTORE](https://rfc.vac.dev/spec/21/)
3. **Discovery** - Static and provided by community owner.
4. **Transport** - Waku2 (Gossipsub)
5. **Offline/long-term storage** - Nodes should have enough storage to maintain entire history.

<img style="max-width: 100%" src="https://camo.githubusercontent.com/acd1d1f15ca077f4a9386611800b65c8b4b44b5ac623e00c4ac6e8e0dc722f24/68747470733a2f2f692e696d6775722e636f6d2f6d364b71704b762e6a7067">

### Use cases

These are some rough notes that need to be turned into cockburn style notes:

- As a user I want to be able to read messages of community channels prior to my membership
- As a user I want to be able to read messages older than 30 days

...

### Functional requirements

#### General

- The community owner MUST run store nodes
  - Store nodes MUST implement [WAKU2-STORE](https://rfc.vac.dev/spec/13/) and [WAKU2-FTSTORE](https://rfc.vac.dev/spec/21/)
  - Store nodes MUST be configured with a static list of all store nodes
  - Store nodes MUST have a synchronized clock with at most +- 20 seconds difference
  - Store nodes MUST be participants of Gossipsub

#### Creating communities

- The community owner MUST specify a list of trusted store nodes and their addresses
- The store node list MUST be public to community members
- The Status client MUST add community store nodes to its known store node cluster

#### Editing communities
- The community owner MAY change the list of store nodes for the community
  - The Status client MUST update its known store nodes
  - The Status client MUST fetch history data when known store nodes were changed
- The community owner MAY remove the list of store nodes from the community
  - The Status client MUST remove the known store nodes from its cluster

### Designs

TODO

### Additional notes
