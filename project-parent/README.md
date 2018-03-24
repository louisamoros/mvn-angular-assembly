# angular-parent

This is the parent pom to build, assemble and deploy angular web applications.

## how it works ?

 - maven-resources-plugin
 
copy src/ and commons angular files to project build directory

 - maven-dependency-plugin
 
unpack dependency into project build directory

 - exec-maven-plugin
 
run `npm install` and `npm run build` in project build directory

 - maven-assembly-plugin
 
based on `ng-src` and `ng-build` assembly descriptor, produce two zip files, one with the build, another one with the src

 - nexus-staging-maven-plugin
 
deploy zip files to local nexus
