---
title: "Chat Input spec"
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

# Chat Input Spec

## Designs

* [text formatting](https://www.figma.com/file/Mr3rqxxgKJ2zMQ06UAKiWL/%F0%9F%92%AC-Chat%E2%8E%9CDesktop?node-id=4144%3A41923)
* mentions (todo: add link)
* emojis (todo: add link)
* code tags (todo: add link)

## Use cases

### Mentions

Preconditions: 
- The user MUST be in a chat

*Primary Scenairo*
1. User types `@` in chat input box
2. System opens the @mention suggestions menu. Valid contacts are listed in alphabetical order
3. User types another character
4. System filters the suggestions so that only suggestions that match the characters the user has typed after the`@` symbol are displayed.  The results of this filtering are orded by the following criteria:
    1) Results that match the search in the beginning of the username
    2) Results that closely match the query
    3) Alphabetical
5. User sees that the person they wish to @mention is at the top of the suggestions menu (top menu item is always focused by default)
6. User presses ENTER to select the focused contact
7. System closes the suggestions menu and completes the @mention string in the text input box
USE CASE ENDS

*Variation 5a - User moves the focus in the menu*
1. User sees that the person they wish to @mention in the suggestions menu but that person is not focused 
2. User moves the focus in the suggestions menu using the up and down cursors to the person they wish to @mention (if needed)
RETURN TO 7

*Variation 5b - User abandons selecting somebody to @mention*
1. User decides that they don't want to @mention anybody 
2. User presses SPACE or ESC
3. System closes the suggestions menu and returns focus to the text entry box.
4. System places the text caret at the end of whatever the user has typed, including whatever the user typed while navigating and/or closing the suggestions menu.   
USE CASE ENDS

### Emojis

TODO

### Code Tags

TODO

### Text Formatter

TODO

## Functional Requirements

**preconditions**

- The user MUST be in a chat

### Mentions

User types a message and when the character `@` is typed it opens a menu with a list of suggestions, the user can then select a suggestion to autocomplete it

- Typing `@` MUST open a suggestions menu
- Typing after the `@` character will filter the suggestions to match what is being suggested
- Initially the ordering of the suggestions SHOULD follow an alphabetical order
- When a user starts the search the ordering of the suggestions menu MUST follow the following criteria in order
    1. Results that match the search in the beginning of the username
    2. Results that closely match the query
    3. Alphabetical
- The suggestion menu MUST have a selector
- Pressing the key `Enter` or the key `Tab` MUST autocomplete with the currently selected mention

### Emojis

User types a message and once the character `:` is typed the next character type will either autoreplace the text with an emoji or open a suggestions menu

- Typing `:` followed by a known character that forms an emoji MUST auto replace it with an emoji for example typing `:)` will replace it with 🙂
- Typing `:` followed by one or more alphabetical characters MUST open a suggestions menu
- When a user starts the search the ordering of the suggestions menu MUST follow the following criteria in order
    1. Results that match the search in the beginning of the emoji name
    2. Results that closely match the query
    3. Alphabetical
- The suggestion menu MUST have a selector
- Pressing the key `Enter` or the key `Tab` MUST autocomplete with the currently selected emoji

### Code Tags

TODO

### Text Formatter

User types a message and afterwards can select part of his message and apply styles to it such as bold, italic, strikethrough or code tag. The user can also use markdown while typing the tag to apply these styles (e.g `**bold**``)

- Selecting text with the cursor MUST display the formatting menu
- Selecting text with the keyboard (shift + arrow keys) SHOULD display the formatting menu
- Selecting one of the options in the formatting menu MUST change the selected text to reflect the markdown that applies that style
- When an option in the formatting menu is selected the formatting menu SHOULD remain open
- When text is selected with the keyboard, key combinations MUST apply that style and change the selected text to reflect the markdown that applies that style
    - CTRL+B (windows/linux) CMD+B (mac) - bold
    - CTRL+I (windows/linux) CMD+I (mac) - italic

### General

- `SHIFT+ENTER` MUST create a new line
- ONLY in 1 to 1 chats MUST the "chat transactions" functionality be available, it MUST NOT be available in any other chat types.
- The "send image" functionality MUST be avaialble in all chat types EXCEPT public chats
- copying and pasting text MUST work
    - CTRL+C (windows/linux) CMD+C - MUST be able to copy the selected text from the chat input to the clipboard
    - CTRL+V (windows/linux) CMD+V - MUST paste text from the clipboard with styles applied
    - CTRL+X (windows/linux) CMD+X - MUST cut the selected text from the chat input and put it in the clipboard
- `CTRL+A` MUST select the entire text
- `shift+arrow keys` MUST select text[](https://)
