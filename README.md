# ImmunoZoo
## Rationale
iCn3D is a product with a long history of supporting scientific requirements. As such it has an expasive nested menu system that uses a mix of common and structural biology specific terms resulting in over 500 menu items. The sheer number of menus, combined with opaque language can be confusing to scientists and daunting to students and teachers. Additionally, the user interface, being web-based, can have challenges related to the nature of running an app in a browser (mouse controls, selects, positioning, responsiveness, refreshing). The goals of this project are to: 
1. identify the common operations needed for completing classroom exercises; 
2. contribute protoype code for reducing the number of menus for testing; and
3. make initial recommendations for education modes of operation.   

## The Zoo
Want to find antibodies from different creatures. 
* First Presentation:  https://docs.google.com/presentation/d/1OnyCz__iWb9fTSz5xCb71lRYy5MXRFTvo_NPsnCH3W0/edit#slide=id.g13bea56a948_0_7
* ImmunoZoo instructions: https://docs.google.com/document/d/1mgUmdTZb0Jm8a7kcAk3M4k7qT7uyJdRhYs5H_GlYShE/edit?usp=sharing
* ImmunoZoo collection of structures: https://docs.google.com/spreadsheets/d/1dNwRKIW9KKBT1mgaUcUotgTucZFmQWeYpRalAzj_OaQ/edit?usp=sharing

### Background info about antibodies
https://docs.google.com/document/d/1FAHEWJQzkU6aisSKvdcxgtUSxdAJa-PTYiNXRngt16s/edit?usp=sharing

## Controlling Menus
In previous work we created a method to prototype whether an iCn3d menu is displayed or not using a menu.json control file. The control file is created by instantiating iCn3d to get the entire html, scraping the menu items, and writing the menus and classes with a control flag (0 no display, 1 display) in a nested json structure. The nesting corresponds to iCn3D's overall menu structure and allows for entire menu blocks (Specified by Self) or individual items to set.  

To build the menu.jason file, first install and build local version of iCn3D following the instructions on the iCn3D page. 
Next, get cn3d_menu_parser.py and follow the instructions on https://github.com/digitaltodd/iCn3D-protyping/tree/main/menu_parser. 

For simple testing of iCn3d_3.12.7 - the "codeathon" version, download and unpack the zip file in this repository. It has a prebuilt menu.jason file with all menus on. 

run: 
* NPM:  http-server -a localhost -o 'icn3d/?menuconfig=menu.json'
* python: python -m http.server | python -m webbrowser 'http://localhost:8080/icn3d/?menuconfig=menu.json'

As this is a prototype workaround a file is needed. I put these in a structures directory, the commands are now:
* NPM:  http-server -a localhost -o 'icn3d/?menuconfig=menu.json&type=pdb&url=/structures/3WD5_icn3d.pdb'
* python: python -m http.server | python -m webbrowser 'http://localhost:8000/icn3d/?menuconfig=menu.json&type=pdb&url=/structures/3WD5_icn3d.pdb'
The type parameter specifies either a pdb file or a png file. For png use type=icn3dpng. The url paramter is the file path. State files can also be loaded for visualizing annotations using the statefile parameter, statefile=/filepath. Besure to specify the root dir in paths ("/"). 
Note: the python http.server default port is 8000 - to change add a port after the command, e.g. "python -m http.server 8080." Maksure localhost:port matches. 

Being able to call the control file, load a pdb, png, or state file requires that the main html file (full.html) be modified. <br>
need to add a description of the process. 


### to do
Ideally we'd like to have the menus under "positive control." That is, we can most menus off. Rather than toggle each menu item, 500+ times!, we should specifiy the menus we want displayed, and pass those to the script to write a control file with all menus off, except for those passed into the menu parser script. Div tags can used for the matching. Self menus have a ui-id-number that can be used.  


