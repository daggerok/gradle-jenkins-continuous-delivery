gradle-jenkins-continuous-delivery [![build](https://travis-ci.org/daggerok/gradle-jenkins-continuous-delivery.svg?branch=master)](https://travis-ci.org/daggerok/gradle-jenkins-continuous-delivery)
==================================

1. `code` -> `unitTest` ->
2. `start db` -> `build db schema` -> `integrationTest` -> `stop db` ->
3. `verify` -> `build` -> `deploy`

**source code quality**

*sonar*

```sh
docker run -d --name sonarqube -p 9000:9000 -p 9002:9002 sonarqube
./gradlew sonarqube
docker stop sonarqube; docker rm sonarqube
```

**static code analysis**

- pmd
- JDepend (define dependencies)
- checkstyle
- FindBugs
- codenarc (checkstyle + findbugs for groovy)

`unitTest` -> `integrationTest` -> **code analysis** -> `` -> `` 

```sh
./gradlew check # pmd / jdepend
```

**code coverage**

- [Cobertura](#) (offlice bytecode)
- [EMMA](#)  (offlice bytecode)
- [Clover](#) (source code)
- [JACOCO](#) (on-fly bytecode, ships with gradle as a plugin)

*code coverage with JaCoCo for integration tests:*

```sh
./gradlew jacocoIntegrationTestReposrt
```

**running integration tests with db**

`compile  tests`-> `start db` -> `build db schema` -> `integrationTest` -> `stop db`

```sh
./gradlew IntegrationTest
:compile...
...
:startDatabase
starting database...
database is started.
:buildSchema
creating db schema...
db schema is created.
:runDatabase
:integrationTest
:stopDatabase
stopping database...
database is stopped.
```

**how to build** [*see travis build config*](.travis.yml)

```sh
git clone ...
./gradlew unitTest build
./gradlew integrationTest
```

**using gradle wrapper**

```sh
./gradlew projects
./gradlew properties
```
