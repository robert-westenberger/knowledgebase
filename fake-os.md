---
title: Fake Os
description: 
published: true
date: 2021-11-16T00:31:33.597Z
tags: 
editor: markdown
---

![capture.png](/capture.png)
![ss_0e3a544323f957abf6b7789223e9586c6c3f3cee.1920x1080.jpg](/ss_0e3a544323f957abf6b7789223e9586c6c3f3cee.1920x1080.jpg)
![windows_95_2.png](/windows_95_2.png)
![windows_95_3.png](/windows_95_3.png)

# Mock Requirements
## Mock Page 1
* The layout of the mock should resemble the screenshot of windows 95 (the first image on this webpage). 
	* So in the top left there should be a column of icons and text stacked vertically. 
  * There should be a taskbar on the bottom, with the start menu button clicked open. 
  * The start menu should be displayed, to four levels deep like depicted in the screenshot. The start menu items should display some hover state like they are in the screenshot. 
  * The taskbar should have a button to the right of the start menu button containing an icon and some text, which represents an opened program. (In the screenshot, this is the "Control Panel" button on the taskbar). 
  * On the far righthand side of the taskbar, should be a tiny computer icon with a time. 
  * There should be a window on the desktop opened. Buttons / text / scrollbars should show up in the window in the mock in the same place where they do in the screenshot. 







# Features 
* Depending on the users user agent, actually have that particular theme be the default (So if user is connecting on a windows machine, have the windows theme display).
# Components             
## Taskbar
### Start Button (with logo)
* onClick will toggle the start menu.
### Start Menu (ul)
* Clicking anywhere not in the menu will close the start menu
* Multiply nested. Hovering on a menu item that is itself a menu will open the submenu. 
* Submenus only close if a different menu item is hovered over. (Or the user clicks outside of the menu entirely, in which case all menus close.  
#### Start Menu Item (li)
* Always renders an icon and a label
* Either "executes" some command or is a submenu

### Taskbar buttons (ul)
#### Taskbar button (li)
* Rendered for each open window
* onclick will bring associated window to front / visible
* Always renders an icon and a label
* Label text can be updated 
* Always a fixed width, ellipsis text overflow

### Notification area

## Desktop
### Icon + Label

## Window
 
 
 