# Hello World Cloud Native Application

This sample demonstrates a cloud native application that is built with multiple
containerized microservice tiers, multiple languages/technology stacks
(polyglot), and leverages third party services.

How to build the Application
---

1. Naviage to the dropwizard-example directory.
1. Build the jar with commmand: mvn clean install
1. Build the container with command: docker build -t dropwizard-example .
1. You can run the container locally with command: docker run -d -p 8080:8080 -p 8081:8081 dropwizard-example:latest
