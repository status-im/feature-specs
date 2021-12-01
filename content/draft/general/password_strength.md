---
title: "Password strength spec"
description: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "general"
weight: 100
toc: true
---

# Password Strength spec

## Motivation

It's quite important the user chooses a strong password since the entire database is encrypted using that password. No matter how strong the encryption is, if the someone is able to brute force the password, they can read the database. This is why it's important to choose a strong password and to make sure it's not easy to guess. We can aid the user to choose a strong password by providing certain criteria.

## Designs

* [designs](https://www.figma.com/file/IPpvkpDWabBKJTeo6bFop0/Kuba%E2%8E%9CDesktop?node-id=11%3A4921)

## Use Cases

### Account creation

1. User types the choosen password in the password field
2. System displays feedback on the strength of the password
2.1 System checks if the password fits criteria (see Functional Requirements#password criteria) and displays feedback (e.g "Password is too short")
2.2 System categorizes password strength (see Functional Requirements#password categorization) and displays matching category (e.g password Is "Good")
2.2 System checks if password is a common password (see Functional Requirements#password validation) and displays feedback (e.g "this pasword has been pwned and shouldn't be used")
3. User types password again in the confirm password field
4. System checks if password matches and displays "Passwords don't match" if they don't
5. System checks if password matches and enables the "Create" button if they do
6. User clicks "Create" button

### Change password

1. User types the current password in the current password field
2. User types the choosen password in the new password field
3. System displays feedback on the strength of the password
4.1 System checks if the password fits criteria (see Functional Requirements#password criteria) and displays feedback (e.g "Password is too short")
4.2 System categorizes password strength (see Functional Requirements#password categorization) and displays matching category (e.g password Is "Good")
4.2 System checks if password is a common password (see Functional Requirements#password validation) and displays feedback (e.g "this pasword has been pwned and shouldn't be used")
5. User types password again in the confirm password field
6. System checks if password matches and displays "Passwords don't match" if they don't
7. System checks if password matches and enables the "Create" button if they do
8. User clicks "Create" button
7. System checks if current password is valid and displays "Current password is invalid" if it isn't

## Functional Requirements

### Password criteria
- A password MUST BE at least 6 characters long.
- A password MUST BE at most 64 characters long.
- A password MUST NOT contain spaces.
- A password MAY CONTAIN any printable ascii character.

### Password validation

- A password MUST be checked against a list of common passwords
    - If a password matches a common password, it MUST BE rejected
    - If a password matches a common password, it MUST BE display a warning "this pasword has been pwned and shouldn't be used"
    - If the application is online, the password MAY BE checked against an online or a local database.
    - If the application is offline, the password MAY BE checked against a local database.

### Password categorization
- A Password MUST BE categorized as one of the following:
  - Very Weak
  - Weak
  - So-So
  - Good
  - Great
- **TODO**: criteria for each category

### Misc functionality

- It MUST BE possible to paste a password from the clipboard.
- it MUST be possible to view the password in the password field.
- Everytime a password is created or changed, it MUST BE confirmed in a second password field.
- If the password is being changed, the current password MUST BE confirmed.

## Notes

some resources:
- API to check passwords against a list of common passwords: https://haveibeenpwned.com/API/v3#PwnedPasswords
- Bitwarden password verifier https://github.com/bitwarden/jslib/blob/c7ac645eb7b0cfa9c972dd382d63fab5893e1f82/src/services/passwordGeneration.service.ts#L383
- Password Strength Estimation https://github.com/dropbox/zxcvbn
- SecLists Password Repo https://github.com/danielmiessler/SecLists/tree/master/Passwords
