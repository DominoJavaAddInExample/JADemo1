# JavaAddinCoreDemo

## Purpose

Minimal example JavaAddin.  This addin just prints the number of person documents registered on the Domino server in names.nsf every 30 seconds (can be configurable).

## How to build JAR using MAVEN

Make sure you have Maven installed.

form the project in CLI run command:

``mvn package``

if run succesfully a file will be created in Target folder (i.e. JavaAddinCoreDemo-1.0.0.jar).
It is required to have Notes.jar added to your maven local storage, see how to do that: https://maven.apache.org/guides/mini/guide-3rd-party-jars-local.html

## How to load JavaAddinCoreDemo inside of Domino

Open notes.ini on server and register your addin. For Example:

``
JavaUserClassesExt=GJA_Genesis,GJA_DominoMeter,JavaAddinCoreDemo
GJA_DominoMeter=JavaAddin/DominoMeter/DominoMeter-118.jar
GJA_Genesis=JavaAddin/Genesis/Genesis-0.6.15.jar
JavaAddinCoreDemo=JavaAddinCoreDemo/JavaAddinCoreDemo-1.0.0.jar
``

Make sure you uploaded JavaAddinCoreDemo-1.0.0.jar to the folder JavaAddinClean. On Windows it would be under Domino folder while on Linux it could be under Data folder.

After that restart runjava task (first make quit and than load).

``
tell runjava quit
``

Ensure all java addins have been unloaded by command

``
tell runjava show tasks
``

### Run Addin from Domino console

``load runjava JavaAddinCoreDemo``

### Unload Addin from Domino console

``tell runjava unload JavaAddinCoreDemo``

Here is an example of successful run of JavaAddinCoreDemo

![image](https://user-images.githubusercontent.com/844872/198114625-ba4b2bb4-a7ad-48cf-85be-e4d3f5145625.png)

If you see a message like below it means you have not registered JavaAddin properly or maybe it's built somehow worng.

> [57CC:0002-3994] 10/26/2022 09:12:08 PM  RunJava: Can't find class JavaAddinCoreDemo or lotus/notes/addins/JavaAddinCoreDemo/JavaAddinCoreDemo in the classpath.  Class names are case-sensitive.
