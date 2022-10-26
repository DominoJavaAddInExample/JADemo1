# JADemo1

#Purpose
Use it for education or test purpose.

The addin just prints amount of person documents registered on Domino server in names.nsf each 30 seconds (can be configurable)

#How to build JAR using MAVEN

Make sure you have Maven installed.

form the project in CLI run command:

``mvn package``

if run succesfully a file will be created in Target folder (i.e. JADemo1-1.0.0.jar).
It is required to have Notes.jar added to your maven local storage, see how to do that: https://maven.apache.org/guides/mini/guide-3rd-party-jars-local.html

#How to load JADemo1 inside of Domino

Open notes.ini on server and register you addin, the most efficient way would be below (see 3 differnt addins are registered)

``
JavaUserClassesExt=GJA_Genesis,GJA_DominoMeter,JA_Demo1
GJA_DominoMeter=JavaAddin/DominoMeter/DominoMeter-118.jar
GJA_Genesis=JavaAddin/Genesis/Genesis-0.6.15.jar
JA_Demo1=JavaAddinClean/JADemo1-1.0.0.jar
``

Make sure you uploaded JADemo1-1.0.0.jar to the folder JavaAddinClean. On Windows it would be under Domino folder while on Linux it could be under Data folder.

After that restart runjava task (first make quit and than load).

``
tell runjava quit
``

Ensure all java addins have been unloaded by command

``
tell runjava show tasks
``

# Run Addin from Domino console
``load runjava JADemo1``

# Unload Addin from Domino console
``tell runjava unload JADemo1``

Here is an example of successful run of JADemo1

![image](https://user-images.githubusercontent.com/844872/198114625-ba4b2bb4-a7ad-48cf-85be-e4d3f5145625.png)

If you see a message like below it means you have not registered JavaAddin properly or maybe it's built somehow worng.

> [57CC:0002-3994] 10/26/2022 09:12:08 PM  RunJava: Can't find class JADemo1 or lotus/notes/addins/JADemo1/JADemo1 in the classpath.  Class names are case-sensitive.
