# CONTAINERIZING AN ECOMMERCE APPLICATION WITH MULTIPLE SERVICES

**Project Design:**

![project-deployment-design](../images/Project-design.jpg)

This deployment consists of Both multi-stage docker containers and multiple services.

**Client:** Client directory contains the files for the website "frontend" built on angular work.
The dockerfile for the frontend is located at [client-dockerfilw](client/Dockerfile)

**javaapi:** This is the backend part of the application, and it is built with java and depends on the emartdb (MYSQL)

**nginx:** Act as the reverse proxy which connect the entire setup to the world

**nodeapi:** This is a nodejs backend  built with java script it depends on mongodb database system.

### The Dockerfile

Each of the application has their docker file which is then called by the docker compose file ( [Docker-compose](docker-compose.yaml) )
The nginx directory does not have it's own dockerfile, same wth mongodb and mysql, will will be using the public images in the docker hub.
These images will be pulled down and respective docker containers will be created when we run:
```markdown
docker compose up
```
```markdown
docker compose build -d
``` will be run to build the image for client, nodeapi and javaapi.

![containe-runningrs](../images/container-running.png)

The following microservices will be created (client, javaapi, nodeapi, nginx, mongodb and mysqldb).
Note that the docker engine runs on aws ec2 instance, with http port 80 open on the ec2 security group.

The webpage is shown below:

![Emart-webpage](../images/mullti-stage-docker.png)


