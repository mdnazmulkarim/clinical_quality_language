# Overview

This is a simple quickstart project for the CQL java libraries.  It demonstrates how to generate
and build Java lexers, parsers, listeners, and visitors using gradle and the CQL
[ANTLR4](http://www.antlr.org/) grammar.  It also contains the start of a simple proof of concept
visitor class for processing CQL files.

# Building the Project

This project uses the [Gradle](http://www.gradle.org/) build system.  A gradle wrapper, which
automatically downloads and uses an instance of gradle, is provided for convenience.  To build the
project, simply execute the following command:

    ./gradlew build

This will generate the ANTLR4 artifacts to `src/generated`, build the CQL code library, build the
example classes, and execute the example unit tests.

To clean up the artifacts:

    ./gradlew clean

# Generating IDE Projects

You can generate an IDE project for IntelliJ IDEA:

    ./gradlew idea

This is preferred over having IDEA load the gradle file directly, because it (a) generates the CQL
libraries, and (b) generates the configuration for the IDEA ANTLR plugin.  To open the project in
IntelliJ IDEA, launch IDEA and open the `java-quickstart.ipr` file.

See further below for installing and using the ANTLR plugin for IDEA.

# Executing the Sample Code

You can execute the sample code using the `gradlew` command or a script generated by gradle.

To execute the sample code using `gradlew`, you must execute the `run` command:

    ./gradlew run

To execute the sample code using a script generated by gradle, first generate the scripts:

    ./gradlew installDist

Then execute the generated script (optionally passing in an argument).  The following example
executes the sample cql code with the path to a CQL file as an argument:

    ./build/install/java-quickstart/bin/java-quickstart ./src/test/resources/ChlamydiaScreening_CQM.cql

# Installing the ANTLR Plugin for IntelliJ IDEA

The following steps detail how to install the
[ANTLR plugin](http://plugins.jetbrains.com/plugin/7358?pr=) for IntelliJ IDEA.  This allows you to
more easily edit and test the grammar, even supporting real-time parse trees of CQL files.  These
instructions apply to the Mac OS X version, but installation on Windows should be similar.

1. Download and install the [IntelliJ IDEA Community Edition](http://www.jetbrains.com/idea/download/)
   if you don't have it already
2. Open IntelliJ and open the "Preferences" pane (IntelliJ IDEA --> Preferences)
3. Choose "Plugins" from the "IDE Settings" section
4. Click the "Browse Repositories..." button
5. Use the search box to find the "ANTLR v4 grammar plugin"
6. Click the "Install Plugin" button
7. After installation, restart IDEA

_NOTE: There is currently a minor incompatibility between the ANTLR plugin for IDEA and the ANTLR4_
_libraries used by the gradle project.  The plugin uses a 4.4.x version of ANTLR, but the gradle_
_project uses 4.3.  As a result, if you regenerate the ANTLR lexer/parser classes using the plugin_
_(for example, by editing the g4 file from the IDE), the generated classes will not run using the_
_ANTLR 4.3 runtime libraries.  If this happens, re-run `gradle build` to fix it._

# Using the ANTLR Plugin for IntelliJ IDEA

The most helpful feature of the ANTLR plugin for IDEA is the ability to test CQL phrases and
see dynamic parse trees for them.  To do this:

1. Open the cql.g4 file (located in `src/main/resources`)
2. Right-click the `logic` grammar rule in the file
3. Choose "Test Rule logic"
4. Enter a phrase in the preview window to see if it is valid and generate a parse tree

Note: You can test other grammar rules by changing the rule you select in step 2.

# License

Copyright 2014 The MITRE Corporation

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
