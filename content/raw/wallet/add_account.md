---
title: "Add Account spec"
description: ""
date: 2020-12-08T08:48:57+00:00
lastmod: 2020-12-08T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "wallet"
weight: 100
toc: true
---

# Add Account Spec

## Motivation

Users often want to add an account to their wallet and this is a very common use case. These accounts can either be generated, or imported. In some cases Users also want to add addresses just to watch them.

## Definitions

- ethereum address - hexadecimal string of 64 characters used to identify an account
- private key - hexadecimal string of 64 characters that is used to sign transactions belonging to the account
- seed phrase - a list of 12 words used to generate one or more private keys
- derivation path - a list of integers used to derive a private key from a seed phrase 
- ENS - a ethereum domain name that is used to resolve an address
- assets - refers to Ethereum Tokens and ERC-20 Tokens
- active account - an ethereum address that has transactions

## Designs

- [designs](https://www.figma.com/file/FkFClTCYKf83RJWoifWgoX/Wallet-v2?node-id=49%3A1737962)

## Use Cases

### Generate an account

**TODO** design is missing

1. User selects "Generate an account"
2. System shows dialog to enter account name and emoji
3. System randomly selects an emoji
4. User fills in account name
5. (optional): User selects emoji
6. User selects "Add account"

### Import an account from a private key

1. User selects "Add with a key or seed phrase"
2. System shows dialog to enter a private key or seed phrase, name and emoji
3. System randomly selects an emoji
4. User enters private key
4.1 alternative: user fills seed phrase, see "Import an account from a seed phrase"
5. Systems validates private key
6. User fills name
7. (optional) User selects emoji
8. User selects "Add account"

### Import an account from a seed phrase

1. User selects "Add with a key or seed phrase"
2. System shows dialog to enter a private key or seed phrase, name and emoji
3. System randomly selects an emoji
4. User enters seed phrase
5.1 alternative: user fills private key, see "Import an account from a private key"
5. System searches for "active accounts"
6. System displays list of known active accounts
6.1 alternative: System displays "We found no active accounts with that seed phrase"
6.1.1 System offers option to generate an account, see "Generate an account
6.1.1 System offers option to proceed with seed phrase, see "Import an account from a seed phrase: no active accounts found or new derivation path"
7. (optional) User deletes one or more "active account"
8. User fills names of active accounts
9. (optional) User changes emoji of an active account
10 User selects "Add accounts"
10.1 alternative: user selects: "Add new derivation path", see "Import an account from a seed phrase: no active accounts found or new derivation path"

#### Import an account from a seed phrase: no active accounts found or new derivation path

1. System displays a list of derivation paths
2. User selects one of the derivation paths
2.1 alternative: User types derivation path
3. **TODO** design is missing next steps

## Functional Requirements

**general**
- A user MUST be able to generate a new account
- A user MUST be able to import an account from a private key
- A user MUST be able to import an account from a seed phrase
- A user MUST be able to add a watch only address to their wallet

- An account MUST have a name associated to it
- An account name MUST be composed of alphanumeric characters, underscores, and/or hyphens
- An account name MUST be at least 3 characters long
- An account name MUST be at at most 20 characters long
- An account MUST have an emoji associated to it
- A account emoji default MAY be randomly selected

**private keys**
- An imported private key MUST be 64 characters long
- An imported private key MUST be composed of hexadecimal characters
- An imported private key MAY start with 0x

**seed phrases**
- A seed phrase MUST be composed of 12 or 15 or 18 or 21 or 24 words
- A seed phrase MUST be composed of words present in the BIP39 english word list

- The following derivation paths MUST be supported:
   - Ethereum
   - Ethereum Classic
   - Ropsten Testnet
   - Ledger

- an "active account" MUST display the name of the derivation path, the address
- an "active account" MUST have the same properties as an account such as name and, emoji
- an "active account" emoji default MAY be randomly selected
- A user MAY delete an "active account"

## Notes

- This spec is about only the process of adding an account to a wallet. It does not cover the what each account should display.
- https://github.com/bitcoin/bips/blob/master/bip-0039/bip-0039-wordlists.md
