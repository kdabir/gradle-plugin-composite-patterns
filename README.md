## Including Gradle Plugin through composite builds

Sample Plugin's code is exactly the same in all the three projects. The only difference is how this plugin is included in each consumer build.

1. `direct-include` - consumer directly includes it by changing its own `settings.gradle` file
2. `parent-composite` - tries to include the plugin via a parent composite project (without having to change consumer)
3. `sibling-composite` - tries to include the plugin via a sibling composite project (without having to change consumer)



To reduce file noise, gradle wrapper is not included. Check system gradle

```
$ gradle --version

------------------------------------------------------------
Gradle 6.8.3
------------------------------------------------------------

Build time:   2021-02-22 16:13:28 UTC
Revision:     9e26b4a9ebb910eaa1b8da8ff8575e514bc61c78

Kotlin:       1.4.20
Groovy:       2.5.12
Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
JVM:          11.0.7 (Amazon.com Inc. 11.0.7+10-LTS)
OS:           Mac OS X 10.16 x86_64
```


## Running

1. `gradle -p direct-include/consumer sayHello`

2. `gradle -p parent-composite :consumer:sayHello`

3. `gradle -p sibling-composite/composite :consumer:sayHello`

