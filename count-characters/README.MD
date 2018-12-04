# Count Characters

## About

This macOS Automator workflow counts characters for selected text in Notes, and displays the results as a Notification Center notification.

## Instructions

1. Download the `Count Characters.workflow` file.
2. Double-click the .workflow file in the Finder.
3. When prompted, click **Install** to add it to your system as a **Quick Action**.

![Quick Action install example screenshot](count-characters-quick-action-install.png?raw=true "Quick Action")

To run the action in the future, select the target text in any application, then right-click and select *Services > Count Characters*.

![Show Unix File Permissions example screenshot of results](count-characters-notification-example.png?raw=true "Count Characters Notification Example Screenshot")

## Automator Workflow Breakdown

Since GitHub can't display Automator workflows in an easy-to-read format, here's a breakdown of all the actions. Feel free to recreate manually if you'd rather not run mysterious workflows from the Internet.

### Document Type: Quick Action

### Input
- Workflow receives current **text** in **Notes.app**

### Run Shell Script
~~~~
#!/bin/bash
# Counts characters for selected text in Notes.

echo "$@" | wc -m | bc
~~~~

### Set Value of Variable
- Variable: **characterCount**

### Display Notification
- Title: Count Characters
- Message: **characterCount**
