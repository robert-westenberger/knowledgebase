---
title: Fake Os
description: 
published: true
date: 2021-11-08T06:36:42.707Z
tags: 
editor: markdown
---

![capture.png](/capture.png)
![ss_0e3a544323f957abf6b7789223e9586c6c3f3cee.1920x1080.jpg](/ss_0e3a544323f957abf6b7789223e9586c6c3f3cee.1920x1080.jpg)
![windows_95_2.png](/windows_95_2.png)
![windows_95_3.png](/windows_95_3.png)
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
 