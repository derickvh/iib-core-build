# iib-core-build-files

This project contains Gradle & Ant build and other files to build, test and deploy IBM Integration Bus applications.

The Ant build is managed by Gradle. The gradle build file sets some ant properties from a build.config file before it imports the Ant build.xml file. A deployment is typically invoked by typing 'gradle multiDeploy' or 'gradle mD' on the command line. Any of the Ant targets/Gradle tasks can be invoked in this way.

There is a Gradle task to execute a SoapUI Test project. It is named 'runSoapUI' or 'rS' for short. If there is no SoapUI project to be executed, leave the SoapUIProject property set to 'None' in the build.config file. The SoapUI project file is expected to be in the projectDir (Ant basedir).

Configuration information or other variable information, such as the parameters one would pass to the mqsicreatebar command, are found in the  build.config file. The mqsiapplybaroverride command (Ant override target) also reads new property values from an overrides properties file.

The following files must be checked and edited before a build is run.

1. build.config - Sets 1) an environment (DEV, QA,PROD) and other properties. 2) application name, 3) mqsicreatebar parameters, 4) Soapui project details.
2. gradle.properties - Contains platform specific information (Windows, Linux, MacOS) for finding IIB and SoapUI executables.
3. override.properties (This file can be left empty if no overrides are to be applied). This file is completely dependent on the application being built.

To use these files Gradle 3.1 or higher is required. 

Clone this repository to local storage. Create a new directory and copy your IIB Application and dependencies (e.g. Libraries) into the new directory. Copy everything in the iib-core-build directory to the IIB Application directory. Edit the property/configuration files to reflect your environment and application.

