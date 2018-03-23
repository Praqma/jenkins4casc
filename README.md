# jenkins4casc

Repository for the praqma custom docker image using the new [Configuration as Code plugin](https://github.com/jenkinsci/configuration-as-code-plugin).

## How to use the docker image

Basically the same way as you would use the official Jenkins docker image. With one difference. If you start a container using this image with an environment variable `CASC_JENKINS_CONFIG` you can configure Jenkins to be configured on startup. And if you point to a configuration file from an URL you can reconfigure without the need for a restart. 

### Example with a minimum configuration file

`docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home -e CASC_JENKINS_CONFIG=https://raw.githubusercontent.com/Praqma/jenkins4casc/master/jenkins-minimal-example.yaml praqma/jenkins4casc`

We added the switch

`-e CASC_JENKINS_CONFIG=https://raw.githubusercontent.com/Praqma/jenkins4casc/master/jenkins-minimal-example.yaml` 

To point to the smallest possible configuration of Jenkins with Jenkins configuration as code:

```
jenkins:
  systemMessage: "The smallest possible configuration for Jenkins Configuration as Code plugin"
```

This gives this message on the welcome screen when Jenkins boots up: 

![Example of configuration](/img/small.png)

For more advanced examples take a look at the demos sections found in the [official repository for Configuration as Code plugin repository](https://github.com/jenkinsci/configuration-as-code-plugin)

### Example using docker compose and docker secrets

Comming soon...

