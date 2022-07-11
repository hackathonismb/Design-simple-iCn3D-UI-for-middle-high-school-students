# ImmunoZoo
## Rationale
iCn3D is a product with a long history of supporting scientific requirements. As such it has an expasive nested menu system that uses a mix of common and structural biology specific terms resulting in over 500 menu items. The sheer number of menus, combined with opaque language can be confusing to scientists and daunting to students and teachers. Additionally, the user interface, being web-based, can have challenges related to the nature of running an app in a browser (mouse controls, selects, positioning, responsiveness, refreshing). The goals of this project are to: 1. identify the common operations needed for completing classroom exercises, 2. contribute protoype code for reducing the number of menus for testing, and 3. make initial recommendations for education modes of operation.   

### the zoo
Want to find antibodies from different creatures. 
First Presentation:  https://docs.google.com/presentation/d/1OnyCz__iWb9fTSz5xCb71lRYy5MXRFTvo_NPsnCH3W0/edit#slide=id.g13bea56a948_0_7
ImmunoZoo instructions: https://docs.google.com/document/d/1mgUmdTZb0Jm8a7kcAk3M4k7qT7uyJdRhYs5H_GlYShE/edit?usp=sharing
ImmunoZoo collection of structures: https://docs.google.com/spreadsheets/d/1dNwRKIW9KKBT1mgaUcUotgTucZFmQWeYpRalAzj_OaQ/edit?usp=sharing

###Background info about antibodies
https://docs.google.com/document/d/1FAHEWJQzkU6aisSKvdcxgtUSxdAJa-PTYiNXRngt16s/edit?usp=sharing

### Controlling Menus
Note: Requires that a local server be running
Install a local version of iCn3D
See https://github.com/digitaltodd/iCn3D-protyping/tree/main/menu_parser for python code

For testing
unpack the zip file
create a public_html directory
mv icn3d dir to public_html
run: 
* Using NPM:  http-server -a localhost -o 'icn3d/?menuconfig=menu.json'
* Using python: python -m webbrowser 'http://localhost:8080/icn3d/?menuconfig=menu.json'
