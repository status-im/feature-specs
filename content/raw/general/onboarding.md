---
title: "Login & Onboarding spec"
description: ""
date: 2022-08-16T08:48:57+00:00
lastmod: 2022-08-16T08:48:57+00:00
draft: false
images: []
menu:
  raw:
    parent: "general"
weight: 100
toc: true
---

# Login & Onboarding

## Motivation

## Definitions

- Touch ID - Electronic fingerprint recognition used by apple desktop devices

## Designs

- [First time opening app](https://www.figma.com/file/17fc13UBFvInrLgNUKJJg5/Kuba%E2%8E%9CDesktop?node-id=1075%3A312335)
- [Login](https://www.figma.com/file/17fc13UBFvInrLgNUKJJg5/Kuba%E2%8E%9CDesktop?node-id=1023%3A298171)
- [New user](https://www.figma.com/file/17fc13UBFvInrLgNUKJJg5/Kuba%E2%8E%9CDesktop?node-id=1027%3A302661)

## Use Cases

## Functional Requirements

### Initial Screen

- If and only if it's the first time opening the app then the Initial Screen MUST BE displayed
- The allow notifications screen MUST be displayed
- The user MUST agree to the terms to proced
    - `I aknowledge that Status Desktop is in Beta and by using it, I take the full responsibility for all risks concerning my data and funds.`
    - Terms of Use
    - Privacy Policy
- The following two options should be shown
    - "I'm new to Status"
    - "I already use Status"

### Login & Accounts

#### Accounts and types of Logins

- Each account MUST display:
    - The profile picture
        - If no profile picture is available then the initials matching the username MUST be displayed
    - The Identicon ring
        - If and only if the account uses an ENS name the identicon ring MUST NOT be displayed
    - The Display name
        - If and only if the account uses an ENS name, then the ENS name MUST BE displayed instead
    - An icon repesenting the type of login
        - If and only if the account uses a keycard login then the keycard icon MUST BE displayed
        - If the account has a non keycard login then the icon MUST NOT be displayed
- Each account MUST have a type of login:
    - Password
    - Touch ID
    - Keycard

#### Login Screen

- If there are any accounts available then the login screen MUST be displayed.
- The account that last made a login MUST BE selected by default
- The account dropdown MUST NOT show the currently selected account in the list
- The login screen MUST display all available accounts in an account dropdown other than the selected account
- The following options MUST be displayed in the login screen
    - Add new user
    - Add existing Status user
    - Lost Keycard
- If and only if the type of login of the selected user is password then the "Password Login" screen MUST BE displayed
- If and only if the type of login of the selected user is Touch ID then the "Biometrics Login" screen MUST BE displayed
- If and only if the type of login of the selected user is Keycard then the "Keycard Login" screen MUST BE displayed

#### Successful login screen

- If the user logins sucessuflly then a loading screen MUST BE displayed

#### Password Login screen

- Then the password field MUST be displayed
- If the user types a wrong password the error "Password incorrect" MUST BE displayed

####  Biometrics Login screen

- The biometrics logo MUST BE shown only if the platform is MacOS
- The message "Waiting for TouchID." MUST BE displayed
- The option for "Use password instead" MUST BE displayed
- If "Use password instead" is selected the password field MUST BE displayed, this should behave like the password login screen
- If "Use password instead" is selected the Touch ID logo MUST BE displayed, clicking this logo MUST take the user back to the original screen "Waiting for Touch ID"
- If the user biometric login is NOT sucesfull then the biometrics logo MUST BE replaced with a logo indicating an error
- If the user biometric login is NOT sucesfull then a error message "Fingerprint not recognized" MUST BE displayed
- If the user biometric login is NOT sucesfull then the option "Use password instead" MUST BE displayed

#### Keycard Login screen

- The keycard logo MUST BE shown
- If no reader is detected the message "Plug in Keycard reader.." MUST be displayed
- If a reader is detected but no keycard is present the message "Insert your Keycard" MUST be displayed
- If a keycard is present then the loading message "Reading Keycard..." MUST be displayed
- If the keycard is not linked to the seleted account then the error message "Wrong Keycard! The card inserted is not linked to your profile" MUST BE displayed
- If the keycard is not linked to the seleted account then the message "Insert another Keycard" MUST BE displayed
- If the keycard is empty then the error message "The card inserted is empty" MUST BE displayed
- If the keycard is empty then the option "Generate keys for a new Keycard" MUST BE displayed
    - TODO
- If the keycard is locked then the error message "Keycard locked" MUST BE displayed
    - TODO
- If the keycard is locked then the option "Unlock your Keycard" MUST BE displayed
    - TODO
- If the keycard is locked with a PIN then a "Enter Keycard PIN" message MUST BE displayed
- If the keycard is locked with a PIN then a 6 Digit input MUST BE displayed
- If the keycard pin is incorrect then the error message "PIN incorrect" MUST be displayed
- The maximum number of possible PIN attempts MUST BE 3
- If the keycard pin is incorrect then the number of possible attempts MUST decrease by 1 and the message "X attempts" remaining MUST BE displayed
- If the total number of failed attemps reaches the maximum number then the keycard logo MUST BE reaplced with a logo indicating an error
- If the total number of failed attemps reaches the maximum number then the error message "Keycard locked" MUST BE displayed
- If the total number of failed attemps reaches the maximum number then the option "Recover your Keycard" MUST BE displayed
    - TODO

#### Account Syncing screen

- A logo representing the data syncing MUST BE displayed
- The message "Securely transferring data..." MUST BE displayed
- If the profile syncing fails, then the message "Unable to fetch your profile" MUST BE displayed
- If the profile syncing fails, then the option "Try Again" MUST BE displayed
- If the profile syncing fails, then the option "Create new Status profile" MUST BE displayed
- If the profile syncing succeeds then application screen MUST be displayed

### Import existing user

#### Existing User Import screen

- The following options MUST BE displayed
    - "Scan sync code"
    - "Login with Keycard"
    - "Enter a seed phrase"
- Choosing the "Enter a seed phrase" MUST display the "Existing User Seed Phrase Import screen"
- Choosing the "Login with Keycard" MUST display the "Existing User Keycard Login Import screen"
- Choosing the "Scan sync code" MUST display the "Existing User Sync Code Import screen"

#### Existing User Seed Phrase Import screen

TODO: this should be in a seed phrase screen
- The following seed phrase options MUST BE available: "12 words", "18 words", "24 words"
- When displaying this screen for the first time the first seed phrase word input MUST BE auto focused
- Pressing Tab MUST move the focus to the next input
- Choosing another word number MUST keep the already inputed seed phrase words
- Typing in a seed phrase word input MUST show a list of valid word suggestions
- If the seed phrase suggestions is displayed then pressing TAB MUST input the currently selected word
- If the seed phrase suggestions is displayed then pressing ENTER MUST input the currently selected word
- If the seed phrase suggestions is displayed and the user presses the DOWN key, it must select the next suggestion in the list
- If the seed phrase suggestions is displayed and the user presses the UP key, it must select the previous suggestion in the list
- The submit button MUST NOT be enabled until each and every input contain valid seed phrase words
- If the user submits the seed phrase, and the seed phrase is invalid or fails a checksum then the error message "Invalid seed" MUST BE displayed
- If the user submits the seed phrase, and the seed phrase is invalid or fails a checksum then the submit button MUST NOT be enabled until at least one of the input changes
- If the user submits the seed phrase and it's valid then the "account syncing screen" MUST BE displayed

#### Existing User Keycard Login Import screen

- The keycard logo MUST BE shown
- If no reader is detected the message "Plug in Keycard reader.." MUST be displayed
- If a reader is detected but no keycard is present the message "Insert your Keycard" MUST be displayed
- If a keycard is present then the loading message "Reading Keycard..." MUST be displayed
- If the keycard does not store a profile, then the error message "This keycard stores keys but doesn’t store a profile" MUST BE displayed
- If the keycard does not store a profile, then options "Factory reset" and "Cancel" must be displayed
- TODO
- If the keycard is empty then the error message "This Keycard is empty" MUST BE displayed
- If the keycard is empty then the option "Generate keys for a new Keycard" MUST BE displayed
    - TODO
- If the keycard is locked with a PIN then a "Enter Keycard PIN" message MUST BE displayed
- If the keycard is locked with a PIN then a 6 Digit input MUST BE displayed
- If the keycard pin is incorrect then the error message "PIN incorrect" MUST be displayed
- The maximum number of possible PIN attempts MUST BE 3
- If the keycard pin is incorrect then the number of possible attempts MUST decrease by 1 and the message "X attempts" remaining MUST BE displayed
- If the total number of failed attemps reaches the maximum number then the keycard logo MUST BE reaplced with a logo indicating an error
- If the total number of failed attemps reaches the maximum number then the error message "Keycard locked" MUST BE displayed
- If the total number of failed attemps reaches the maximum number then the option "Unlock your Keycard" MUST BE displayed
    - TODO https://www.figma.com/file/17fc13UBFvInrLgNUKJJg5/Kuba%E2%8E%9CDesktop?node-id=7971%3A412047
- If the keycard login is successful then a Biometrics screen must be displayed
- The Biometrics screen MUST display a biometrics logo
- The Biometrics screen MUST display the options "Yes, use Touch ID" and "I prefer to use my PIN"
- Choosing the option "Yes, use Touch ID" MUST display the biometrics screen
    - TODO: unclear here what should happen
- Choosing the option "I prefer to use my PIN" MUST display the "Account Syncing Screen"
- If "Yes, use Touch ID" is successful then the "Account Syncing Screen" MUST BE displayed

#### Existing User Sync Code Import screen

- The options "Sync From Mobile" and "Sync From Desktop" MUST BE displayed

**Sync from mobile**
- The option to sync from mobile MUST display a QR code
- If the mobile app scans the QR code then the "Account Syncing screen" MUST BE displayed

**Sync from desktop**
- A input for the sync code MUST BE displayed
- If a sync code is inputted then the "Account Syncing screen" MUST BE displayed

### New User

### New User screen

- The option "Generate new keys" MUST BE displayed
- The option "Generate keys for a new Keycard" MUST BE displayed
- The option "Import a seed phrase" MUST BE displayed
- Choosing the option "Generate new keys" MUST display the "New Profile screen"
- Choosing the option "Generate keys for a new Keycard" MUST display the "Keycard new keys screen"
- Choosing the option "Import a seed phrase" MUST display the "Import seed screen"

#### New Profile screen
note: refer to "Username & profile spec" for more details

**profile input screen**
- The identicon ring MUST BE displayed
- The user MAY upload a profile image
- The user MUST input a display name
- The next screen must be display if and only if a valid display name as been inputted

**profile details screen**
- The identicon ring MUST BE displayed
- The profile image MAY BE displayed
- The compressed chat key MUST BE displayed
- The emoji hash MUST BE displayed

note: refer to "Password strength spec" for more details

**create password screen**
- The user MUST confirm the password two times
- If the password is valid then the "Biometrics screen" MAY BE displayed
- The Biometrics screen MUST display a biometrics logo
- The Biometrics screen MUST display the options "Yes, use Touch ID" and "I prefer to use my PIN"
- Choosing the option "Yes, use Touch ID" MUST display the biometrics screen
    - TODO: unclear here what should happen
- Choosing the option "I prefer to use my PIN" MUST display the "Account Syncing Screen"
- If "Yes, use Touch ID" is successful then the application MUST be displayed

#### Import seed screen

**initial screen**
- The option "Import a seed phrase" MUST BE displayed
- The option "Import a seed phrase into a new Keycard" MUST BE displayed
- Choosing the option "Import a seed phrase" MUST display the "seed phrase screen"
    - TODO: needs to abstracted
- Succesfully importing a seed phrase MUST display the "New Profile Screen"

**import a seed phrase into a new keycard**

#### Keycard new keys screen

- TODO




## Notes

- Windows and Linux Biometrics are not included in this spec
