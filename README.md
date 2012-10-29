XCODE FORMATTER
================

Xcode formatter use [uncrustify](http://uncrustify.sourceforge.net/) to easily format your source code as your team want it to be !
Add a simple directory in your Xcode project to provide Xcode : 

* __shortcut-based code formatting__ : use a shortcut to format modified sources in the current workspace
* __automatic code formatting__ : add a build phase to your project to format current sources when application builds
* __all sources formatting__ : format all your code with one command line
* __shared formatting rules by project__ : edit and use a same configuration file with your dev team


1) How to setup the code formatter for your project
-----------------------------------------------------

### Install uncrustify

	$ brew install uncrustify

To install brew :
 
	$ ruby -e "$(curl -fsSkL raw.github.com/mxcl/homebrew/go)"


### Check that uncrustify is located in /usr/local/bin/ 

	$ which uncrustify


### Extract CodeFormatter directory and put it in same directory as .xcodeprojet file

![CodeFormatter directory location](https://raw.github.com/octo-online/Xcode-formatter/master/images/directory_location.png)


### Check that your Xcode application is named "Xcode" (default name)

You can see this name in the Applications directory.

Why ? This name is used to get currently opened files with an Applescript script.

If you have multiple instances of Xcode on your mac, ensure that project's one is named "Xcode". Or you can change the name of the application in the CodeFormatter/Uncrustify\_opened\_Xcode\_sources.workflow appleScript.


### Install the automator service Uncrustify\_opened\_Xcode\_sources.workflow

Double-click on this file or copy it to your ~/Library/Services/ folder (create this folder if needed).


2) How to format opened files when building the project
---------------------------------------------------------

### Add on project target a build phase "run script" containing the following line :

	sh CodeFormatter/scripts/formatOpenedSources.sh

![Add build phase](https://raw.github.com/octo-online/Xcode-formatter/master/images/add_build_phase.png)


3) How to format opened files with a shortcut
-----------------------------------------------

### Add a shortcut to the Uncrustify_opened_Xcode_sources service

Go to Xcode > Services > Services preferences and set your shortcut

![Create service shortcut](https://raw.github.com/octo-online/Xcode-formatter/master/images/add_service_shortcut.png)


### Use your shortcut to format code !


 
4) How to format files in command line
----------------------------------------

### To format currently opened files, use formatOpenedSources.sh : 

	$ sh CodeFormatter/scripts/formatOpenedSources.sh


### To format all files, use formatAllSources.sh :

	$ sh CodeFormatter/scripts/formatAllSources.sh PATH

PATH must be replaced by your sources path.


 
5) How to change formatter’s rules
------------------------------------

### Edit CodeFormatter/uncrustify_objective_c.cfg

You can use UniversalIndentGUI (http://universalindent.sourceforge.net/) to simplify edition.
