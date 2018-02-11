# deors-demos-cloud-openshift

Demonstration of a simple Java web application deployed on Red Hat OpenShift Container Platform 3.

The application is Spring-based and deployed on WildFly server.

This project is an evolution of deors-demos-cloud-rhc, which was targetted at OpenShift 2.

The steps needed to recreate this project in your own OpenShift Online 3 account (analogous steps
will work at any OCP installation) are the following:

1. Login into OpenShift web console

2. Create a new project. For example: deors

3. Add pod for the database, selecting the MySQL image. Give it a service name and database name.
User name and password can be left blank, and OCP will generate some for you. Take note of both
parameters if automatically generated, as they will be needed later to connect with the web
application.

4. Add pod for the web application, selection the WildFly 10.1 image. Strategy is source build, so
don't forget to add the project repository SSH URL.

5. If using a private repository, e.g. GitHub, configure keys to allow OCP to pull changes into the
platform. Follow the instructions in the following link in case of any doubts about how to create a
key pair and configure it at both sides (OCP and GitHub).
[[https://blog.openshift.com/private-git-repositories-part-1-best-practices/]]

6. Configure the database parameters as environment variables (deployment config). Use these
variable names: MYSQL_USER, MYSQL_PASSWORD, MYSQL_DATABASE.

7. Add a route to the web application, so it is accessible from the Internet.

8. Optionally, configure a webhook in GitHub to enable automated builds when changes are pushed into
the repository.

NOTE: All the above steps can be conducted directly from the oc cli tool.
