---
title: "Send Transaction spec"
description: ""
version: "2.0.0"
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

# Send Transaction Spec

## Motivation

One of the most common use cases for a wallet is to send tokens to another account. A user typically expects to know how much tokens they are sending are worth in some currency and also expect a wide range of functionality such as ENS addresses, address validation using EIP-55, and the ability to choose easily common addresses, saved or recently used address to send to. The user also expects to be able to understand the transactions fees involved and choose the priority for transaction.

## Definitions

## Designs

- [send](https://www.figma.com/file/FkFClTCYKf83RJWoifWgoX/Wallet-v2?node-id=350%3A83031)
- [swap](https://www.figma.com/file/FkFClTCYKf83RJWoifWgoX/Wallet-v2?node-id=350%3A92081)
- [swap & send](https://www.figma.com/file/FkFClTCYKf83RJWoifWgoX/Wallet-v2?node-id=29%3A12317)

## Use Cases

### Send Token

prerequesites: User is in the wallet with an account selected

1. User selects send
2. User selects a token
3. User fills an amount
4. System updates fiat field to reflect token amount in fiat
5. User pastes an ethereum address in the to field
6.1 alternative: user types an ens address in the to field
6.2 alternative: user selects an address in the saved section
6.3 alternative: user selects an address in the my accounts section
6.4 alternative: user selects an address in the recent section
6. System validates address
7. System displays Priority section with "Optimal" pre selected
8. (optional) User selects a priority
9. System validates if origin account has enough to pay for gas
10. User presses Send
11. System notifies user transaction is ongoing
12. System notifies user when transaction is complete

## Functional Requirements

### general

- The Send Transaction functionality MUST support the following use cases "Swap", "Swap & Send", "Send"

### Send

**Asset & Amount**
- The Assets & Amount section MUST display two fields, the token selector and the fiat selector
- The token selector MUST have a token selected by default (e.g USDC)
- The fiat selector MUST have a fiat currency selected by default, the default fiat currency MUST be the users prefered fiat currency.
- The total balance across networks for the selected token MUST be displayed
- Changing the selected token MUST update the displayed total balance
- The fiat selector MUST be greyed out unless selected
- Inputing or changing a token amount in the token field MUST change the amount in the fiat field to reflect the amount
- Inputing or changing a fiat amount in the fiat field MUST change the amount in the token field to reflect the amount
- The token selector MUST display the tokens enabled for that account
- Each token in the token selector MUST display the token logo, name, balance, and the balance in the prefered fiat currency
- The tokens in the token selector MUST be ordered by their fiat value
- The user MUST be able search for a token by name or symbol in the token selector
- The user MAY input a token address in the token selector to use that token

**To**
- The To section MUST have the following options: an address field, saved addresses section, my accounts section, recent section
- The address field MUST support ethereum addresses OR ENS names
- The address field MUST validate ethereum addreses
- The address field MUST validate ethereum addreses using [EIP-55](https://eips.ethereum.org/EIPS/eip-55)
- The address field MUST validate ENS names
- The addresses in the saved addresses section MUST be sorted by favourite state, then by how long ago it was used
- The addresses in the saved addresses section MUST display: emoji, display name, how long ago it was used, ethereum address
- The addresses in the my accounts section MUST be sorted by display name
- The addresses in the my accounts section MUST display: emoji, display name, ethereum address, balance in prefered fiat currency 
- The addresses in the my accounts section MUST display the balance in the preference fiat currency only if that balance is more than 0
- The addresses in the recent section MUST be sorted by date of how long ago it was used
- The addresses in the recent section MUST display the account emoji, display name, how long ago it was used, ethereum address, and balance transfered of the last transaction
- If an address in the recent section is not in the saved addresses or my accounts section, then it MUST display a default emoji, and display the ethereum address instead of the display name

**Priority & Gas**
- After selecting a destination address the user MUST be able to choose a priority for the transaction
- The priorities supported MUST be: low, optimal, high, custom
- If the origin address does not have enough ether to pay for the choosen amount of gas an error MUST be shown

### Swap

**Asset & Amount**
- The Assets & Amount section MUST display two fields, the origin token selector and destination token selector
- Each token selector MUST have a token selected by default (e.g USDC)
- The total balance across networks for the selected token in the origin token selector MUST be displayed
- Changing the selected origin token MUST update the displayed total balance
- Inputing or changing a token amount in the origin token field MUST change the amount in the destination token field to reflect the amount
- Inputing or changing a token amount in the destination token field MUST change the amount in the origin token field to reflect the amount
- A user MUST be able to reverse the origin and destination token selectors
- The fiat amount equivalent to the amount in the destination token field MUST be displayed
- The token selector MUST display the tokens enabled for that account
- Each token in the token selector MUST display the token logo, name, balance, and the balance in the prefered fiat currency
- The tokens in the token selector MUST be ordered by their fiat value
- The user MUST be able search for a token by name or symbol in the token selector
- The user MAY input a token address in the token selector to use that token

**Priority & Gas**
- After inputing values for the origin and destination tokens the user MUST be able to choose a priority for the transaction
- The priorities supported MUST be: low, optimal, high, custom
- If the origin address does not have enough ether to pay for the choosen amount of gas an error MUST be shown

### Swap & Send

**TODO**

## Notes

