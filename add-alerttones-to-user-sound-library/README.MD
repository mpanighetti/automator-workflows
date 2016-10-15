# Add AlertTones to Sound Library

## About

This macOS Automator workflow copies the audio files (all files with .caf extension) from `/System/Library/PrivateFrameworks/ToneLibrary.framework/Versions/A/Resources/AlertTones/` to `~/Library/Sounds`, then reformats their names for easier legibility when selecting sounds in *System Preferences > Sounds*.

Inspired by a [Six Colors post from Jason Snell lamenting the staleness of macOS' default system sounds](https://sixcolors.com/post/2016/10/wish-list-new-mac-alert-sounds/ "Six Colors - Wish List: New Mac Alert Sounds"). He brought the existence of the AlertTones to my attention, and I figured others might want a method of using these files alongside the classic sounds.

## Instructions

Open the .workflow file in Automator to run this on your Mac. Typically it would only need to be run once, but you could save it as an application or service if you want to access it regularly for some reason (it should overwrite any files it's previously copied over).

## Automator Workflow Breakdown

Since GitHub can't display Automator workflows in an easy-to-read format, here's a breakdown of all the actions. Feel free to recreate manually if you'd rather not run mysterious workflows from the Internet.

### Find Finder Items
- Search `/System/Library/PrivateFrameworks/ToneLibrary.framework/Versions/A/Resources/AlertTones/`
- All of the following are true
    - File extension IS `caf`

### Copy Finder Items
- To `~/Library/Sounds`
- Replace existing files

### Rename Finder Items
- Change Case
- Basename only
- Title Case

### Rename Finder Items
- Add Text
- ""
- before name

### Run Shell Script
~~~~
#!/bin/bash

for file in ~/Library/Sounds/**
	do
	mv "$file" "`echo $file | \
	sed 's/-/ /g' | \
	sed 's/_/ /g' | \
	sed 's/Sms/SMS/g' | \
	sed 's/[0-9]/ &/g' | \
	tr -d `"
done
~~~~
