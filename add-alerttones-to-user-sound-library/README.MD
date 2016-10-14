# Add AlertTones to Sound Library

This Automator workflow copies the audio files (all files with .caf extension) from /System/Library/PrivateFrameworks/ToneLibrary.framework/Versions/A/Resources/AlertTones/ to ~/Library/Sounds, then reformats their names for easier legibility when selecting sounds in System Preferences > Sounds.

Open the .workflow file in Automator to run this on your Mac. Typically it would only need to be run once, but you could save it as an application or service if you want to access it regularly for some reason (it should overwrite any files it's previously copied over).

Find Finder Items
- Search /System/Library/PrivateFrameworks/ToneLibrary.framework/Versions/A/Resources/AlertTones/
- All of the following are true
    - File extension IS caf

Copy Finder Items
- To ~/Library/Sounds
- Replace existing files

Rename Finder Items
- Change Case
- Basename only
- Title Case

Rename Finder Items
- Add Text
- 
- before name

Run Shell Script
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
