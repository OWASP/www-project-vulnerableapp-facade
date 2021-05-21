---

layout: col-sidebar
title: OWASP VulnerableApp-Facade
tags: VulnerableApp-Facade
level: 2
type: code
pitch: As Vulnerabilities are highly dependent on technologies and covering all the technology under on Vulnerable Application is impossible hence VulnerableApp-facade is built to solve this problem by building a distributed farm of Vulnerable Applications such that they can be built agnostic to tech stacks.

---
#  ![VulnerableApp-facade](https://raw.githubusercontent.com/SasanLabs/VulnerableApp/master/docs/logos/Coloured/iconColoured.png)VulnerableApp-facade
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

As we are seeing a lot of technological enhancements in the industry from past few years, these technical enhancements are solving one or the other problem however with that they also bring few different vulnerabilities. VulnerableApps are generally written in one of the techstacks like either Node.js or Java with a SQL or NoSQL database etc and hence they are not able to expand to a whole new set of Vulnerabilities which are present in other technologies. Also adding more vulnerabilities in a single vulnerable application makes it heavier and complex which finally makes it unmaintainable. So VulnerableApp-facade is built to solve this problem by building a distributed farm of Vulnerable Applications such that they can be built agnostic to tech stacks.

## High Level Design Details
![High Level Design](https://github.com/SasanLabs/VulnerableApp-facade/blob/main/docs/images/VulnerableApp-facade.jpeg)

**VulnerableApp-facade** is a small component which acts as a webserver and a gateway. It routes the calls to different Vulnerable Applications which are registered with it based on a url pattern. It also exposes a schema/contract (Vulnerability Definition) and if a vulnerable application adhere to that then it will be able to intract and route the traffic to that vulnerable application. It also provides the generic skeleton UI which it builds by reading the provided schema (Vulnerability Definition) from the vulnerable application and then loads the UI specific to vulnerable application inside the skeleton UserInterface. 

## How to run the project
VulnerableApp-facade is a farm of vulnerable applications where each application runs as a docker container. VulnerableApp-facade has `docker-compose.yml` file which contains docker configuration of other vulnerable applications along with docker configuration of VulnerableApp-facade. 
### Simple Start ###
In order to run entire suit please download the [docker-compose.xml](https://github.com/SasanLabs/VulnerableApp-facade/blob/main/docker-compose.yml) and run the following command from terminal:
``` docker-compose up ```
Then naviate to ``` http://localhost:8080 ``` to play with the application

### Advanced Start ###
As [docker-compose.xml](https://github.com/SasanLabs/VulnerableApp-facade/blob/main/docker-compose.yml) contains all the applications which adhere to the schema of VulnerableApp-facade so in cause you are looking for specific vulnerable applications like only Java related vulnerable applications then remove other vulnerable applications from [docker-compose.xml](https://github.com/SasanLabs/VulnerableApp-facade/blob/main/docker-compose.yml) and then run steps as mentioned in the [Simple start step](#simple-start).

## How to Contribute to the project
VulnerableApp-facade have majorly 2 components:
1. Static files
2. Lua module

Static files are used to load the skeleton UserInterface and Lua module is used to merge the Vulnerability Definitions exposed by different vulnerable applications.
So you just need to do the changes in any of the components and then build the docker image using command ```docker build . -t vulnerableapp_facade``` and then run the project as mentioned at [How to run the project](#how-to-run-the-project) 

# Communication
Please feel free to reach out to us on our [VulnerableApp Slack Channel](https://owasp.slack.com/messages/#owasp-vulnerableapp/) or send an email to karan.sasan@owasp.org for any queries.

OWASP is a fantastic place to learn about application security, to network, and even
to build your reputation as an expert. We also encourage you to be [become a member](/membership) or consider
a [donation](https://owasp.org/donate/?reponame=www-project-vulnerableapp-facade&title=OWASP+VulnerableApp-facade) to support our ongoing work.

[More Information on Project](https://sasanlabs.github.io/VulnerableApp-facade/)

