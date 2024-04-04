# Choosen Language/Framework: Spring boot /JAVA

We choose gradle as our build automation tool and to build the spring boot projects. We can also choose maven instead of Gradle.
We need to add all our dependencies and configurations of our project into a file called build.gradle file. 
### Linting:
   There are various plugins for java linting. We have choosen checkStyles plugin for linting our spring boot project.We need to add checkStyles into the build.gradle file plugins array.
### Testing: 
   We have choosen JUnit as our testing framework.After writing tests we can run tests with gradle tests command. We also can automate the tests to run whenever we are building the project.
### Building: 
   With gradle, we can easily turn our java code into an executable JAR file.We need to use the command gradle build. 

## Alternatives to Github actions / Jenkins: 
   Travis CI, Circle CI, Bamboo, Gitlab CI/CD. There are various platforms for setting up CI/CD in a spring boot project.
## We made the decision to use a cloud based approach since we are only a team of 6 people and also our product is still in early stage. If required , we may use a self hosted servers to manage ci/cd like jenkins or anything else.