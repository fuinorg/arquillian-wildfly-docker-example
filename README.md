# arquillian-wildfly-docker-example
Arquillian test deployed to a remote Wildfly server running in a Docker container

There seems to be a problem while Arquillian connects to a Wildfly 14 that is running in a docker container.

Steps to reproduce:

1. Clone the project: ```git clone git@github.com:fuinorg/arquillian-wildfly-docker-example.git```
2. Compile the project: ```mvn clean compile```
   This also creates a Wildfly Docker container that allows access to the management console with user 'admin' and password 'changeit'.
3. Run the Docker container: ```docker run -p 127.0.0.1:8080:8080 -p 127.0.0.1:9990:9990 -it arquillian-wildfly-docker-example/wildfly:14.0.1.Final```
4. Run test: ```mvn test```
   Fails with "WFLYPRT0023: Could not connect to remote+http://127.0.0.1:9990. The connection timed out"
5. Run test again: ```mvn test```
   Should succeed
   
   