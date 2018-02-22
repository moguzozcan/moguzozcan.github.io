---
title: "A Gradle Challenge"
date: 2017-10-11
categories: 
  - Jekyll
---

At work we had a situation that some of our used shared project should be in the artifactory, but we do not have any artifactory yet :) 
So what we were doing is pushing the output jars into pTML by building from command line with 'gradle clean build pTML' command. However,
this is not a good solution and we had to handle that. So, I looked at how can we push our jars into the maven local repo immediately 
after a build. Since we had a multiproject and some of the modules are depend on each other, the jars have to be pushed to maven local repo
immediately after the build. I've done many reseacrh and ask questions on stackoverflow. Since I was using gradle for 1 week I was having
hard time to understand the whole process. After some days I came up ending with adding the following one line command into all the 
build.gradle files of projects that need to be pushed. This might seem easy to you but understanding the whole structure and concept is 
very hard :)

```gradle
build.finalizedBy(publishToMavenLocal)
```

By the way, 
Of course the repositories are also defined in some scripts like the following:
```gradle
repositories {
        mavenLocal()
        mavenCentral()
        maven {
            url repoUrl
            credentials {
                username user 
                password password 
            } 
        }
    }
 ```
