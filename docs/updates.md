# Updates

The app checks for a new version when it starts and every six hours. When there is one, it downloads it in the background, checks it's exactly the file that was released (its SHA-512 checksum), and says so. Then:

- **Restart now** in the message (or **Restart to update** in the title bar, or at the bottom of Settings) installs it straight away, or
- it installs the next time you quit the app. Closing the window keeps the app in the tray, so quit from there: right-click the tray icon → **Quit AzTech PRador**.

If a review is running, restarting asks first: the review is stopped, and you can run it again after the update.

**Check for updates** is at the bottom of Settings, and in the command palette.

## What's new

After an update, the app shows what's new in it. **Release notes** at the bottom of Settings (or <kbd>Ctrl</kbd>+<kbd>K</kbd> → "What's new") shows the notes of every version. They're also on the [releases page](https://github.com/mtomorowicz/AzTech-releases/releases).

## Copies that don't update

The installed app updates itself. These don't, and the bottom of Settings says "Updates are off for this build":

- the portable `.exe`: download the new one from the [releases page](https://github.com/mtomorowicz/AzTech-releases/releases), or install with the setup `.exe` instead;
- test builds, whose version has a label after it (`0.9.54-pr.12`, say).
