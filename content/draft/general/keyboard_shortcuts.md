---
title: "Keyboard shortcuts spec"
description: ""
version: "2.0"
date: 2020-12-01T08:48:57+00:00
lastmod: 2020-12-01T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "general"
weight: 100
toc: true
---

# Keyboard Shortcuts spec

## Motivation

Users often use keyboard shortcuts to more effectively navigate applications. This spec aims to document the keyboard shortcuts available as well as any preconditions.

## Designs

* [shortcut list modal](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=2457%3A357870)

## Functional Requirements

### Key definition

The requirements will use the keys `CMD` and `OPT` which are defined for each platform as follows:

- `CMD`
    - macOS: `⌘` or `CMD`
    - Windows: `Ctrl`
    - Linux: `Ctrl`
- `OPT`
    - macOS: `⌥` or `OPT`
    - Windows: `Alt`
    - Linux: `Alt`

### Keyboard shortcuts help

- `CMD + /` MUST open a modal listing available key shortcuts
- The Modal listing available keyshortcuts MUST display the correct keys depending on the platform, for example `CMD + C` on macOS and `Ctrl + C` on Windows.

### Keyboard shortcuts

- `ESCAPE`:
    - if input box is already in focus then focus MUST BE removed completely
    - if there is nothing in focus then the input box MUST be focused

#### Navigation shortcuts

- `OPT + ENTER + UP` - MUST select the previous community, if there is no previous community then it MUST select the last community
- `OPT + ENTER + DOWN` - MUST select the next community, if there is no next community then it MUST select the first community
- `OPT + UP` - MUST select the previous channel, if there is no previous channel then it MUST select the last channel
- `OPT + DOWN` - MUST select the next channel, if there is no next channel then it MUST select the first channel
- `CMD + [` - MUST Navigate backward in page history
- `CMD + ]` - MUST Navigate forward in page history
- `OPT + SHIFT + UP` - MUST select the previous unread channel, if there is no previous unread channel then it MUST select the last unread channel, if there is no unread channels then it MUST select the first channel
- `OPT + SHIFT + DOWN` - MUST select the next unread channel, if there is no next unread channel then it MUST select the first unread channel, if there is no unread channel then it MUST select the first channel
- `OPT + SHIFT + OPT + UP` - MUST select the previous unread channel with mentions, if there is no previous unread channel with mentions then it MUST select the last unread channel with mentions, if there is no unread channels with mentions then it MUST select the first channel
- `OPT + SHIFT + OPT + DOWN` - MUST select the next unread channel with mentions, if there is no next unread channel with mentions then it MUST select the first unread channel with mentions, if there is no unread channels with mentions then it MUST select the first channel

#### Communities Shortcuts
requirement: a community must be selected

- `SHIFT + ESCAPE` - MUST mark as community as read
- `ESCAPE` - MUST mark a community channel as read
- `CMD + P` - MUST toogle pins popout
- `CMD + i` - MUST toogle inbox popout
- `CMD + SHIFT + E` - MUST mark top inbox channel as read
- `CMD + U` - MUST toggle channel member list

#### Chat shortcuts

- `CMD + E` - MUST toggle emoji picker 
- `CMD + G` - MUST toggle GIF picker 
- `CMD + S` - MUST toggle sticker picker 
- `PAGE UP` - MUST Scroll chat up
- `PAGE DOWN` - MUST Scroll chat down
- `SHIFT + PAGE UP` - MUST jump to oldest unread message
- `CMD + SHIFT + H` - MUST trigger Help
- `CMD + F` - MUST trigger search modal

## Notes

- Comparision of keyboard shorcuts https://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts
