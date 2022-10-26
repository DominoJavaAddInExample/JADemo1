# JavaAddinCoreDemo

## Purpose

Minimal example JavaAddin.  This addin just prints the number of person documents registered on the Domino server in names.nsf every 30 seconds (can be configurable).

## Build instructions:

### Moonshine

The following SDKs must be configured in Moonshine
- Gradle
- OpenJDK 8

Run the project like this:
1. Open the project in Moonshine
2. Open build.gradle and confirm that `notesInstallation` is set to your HCL Notes directory.  TODO:  examples for each OS.
3. Run `Project > Run Gradle Command..." in the project menu.
4. The JAR will be generated at:  `build/libs/JavaAddinCoreDemo.jar`

### Command Line

Make sure you have Gradle installed.  `JAVA_HOME` should be JDK 8.  

For macOS set `DYLD_LIBRARY_PATH`:

	export DYLD_LIBRARY_PATH=/Applications/HCL Notes.app/Contents/MacOS/
	
TODO:  Windows needs Notes on the PATH

Open the project directory and run:

``gradle clean build``

If the build is successful, a file will be created in Target folder (i.e. `JavaAddinCoreDemo.jar`).


## How to load JavaAddin inside of Domino

Copy the JAR build above to a directory under the `JavaAddin` directory in the Domino directory.  For example:

``
/local/dominodata/JavaAddin/JavaAddinCoreDemo/JavaAddinCoreDemo.jar
``

Open notes.ini on server and add your addin to the classpath using the path selected above (relative to the Domino directory). For example:

``
JavaUserClassesExt=JavaAddinCoreDemo
JavaAddinCoreDemo=JavaAddin/JavaAddinCoreDemo/JavaAddinCoreDemo.jar
``

If `JavaUserClassesExt` already exists in notes.ini, you can add the new addin with comma separator:

``
JavaUserClassesExt=ExistingAddin,JavaAddinCoreDemo
``


After that, restart the runjava task:

``
tell runjava quit
``

Ensure all java addins have been unloaded (If the command returns an error, they are unloaded):

``
tell runjava show tasks
``

Then load the addin like this.  The addin name is based on the main class (the class that implements JavaAddinCoreDemo)

``load runjava JavaAddinCoreDemo``

The addin can be unloaded like this

``tell runjava unload JavaAddinCoreDemo``

Here is an example of successful run of JavaAddinCoreDemo

![image](https://user-images.githubusercontent.com/844872/198114625-ba4b2bb4-a7ad-48cf-85be-e4d3f5145625.png)

## Debugging

If you see a message like below:

``
RunJava: Can't find class JavaAddinCoreDemo or lotus/notes/addins/javaaddincoredemo/JavaAddinCoreDemo in the classpath.  Class names are case-sensitive.
``

Then check that:
- `JavaUserClassesExt` and `JavaAddinCoreDemo` are populated correctly according to the instructions above.  
- Navigate to the Domino data directory and check that the JAR path defined in `JavaAddinCoreDemo` exists.
- If you renamed the main class, then make sure that class exists in the compiled JAR.