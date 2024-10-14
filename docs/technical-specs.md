# Technical Specifications
## Introduction
This document describes technical system requirements and specifications for operating KomMonitor with
Docker. It is assumed that all KomMonitor components and 3rd party software components that are necessary
for the operation of KomMonitor are deployed using Docker Compose.

Docker Compose templates for deploying KomMonitor as Docker containers are provided in the following 
repository: https://github.com/KomMonitor/docker. The configuration files provided simplify and
accelerate the local deployment of the entire KomMonitor stack via Docker. For productive deployment,
the configuration files provided must be adapted to the respective operating environment,

The operation of KomMonitor in a Kubernetes cluster is not described in this document.

## System Requirements
The most important requirement for the operation of KomMonitor is that it is possible to use a Docker Engine
on the server. Windows Server as an operating system is not supported. Additional system requirements:
* Server operating system: Ubuntu (other Linux distributions would also be possible, provided that a Docker engine can be operated there - see supported platforms: https://docs.docker.com/desktop/install/linux-install/#supported-platforms)
* CPU: 4 cores
* Memory: 12-16 GB RAM
* Storage: 50 GB SSD (depending on the amount of data to be managed in KomMonitor, there may be higher storage requirements)