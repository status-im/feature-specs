---
title: "Token store"
description: ""
version: "1.0.0"
date: 2022-05-19T12:03:57+00:00
lastmod: 2022-05-18T12:03:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "wallet"
weight: 100
toc: true
---

# Token store Spec

## Motivation

This specs defines how the token store should be managed in Status applications for mainnet and test

## Definitions

### Token

A token either implement the ERC20 specs or is native in the network.

For example:
* SNT is implementing the ERC20 specs
* ETH is the native chain token of Ethereum mainnet

## Functional Requirements

### Token Identifier

The way to identify a token is via the Symbol

Example:
    * SNT and DAI are 2 differents token

### Token balance

The balance of a token MUST be the sum of all enabled chain balance for the specific token
Example:
    * Account A have 10 SNT on mainnet and 10 SNT on arbitrum, the balance of this token will then be 20

Native token and ERC20 are not different

### Testnet Token

Testnet token are not different in behaviour than mainnet token.
The name of a token in mainnet MUST be named the same way in testnet

Example:
    * SNT MUST be named SNT on all chain, test or not.
    * ETH MUST be named ETH on all chain, test or not.