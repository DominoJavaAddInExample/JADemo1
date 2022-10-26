# JADemo1
JavaAddin example #1 - it prints amount of person documents in names.nsf each 30 seconds
Use it for education purpose.

#How to build JAR using MAVEN
form CLI run commands:

``mvn package``

if run succesfully a file will be created in Target folder (i.e. JADemo1-1.0.0.jar).
It is required to have Notes.jar added to your maven local storage, see how to do that: https://maven.apache.org/guides/mini/guide-3rd-party-jars-local.html

#How to configure Java Addin
Open notes.ini on server and register you addin, the most efficient way would be below (see 3 differnt addins are registered)

``
JavaUserClassesExt=GJA_Genesis,GJA_DominoMeter,JA_Demo1
GJA_DominoMeter=JavaAddin/DominoMeter/DominoMeter-118.jar
GJA_Genesis=JavaAddin/Genesis/Genesis-0.6.15.jar
JA_Demo1=JavaAddinClean/JADemo1-1.0.0.jar
``

After that make sure to restart runjava task

``
tell runjava quit
``

# Run Addin from Domino console
``load runjava JADemo1``

# Unload Addin from Domino console
``tell runjava unload JADemo1``

Here is an example of successful run of JADemo1

![image](https://user-images.githubusercontent.com/844872/198114625-ba4b2bb4-a7ad-48cf-85be-e4d3f5145625.png)
