# Show Unix File Permissions

## About

This macOS Automator workflow reads the Unix file permissions of selected Finder files and folders, and displays them in a dialog box.

Inspired by a request for this feature in [MacAdmins Slack](http://macadmins.org/ "MacAdmins Slack"). Though this same behavior can be accomplished in the Terminal (`ls -ld *`), this workflow allows a quick glimpse of selected files without requiring a context change via application switch.

Note that the dialog box will probably not scale well depending on how many files are selected when the service is run. It also has an issue where files with spaces in their names display each space-separated word on its own line. An AppleScript dialog box would parse better, but I try to use native Automator actions whenever possible, so I leave that as an exercise to the reader.

## Instructions

1. Download the `Show Unix File Permissions.workflow` file.
2. Double-click the .workflow file in the Finder.
3. When prompted, click **Install** to add it to your system as a Service.

![Service Installer example screenshot](show-permissions-service-installer.png?raw=true "Service Installer")

To run the action in the future, select the target files or folders in the Finder, then right-click and select *Services > Show Unix File Permissions*.

![Show Unix File Permissions example screenshot of results](show-permissions-example.png?raw=true "Show Unix File Permissions Example Screenshot")

## Automator Workflow Breakdown

Since GitHub can't display Automator workflows in an easy-to-read format, here's a breakdown of all the actions. Feel free to recreate manually if you'd rather not run mysterious workflows from the Internet.

### Document Type: Service

### Input
- Services receives selected **files or folders** in **Finder.app**

### Run Shell Script
~~~~
#!/bin/bash
# Displays Unix permissions for selected files and folders alongside file names.

for f in "$@"
do
	fPerm=$(ls -ld "$f" | awk '{print $1}')
echo "$(basename $f): $fPerm"
done
~~~~

### Set Value of Variable
- Variable: **permissionsList**

### Ask for Confirmation
- Message: **permissionsList**
