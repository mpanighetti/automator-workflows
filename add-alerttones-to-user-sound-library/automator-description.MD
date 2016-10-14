# Add AlertTones to Sound Library

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
