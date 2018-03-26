## How to use ?

- launch nexus on docker

`docker run -d -p 8081:8081 --name nexus sonatype/nexus3`

- verify docker nexus is has started ( could be long)

`curl -u admin:admin123 http://localhost:8081/service/metrics/ping`

- set credentials for maven to access nexus

`vi ~/.m2/settings.xml`

```xml
  <!-- add those lines -->
  <servers>
    <server>
      <id>nexus-snapshots</id>
      <username>admin</username>
      <password>admin123</password>
    </server>
  </servers>
```

- deploy project assembly

`cd project-assembly && mvn clean deploy`

- deploy project parent

`cd project-parent && mvn clean deploy`

- deploy project 1

`cd project-child-1 && mvn clean deploy`

- deploy project 2

`cd project-child-2 && mvn clean deploy`

## What is the problem ?

There are two assembly descriptor files `ng-build.xml` and `ng-src.xml` in the `project-assembly` folder.
These assembly files are set up to zip respectively the `dist` and `src` folder when they are inside the `target` directory.
Thus, the first task of the `project-parent` is to copy source files into `target` to use those assembly files.
Is there a way to parameterize this working directory to avoid the copy task and run the assembly files where the pom child wants ?
For example a configuration with a `${working.directory}`.
