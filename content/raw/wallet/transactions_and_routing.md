---
title: "Transactions & Routing spec"
description: ""
version: "1.0.0"
date: 2022-05-10T12:03:57+00:00
lastmod: 2022-05-10T12:03:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "wallet"
weight: 100
toc: true
---

# Transactions & Routing Spec

This spec makes redundant the send transaction spec

## Motivation

One of the most common use cases for a wallet is to send tokens to another account. A user typically expects to know how much tokens they are sending are worth in some currency and also expect a wide range of functionality such as ENS addresses, address validation using EIP-55, and the ability to choose easily common addresses, saved or recently used address to send to. The user also expects to be able to understand the transactions fees involved and choose the priority for transaction. Finally, a user also expect transaction to work accross multi chain.

## Definitions

### Best route

We define the best route as the less costly route amongst all the route that can terminate in less than 5min

If there is no route that can terminate in less than 5min: update the time by 5min and apply same logic until a route is found

### Send

Send is the action of creating one or more transactions in order to send token from an account to another account

### Swap

Swap is the action of creating one or more transactions in order to swap token from another token to the same account

### Bridge

Bridge is the action of creating one or more transactions in order to bridge a token from one chain to another chain

## Designs

- [send](https://www.figma.com/file/FkFClTCYKf83RJWoifWgoX/Wallet-v2?node-id=2774%3A143138)
- [swap](https://www.figma.com/file/FkFClTCYKf83RJWoifWgoX/Wallet-v2?node-id=350%3A91908)
- [bridge](https://www.figma.com/file/FkFClTCYKf83RJWoifWgoX/Wallet-v2?node-id=2829%3A145815)

Requirement: it must be trivial to add/remove supported bridge, the routing algorithm must be abstracted from bridge X,Y or Z
## Use Cases

### Send Token

1. User open send modal
2. User selects the wallet account to send from
3. User selects an ERC20 token or native chain token
4. User fills an amount
5.1 System updates fiat field to reflect token amount in fiat
5.2 System warns if the amount is invalid (not enough token to make the transaction)
6. User pastes an ethereum address in the to field
6.1 alternative: user types an ens address in the to field
6.2 alternative: user selects an address in the saved section
6.3 alternative: user selects an address in the my accounts section
6.4 alternative: user selects an address in the recent section
6.5 alternative: user types a network preference and an ethereum address in the field
7. System validates address and populate the network preference if they are available from the contact
8. System calculate best route for the transaction
9. (optional) User selects Advance routing and is able to enable/disable chain
9.1 (optional) User can Hide/Show prefered network
10. (optional) User selects Custom routing and is able to enable/disable chain as well as update value for each transaction
11. System displays Priority section with "Optimal" pre selected
12.1 (optional) alternative: User selects a priority
12.2 (optional) alternative: User can selects priority for each transaction
12.3 (optional) alternative: User can update the gas setintgs for each transaction
13. System updates the estimated time
14. System validates if origin account has enough to pay for gas
15. User presses Send
16. System notifies user transactionis  ongoing
17. System notifies user when transaction is complete
17.1 alternative: System notifies user when transaction has failed

### Swap

1. User open swap modal
2. User selects the wallet account to swap
3. User selects the ERC20 token or native chain token to swap from
4. User selects the ERC20 token or native chain token to swap to
5. (optional) User can invert the swap from and to
6. User fills a from amount
6.1 alternative: Users fills the to amount
7. System validates amount
8. System calculate best route for the transaction
9. (optional) User selects Advance routing and is able to enable/disable chain
9.1 (optional) User can Hide/Show prefered network
10. (optional) User selects Custom routing and is able to enable/disable chain as well as update value for each transaction
11. System displays Priority section with "Optimal" pre selected
12.1 (optional) alternative: User selects a priority
12.2 (optional) alternative: User can selects priority for each transaction
12.3 (optional) alternative: User can update the gas setintgs for each transaction
13. System updates the estimated time
14. System validates if origin account has enough to pay for gas
15. User presses Swap
16. System notifies user transaction is ongoing
17. System notifies user when transaction is complete
17.1 alternative: System notifies user when transaction has failed

### Bridge

1. User open bridge modal
2. User selects the wallet account to bridge
3. User selects the ERC20 token or native chain token to bridge
4. User fills the amount
5. System validates amount
6. System calculate best route for the transaction
7. (optional) User selects Advance routing and is able to enable/disable chain
7.1 (optional) User can Hide/Show prefered network
8. (optional) User selects Custom routing and is able to enable/disable chain as well as update value for each transaction
9. System displays Priority section with "Optimal" pre selected
10.1 (optional) alternative: User selects a priority
10.2 (optional) alternative: User can selects priority for each transaction
10.3 (optional) alternative: User can update the gas setintgs for each transaction
11. System updates the estimated time
12. System validates if origin account has enough to pay for gas
13. User presses Swap
14. System notifies user transaction is ongoing
15. System notifies user when transaction is complete
15.1 alternative: System notifies user when transaction has failed

## Functional Requirements

### Chain supported

The following chains are supported in live mode:
* Ethereum Mainnet
* Optimism Mainnet
* Arbitrum Mainnet

In test mode:
* Ethereum Ropsten
* Ethereum Rinkeby

Requirement: it must be trivial to add/remove supported chain

### Bridge supported

The following brigde are supported:
* [hop](https://app.hop.exchange/#/send?token=ETH)
* [connext](https://bridge.connext.network/)
* [cbridge](https://cbridge.celer.network)

Requirement: adding/removing a bridge should not change the routing algorithm as the bridges must be astracted

### Amount field

When entering an amount, it MUST be validated and ensure the account hold enough to proceed the transaction
When entering an amount, the fiat value MUST be updated

### ERC20 token or native chain token selector

The selector MUST display for each token, the symbol, the balance of the account in currency, the fiat in currency, the change in last day
The selector MUST display all known token from all chains
The selector MUST also have a text field to filter the list by typing the name or symbol of the token
### Adddress field

The address field can be filled with multiple option:
1. an ethereum address
2. an ENS name
3. a Contact display name

Plus it can be prefixed by the prefered destinations chains of the transaction separated by `:`

Example of valid address field:

* `0x4d45e726c4089a385730fc14943ea6628051e2dc`
* `eth:opt:0x4d45e726c4089a385730fc14943ea6628051e2dc`
* `anthony.eth`
* `eth:opt:anthony.eth`
* `anthony`
* `eth:opt:anthony`

The address field MUST validate ethereum addreses using [EIP-55](https://eips.ethereum.org/EIPS/eip-55)
The address field MUST have a paste button on the right of the input field
The address field placeholder MUST be `Enter an ENS name or address`

### Address suggestion

The Address suggestion MUST have the following options: saved addresses section, my accounts section, recent section and contacts section
The addresses in the saved addresses section MUST be sorted by favourite state, then by how long ago it was used
The addresses in the saved addresses section MUST display: emoji, display name, how long ago it was used, ethereum address
The addresses in the my accounts section MUST be sorted by display name
The addresses in the my accounts section MUST display: emoji, display name, ethereum address, balance in prefered fiat currency 
The addresses in the my accounts section MUST display the balance in the preference fiat currency only if that balance is more than 0
The addresses in the recent section MUST be sorted by date of how long ago it was used
The addresses in the recent section MUST display the account emoji, display name, how long ago it was used, ethereum address, and balance transfered of the last transaction
The addresses in the contact section MUST be sorted by date by display name
The addresses in the contact section MUST display the account emoji, display name, how long ago it was used, ethereum address, and balance transfered of the last transaction

If an address in the recent section is not in the saved addresses or my accounts section, then it MUST display a default emoji, and display the ethereum address instead of the display name

### Simple routing
#### Networks

The section MUST display the number of assets we are sending to each chain
#### Priority & Gas

The priorities supported MUST be: low, optimal, high
For each priority, the currency amount and expected time MUST be displayed globally
If the origin address does not have enough ether to pay for the choosen amount of gas an error MUST be shown
The estimated time MUST be updated as well as the max fees

Each time there is a change in the priority, the gas and estimation time MUST be re-calculated

### Advanced routing
#### Networks

The section MUST display all chain that support the asset in the source
The section MUST display all chain that are preferred in the destination
A click on show unprefered networks will makes visible all the chain in the destination
If there is enough gas and balance is more than 0, it MUST be possible to enable/disable chain by clicking on them
If an unpreferred networks is selected as destination, there MUST be a warning
If there is not enough asset in the source, an error MUST be displayed
A click on custom networks will toggle them

Each time there is a change in the routing, the gas and estimation time are re-calculated
Each time there is a change in the routing, the amount being transfer by chain are recalculated with a goal of cleaning balance as much as possible

#### Priority & Gas

The priorities supported MUST be: low, optimal, high
If the origin address does not have enough ether to pay for the choosen amount of gas an error MUST be shown
For all inner transactions, the amount in the native chain token and currency MUST be displayed
The estimated time MUST be updated as well as the max fees

### Custom routing
#### Networks

Same as advanced routing +

For each chain it is possible to enter the amount of asset to be transfered
When an amount is entered, this one is being locked
#### Priority & Gas

For each chain display the transaction fee, the gas amount, gas limit, overall limit, value in chain asset and fiat
For each chain display the transaction nonce

When clicking on the transaction it is possible to manualy change the gas parameters

### Notifications

The notification is a snackbar at the bottom right of the app.
There is 3 types of notification:
* Transaction is pending
* Transaction succeed
* Transaction failed

The transaction contains a link to the transaction details view (design in progress)

### Notes

* In this version the routing algorithm doesn't allow intermediate chain
* In this version the routing algorithm there is no internal swap for the purpose of owning gas in other chain