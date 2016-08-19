# iib-core-build-files

This project contains Gradle & Ant build and other files to build and deploy IBM Integration Bus applications.

The Ant build is managed by Gradle. The gradle build file sets some ant properties from a gradle.properties file before it imports the Ant build.xml file. A deployment is typically invoked by typing 'gradle multiDeploy' or 'gradle mD' on the command line. Any of the Ant targets/Gradle tasks can be invoked in this way.

Configuration information or other variable information, such as the parameters one would pass to the mqsicreatebar command, are found in the respective properties files. The mqsiapplybaroverride command (Ant override target) also reads new property values from a properties file.

The following files must be checked and, if required, edited before a build is run.

1. gradle.properties - 1) Selects an environment (DEV, QA,PROD) and other properties. 2) Sets application name. 3) mqsicreatebar parameters. 4) Soapui project details.
2. override.properties (This file can be left empty if no overrides are to be applied). This file is completely dependent on the application being built.
3. broker.properties. Contains information of the brokers (integration nodes) to which the compiled bar file must be deployed.
