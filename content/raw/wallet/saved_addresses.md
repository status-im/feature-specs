---
title: "Saved Addresses spec"
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

# Saved Addresses

## Motivation

## Definitions

- Network - refers to a blockchains, sidechains and L2 networks
- Ethereum Address - hexadecimal string of 64 characters

## Designs

- [save & edit dialogs](https://www.figma.com/file/FkFClTCYKf83RJWoifWgoX/Wallet-v2?node-id=350%3A83032)
- [saved addresses](https://www.figma.com/file/FkFClTCYKf83RJWoifWgoX/Wallet-v2?node-id=350%3A83030)

## Use Cases

### Save an Address

1. User clicks on "Add Address" button
2. System shows dialog for Add address
3. System randomly selects an emoji
4. (optional) User selects one or more networks
5. User fills in the name of the address
6. (optional) User changes emoji
7. User clicks on "Save" button

### Save an existing Saved Address

prequesites: User is interacting with a particular address (for e.g there is an address in a transaction list)

1. User selects address
2. User clicks on "Save Address" button
3. System shows dialog for save address with that address pre-filled
4. System randomly selects an emoji
4. (optional) User selects one or more networks
5. User fills in the name of the address
6. (optional) User changes emoji
7. User clicks on "Save" button

### Edit an Saved Address

1. User selects an existing saved address
2. User clicks on "Edit Address" button
3. System shows dialog for edit address with that saved address details pre-filled
4. (optional) User changes address
5. (optional) User changes emoji
6. (optional) User changes networks
7. (optional) User changes name
8. User clicks on "Save" button

### Delete a Saved Address

prequesites: User is interacting with the list of saved addresses

1. User selects an existing saved address
2. User selects "Delete" from the context menu
3. System asks for confirmation
4. User confirms

## Functional Requirements

- A Saved Address MAY be associated to one or more networks
- A Saved Address MUST have an ethereum address associated to it
- A Saved Address MUST have a name associated to it
- A Saved Address MUST have an emoji associated to it
- A Saved Address emoji default MAY be randomly selected
- The Saved Address ethereum address MUST be valid
- The Saved Address name MUST be unique
- The Saved Address name MUST be be composed of alphanumeric characters, underscores, and/or hyphens
- The Saved Address name MUST be at least 3 characters long
- The Saved Address name MUST be at most 20 characters long
- A user MUST be able to edit a Saved Address
- A user MUST be able to delete a Saved Address
- A user MUST be asked for confirmation before deleting a Saved Address
- A user MUST be able to favourite a Saved Address only if that adddress is not already favourited
- A user MUST be able to unfavourite a Saved Address only if that adddress is already favourited

## Notes

- For Networks please refer to the multiple networks spec
