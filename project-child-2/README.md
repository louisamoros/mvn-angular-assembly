# npm-mvn-nexus

## How to deploy an angular web application to nexus3 in zip format ?

- launch nexus on docker

`docker run -d -p 8081:8081 --name nexus sonatype/nexus3`

- verify docker nexus is has started

`curl -u admin:admin123 http://localhost:8081/service/metrics/ping`

- package angular web application in zip format

`mvn clean package`

- set credentials for maven to access nexus

`vi ~/.m2/settings.xml`

```xml
  <!-- add those lines -->
  <servers>
    <server>
      <id>nexus-snapshots</id>
      <username>nexus-username</username>
      <password>nexus-password</password>
    </server>
  </servers>
```
  
- deploy angular zipped web application to nexus snapshots

`mvn clean deploy`

## Webapp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.7.3.

### Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

### Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

### Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.

### Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

### Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

### Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
