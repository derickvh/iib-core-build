# iib-core-build-files

This project contains Gradle & Ant build and other files to build, test and deploy IBM Integration Bus applications.

The Ant build is managed by Gradle. The gradle build file sets some ant properties from a gradle.properties file before it imports the Ant build.xml file. A deployment is typically invoked by typing 'gradle multiDeploy' or 'gradle mD' on the command line. Any of the Ant targets/Gradle tasks can be invoked in this way.

There is a Gradle task to execute a SoapUI Test project. It is named 'runSoapUI' or 'rS' for short. If there is no SoapUI project to be executed, leave the SoapUIProject property set to 'None' in the gradle.properties file. The SoapUI project file is expected to be in the projectDir (Ant basedir, IIB workspace).

Configuration information or other variable information, such as the parameters one would pass to the mqsicreatebar command, are found in the respective properties files. The mqsiapplybaroverride command (Ant override target) also reads new property values from an overrides properties file.

The following files must be checked and, if required, edited before a build is run.

1. gradle.properties - Sets 1) an environment (DEV, QA,PROD) and other properties. 2) application name, 3) mqsicreatebar parameters, 4) Soapui project details.
2. override.properties (This file can be left empty if no overrides are to be applied). This file is completely dependent on the application being built.
3. broker.properties. Contains information of the brokers (integration nodes) to which the compiled bar file must be deployed.

To use these files Gradle 2.14.1 is required. That assumes that Java is installed and the JAVA_HOME environment variable set.

Clone this repository to local storage. Create a new directory and copy your IIB Application and dependencies (e.g. Libraries) into the new directory. Also copy everything in the iib-core-build directory to this directory. Edit the property files to reflect your environment and application.

Make sure that the mqsi environment has been initialised before you run the gradle script.
