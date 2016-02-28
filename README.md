# Docker-compose CI machine

This is my docker-compose file for run a set of Continuous Integration Tools. This set include:

- *Gitlab*: a web application thats wraps git version control server.
- *Jenkins* CI: The core of the system.
- *SonaQube*: automatic quality code measurements.

# Default credentials for applications

| App       | Credential      |
|-----------|-----------------|
| Jenkins   | no login        |
| SonarQube | admin / admin   |
| Gitlab    | root / 5iveL!fe |

# To do before run docker-compose

Docker images aren't configure to run together yet. Therefore you must config them manually before launching docker-compose first time. 

- *Jenkins CI*: To retrieve the source code of projects from Gitlab you must install git plugin. Each project you configure as job in Jenkins must have a repository from gitlab. The url for the repository would be something like http://gitlab-gitlab/root/<your project>. To comunicate with sonar SonarQube plugin must be installed too. Each project that you want to examine with SonarQube must have a file called sonar-project.properties in its root folder.

- *SonarQube*: In SonarQube each project must be create before run jenkins task. 
- *Gitlab*: To build automatically each time you push the project you must config a "hook" in Gitlab. Config an url like this: http://jenkins-gitlab:8080/git/notify_commit?url=<url of the repository>.
