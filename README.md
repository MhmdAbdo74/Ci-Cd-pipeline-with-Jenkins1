# CI/CD Pipeline with Jenkins, SonarQube, Nexus, and Docker

## Overview

This repository contains the configuration and scripts for setting up a comprehensive Continuous Integration/Continuous Deployment (CI/CD) pipeline using Jenkins, SonarQube, Nexus, and Docker. The pipeline automates the process of building, testing, analyzing code quality, and deploying applications.

## Prerequisites

Before setting up the CI/CD pipeline, ensure you have the following prerequisites installed and configured:

- **Jenkins**: Install and configure Jenkins on the build server. [Download Jenkins](https://www.jenkins.io/download/) and follow the installation instructions.

- **SonarQube**: Set up a SonarQube server for code quality analysis. [Download SonarQube](https://www.sonarqube.org/downloads/) and follow the installation instructions.

- **Nexus**: Install and configure Nexus as a repository manager. [Download Nexus](https://www.sonatype.com/nexus/repository-oss/download) and follow the installation instructions.

- **Docker**: Install Docker on the build server for containerization. [Download Docker](https://www.docker.com/get-started) and follow the installation instructions.

## Jenkins Setup

### Install Jenkins Plugins:

```bash
make install-jenkins-plugins
