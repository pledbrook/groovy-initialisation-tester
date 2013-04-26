Groovy Initialisation Tester
----------------------------

This is a very simple Gradle build to test how long it takes to run very, very
simple apps in Java, Groovy, and Groovy with @CompileStatic. To test a particular
version:

    ./gradlew timeJava
    ./gradlew timeGroovy
    ./gradlew timeGroovyStatic

The app versions take the form of org.example.<type>Main classes which are then
compiled and executed as Java apps.

The biggest difference between `timeGroovy` and `timeGroovyStatic` happens when
the app prints something to `System.out`, presumably because of meta-class
initialisation.

Another interesting bit of behaviour I saw was a hit on the static Groovy version
when `println()` was used in place of `System.out.println()`. Not sure why that's
the case.

BTW, the whole point of these tests was to see whether it's possible to write
Groovy scripts/apps that start up really quickly, so users don't see that noticeable
lag when running them from the command line. Looks like static compilation means
you can!
