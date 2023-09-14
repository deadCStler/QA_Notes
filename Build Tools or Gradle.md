### Build Tools

They are the programs that automate the creation of an executable application from source code. In other words, build automation is the act of scripting or automating a wide variety of tasks such as:

- Downloading Dependencies
- Compiling source code into Binary Code and then packaging the binary code
- Running tests
- Deployment to production systems.

*Java Class Path* is one way to tell applications where to look for classes and other files. This is specified as environment variable.

When building and running two class paths are involved:

- Compile: List of dependencies that are required for the JDK to able to compile Java code into .class files.
- Runtime: List of dependencies that are required to run the complied Java Code.

Gradle is build tool which helps to build a Java Project.

Library provides a set of functions/objects which we call for specific functionality or it is just a collection of class definitions. We need libraries to avoid code reuse.
Libraries on which application is dependent are dependencies.

Dependencies Management allows teams to manage dependencies for multi-module projects.

```html
./gradlew -q dependencies /*Used to see detailed view of dependency tree*/
```

To define dependencies in Gradle we add them in the `build.gradle` file with the dependencies block.

Gradle needs a specific folder structure to operate, if the code doesn’t follows the structure then Gradle won’t function.

Command line flags, System properties, Gradle properties, environment variables is the precedence considered when build properties are mentioned in multiple location.

`Gradlew` is the Gradle Wrapper, is a script which is added to Gradle project and used to execute our build. The advantages of using `gradlew` are:

- We don’t need to have Gradle installed on your machine to build the project.
- The wrapper guarantees you’ll be using the version of Gradle required by the project (and not necessarily the one installed locally).
- We can easily update the project to a newer version of Gradle, and push those changes to version control so other team members also use the newer version.