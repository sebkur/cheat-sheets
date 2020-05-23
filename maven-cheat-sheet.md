# Maven Cheat-Sheet

## Useful commands

List modules:

    mvn help:evaluate -Dexpression=project.modules

Test only some modules:

    mvn test --pl odfdom,validator

Show dependency tree:

    mvn dependency:tree

## Maven lifecycles
* validate - validate the project is correct and all necessary information is available
* compile - compile the source code of the project
* test - test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed
* package - take the compiled code and package it in its distributable format, such as a JAR.
* verify - run any checks on results of integration tests to ensure quality criteria are met
* install - install the package into the local repository, for use as a dependency in other projects locally
* deploy - done in the build environment, copies the final package to the remote repository for sharing with other developers and projects.

## More useful commands

Package a module without running its tests:

    mvn package -Dmaven.test.skip=true -pl generator/schema2template

Execute a main class:

    mvn exec:java -pl generator/schema2template
        -Dexec.mainClass=schema2template.example.odf.PathPrinter

Execute a main class and specify parameters:

    mvn exec:java -pl generator/schema2template
        -Dexec.mainClass=schema2template.example.odf.PathPrinter
        -Dexec.args="argument1"
