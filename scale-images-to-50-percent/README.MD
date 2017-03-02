# Scale Images to 50%

## About

This macOS Automator workflow duplicates image files selected in the Finder, resizes those copies' dimensions to 50%, and renames them to end in "-half" for differentiation.

`Scale Images` isn't a complicated action, but it's good practice to back up files before making changes, so I thought it would be helpful to combine the backup and resize into a single action.

## Instructions

1. Download the `Scale Images to 50%.workflow` file.
2. Double-click the .workflow file in the Finder.
3. When prompted, click **Install** to add it to your system as a Service.

![Service Installer example screenshot](scale-images-service-installer.png?raw=true "Service Installer")

To run the action in the future, select the target image files in the Finder, then right-click and select *Services > Scale Images to 50%*.

## Automator Workflow Breakdown

Since GitHub can't display Automator workflows in an easy-to-read format, here's a breakdown of all the actions. Feel free to recreate manually if you'd rather not run mysterious workflows from the Internet.

### Document Type: Service

### Input
- Services receives selected **image files** in **Finder.app**

### Duplicate Finder Items

### Scale Images
- By Percentage - **50**

### Rename Finder Items
- Replace Text
- Find: " copy" in **full name**
- Ignore Case
- Replace: "-half"
