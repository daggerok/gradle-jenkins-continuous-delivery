gradle-jenkins-continuous-delivery [![build](https://travis-ci.org/daggerok/gradle-jenkins-continuous-delivery.svg?branch=master)](https://travis-ci.org/daggerok/gradle-jenkins-continuous-delivery)
==================================

running integration tests with db

-> `code` -> `unitTest` ->
    -> `start db` -> `build db schema` -> `integrationTest` -> `stop db` ->
        -> `verify` -> `build` -> `deploy`

```sh
gradle IntegrationTest
run db
...
:compileIntegrationTest...
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
...
```

see .travis.yml

```sh
git clone ...
./gradlew unitTest build
./gradlew integrationTest
```

using gradle wrapper

```sh
./gradlew projects
./gradlew properties
```
