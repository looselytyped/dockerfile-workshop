# Docker workshop

## Highlights

- This **is a workshop**. Please come with a laptop that has the necessary installed software.
- Don't let the length of this document intimidate you :)
- Please follow **all of the installation instructions** in this document before coming to the workshop.
  Debugging docker/git installation takes time away from all attendees.

## Installation

You will need **2** things installed

- Docker
- [Git](https://git-scm.com/downloads)

Optionally, a good text editor.
I highly recommend [VS Code](https://code.visualstudio.com/) with the [Docker Extension](https://marketplace.visualstudio.com/items?itemName=PeterJausovec.vscode-docker).

### Docker installation

- For modern OS'es you can find download instructions [here](https://docs.docker.com/get-docker/)

There are two items of note

- Please treat this installation like any other. Different operating systems and different set ups (especially in company-issued laptops) can make this installation tricky. Google, and perhaps your desktop support team (if using a company-issued laptop) are your friends. Debugging this can be tricky.
- Docker requires a slew of permissions to run. So please make sure you grant Docker **all** the permissions it needs

### Testing your installation

```bash
> docker -v
Docker version 20.10.2, build 2291f61
```

## Warm up your engines!

**You want to do this BEFORE you show up for the workshop!!**
Running this over a hotel wifi connection might not go well.
Using the command (bash) prompt:

```bash
docker image pull alpine:3.17;
docker image pull ubuntu:21.04;
docker image pull ubuntu:22.04;
docker image pull jenkins/jenkins:2.60.3-alpine;
docker image pull nginx:1.19.6-alpine;
docker image pull openjdk:11.0.5-jre;
```

## The final test

Once again, at the command prompt:

```bash
> docker container run --rm -d --name myjenkins -p 8080:8080 jenkins/jenkins:2.60.3-alpine;
> docker logs -f myjenkins;
```

You should see the Jenkins logs flowing by eventually settling with the following:

```
Running from: /usr/share/jenkins/jenkins.war
webroot: EnvVars.masterEnvVars.get("JENKINS_HOME")
Apr 03, 2023 11:26:01 PM Main deleteWinstoneTempContents
WARNING: Failed to delete the temporary Winstone file /tmp/winstone/jenkins.war
Apr 03, 2023 11:26:01 PM org.eclipse.jetty.util.log.JavaUtilLog info
INFO: Logging initialized @481ms
Apr 03, 2023 11:26:01 PM winstone.Logger logInternal
INFO: Beginning extraction from war file
Apr 03, 2023 11:26:02 PM org.eclipse.jetty.util.log.JavaUtilLog warn
WARNING: Empty contextPath
# truncated for brevity
```

Visit http://localhost:8080 and see if you see the Jenkins login page.
If you do, you are all set to go!!

```bash
# ctrl-c to break out of the logs
docker container stop myjenkins;
```

Woot!!!
See you soon!!!
