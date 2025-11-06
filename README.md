## Overview

This file automates the installation and configuration of Windows 11 Pro. Applying system settings, removing unwanted components, and customizing user profiles without manual input.

## Installation Details

- **Edition**: Windows 11 Pro
- **Language**: German (Germany), fallback to English (US)
- **Keyboard Layout**: German
- **Computer Name**: `Tatze-PC`
- **Local User Account**: `Tatze` (Administrator)

## Setup Phases and Actions

### 1. Specialize Phase

#### Removed Pre-installed Apps (Appx Packages)
The following built-in apps are removed for all users:

- Microsoft Copilot
- Microsoft 3D Viewer
- Bing Search
- Windows Calculator
- Windows Camera
- Clipchamp
- Alarms & Clock
- Dev Home
- Family Safety
- Feedback Hub
- Game Assist
- Get Help
- Get Started
- Mail & Calendar
- Maps
- Mixed Reality Portal
- News
- Notepad
- Office Hub
- OneNote
- Outlook
- Paint
- People
- Photos
- Power Automate Desktop
- Quick Assist
- Skype
- Snip & Sketch
- Solitaire Collection
- Sticky Notes
- Teams (Classic and New)
- To Do
- Sound Recorder
- Wallet
- Weather
- Xbox-related apps (Game Bar, Identity Provider, Speech-to-Text, etc.)
- Your Phone
- Movies & TV (ZuneVideo)

#### Removed Windows Capabilities
The following optional capabilities are removed:

- Fax and Scan
- Handwriting recognition
- Internet Explorer
- Math Recognizer
- OneSync
- PowerShell ISE
- Quick Assist support
- Snipping Tool
- Speech recognition
- Text-to-speech
- Steps Recorder
- Windows Media Player
- WordPad
- Windows Hello Face (various versions)

#### Disabled Windows Features
The following optional features are disabled and removed:

- Media Playback
- PowerShell v2
- Recall
- Snipping Tool (legacy)

#### Registry Modifications
- Disables SmartScreen and related Defender notifications
- Disables BitLocker device encryption
- Enables long path support
- Disables startup sound
- Disables Windows Consumer Features
- Configures Windows Update to avoid automatic reboots
- Sets active hours dynamically
- Disables Edge first-run experience and background/startup boost
- Enables Remote Desktop
- Removes access for certain user groups
- Sets execution policy to `RemoteSigned`
- Disables last access time updates
- Configures firewall rules
- Registers scheduled task for managing active hours

### 2. Default User Configuration

#### Registry Changes
- Disables Windows Copilot
- Disables OneDrive auto-start
- Disables Game DVR
- Shows hidden files and file extensions
- Hides Task View button
- Disables Edge SmartScreen and PUA protection
- Disables AppHost web content evaluation
- Disables system sounds
- Disables all content delivery and suggestion features
- Sets mouse speed and thresholds to zero
- Disables search box suggestions
- Enables Taskbar “End Task” option
- Configures StickyKeys
- Registers RunOnce script for further user setup

### 3. First Logon Phase

#### Final Cleanup
- Deletes:
  - `Windows.old`
  - `unattend.xml`
  - `unattend-original.xml`
  - `Wifi.xml`
- Resets `AutoLogonCount` to 0

## Required Files

The following scripts must be present in `C:\Windows\Setup\Scripts\`:

```
Specialize.ps1
DefaultUser.ps1
FirstLogon.ps1
RemovePackages.ps1
RemoveCapabilities.ps1
RemoveFeatures.ps1
SetStartPins.ps1
TurnOffSystemSounds.ps1
MoveActiveHours.xml
UserOnce.ps1
```
