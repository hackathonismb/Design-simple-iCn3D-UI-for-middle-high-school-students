# ImmunoZoo - Making iCn3D accessble for many audiences
## Rationale
iCn3D is a product with a long history of supporting scientific requirements. As such it has an expasive nested menu system that uses a mix of common and structural biology specific terms resulting in over 500 menu items. The sheer number of menus, combined with opaque language can be confusing to scientists and daunting to students and teachers, and others less familiar with structural biology, and (or) new to iCn3D (like many hack/code-athon participants).   Additionally, the user interface, being web-based, can have challenges related to the nature of running an app in a browser (mouse controls, selects, positioning, responsiveness, refreshing). The goals of this project are to: 
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

### Menu file
To build the menu.jason file, first install and build local version of iCn3D following the instructions on the iCn3D page. 
Next, get cn3d_menu_parser.py and follow the instructions on https://github.com/digitaltodd/iCn3D-protyping/tree/main/menu_parser. 

For simple testing of iCn3d_3.12.7 - the "codeathon" version, download and unpack the zip file in this repository. It has a prebuilt menu.jason file with all menus on. 

run: 
* NPM:  http-server -a localhost -o 'icn3d/?menuconfig=menu.json'
* python: python -m http.server | python -m webbrowser 'http:<area>//localhost:8080/icn3d/?menuconfig=menu.json'

### URL parameters
As this is a prototype workaround a file is needed. I put these in a structures directory, the commands are now:
* NPM:  http-server -a localhost -o 'icn3d/?menuconfig=menu.json&type=pdb&url=/structures/3WD5_icn3d.pdb'
* python: python -m http.server | python -m webbrowser 'http:<area>//localhost:8000/icn3d/?menuconfig=menu.json&type=pdb&url=/structures/3WD5_icn3d.pdb'

The type parameter specifies either a pdb file or a png file. For png use type=icn3dpng. The url paramter is the file path. State files can also be loaded for visualizing annotations using the statefile parameter, statefile=/filepath. Besure to specify the root dir in paths ("/"). 
Note: the python http.server default port is 8000 - to change add a port after the command, e.g. "python -m http.server 8080." Maksure localhost:port matches. 

### Main html file
Being able to call the control file, load a pdb, png, or state file requires that the main html file (full.html) be modified with code to accept and parse the relelant parameters. This code is added to a copy of full.html (index.html). As new versions of iCn3D come out, this file needs to be compared to the full.html and updated acccoringly. The index.html in the zip file was quickly updated and may have parts that are out of sycn, but should be adequate for testing general ideas. Using the index.html convention simplifies the url in that the main html file does not need to be specified in the URL (https://icn3d/?params vs https://icn3d/full.html?params); anyname can be used with the predeeding caveat in mind.

### to do
Ideally we'd like to have the menus under "positive control." That is, we can most menus off. Rather than toggle each menu item, 500+ times!, we should specifiy the menus we want displayed, and pass those to the script to write a control file with all menus off, except for those passed into the menu parser script. Div tags can used for the matching. Self menus have a ui-id-number that can be used.  


## Recomendations
Making iCn3D more accessbile for naive users requires changes at both the application and data level. The data and the application create the experiece. 
### Application
1. iCn3D has links everywhere, some make selections, others take you places like databases at NCBI, and <em>all look the same</em> - how do I know what will happen before it happens (maybe it's the underlines) - but a tiny external icon many 
2. Title - always get in the way, I'd like to toggle between show and hide. 
3. Select defined sets appaears in two places. 
4. Lauguage lots of thesee, and example: "hide unselected" instead of "view selection" it paralleles the item and the action hides things.
5. Load assymetric unit - who really knows what that is about? 
6. Default displays - make them easier to convey an understanding of structures (like surface, but it's slow), sphere is good too (better behaved, but needs juice too), but needs more depth (pretty has an impact too)
7. MMDB PDB, vs PDB PDB - they are different. 
8. 

#### How to approach
Can we survey users for their 10 essentials? <br>
* side by site is cool - another journey :)

Separate hard core structural biology from genral use? Molecule World provides insights. <br>
Can we use web tracking tools to "follow" users? <br>
Can we break this down, e.g. top menu by top menu? <br>

### Data
Databases are great, they are often populated in automated ways, that's what makes them great. However, it does not take long to experiece data that do not fit expectations. And, while we want to increase levels of annotation to advance science, files can have much information for eduation purposes. A common practice is to learn principles then use unknowns for assessment.  

### Harmony
iCn3D updates frequently. There are lots of discussions regarding specific applications, different modalities, and local operation. A big question that will come up is how can updates of iCn3D be propogated and synchronized with other versions. Presently some modifications require updating functions in several locations within the code. Micgrating changes from one version to another can take on the order of day(s) to complete.  
