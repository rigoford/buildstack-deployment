# Ops-files

This is the README for Ops-files. To learn more about `buildstack-deployment`, go to the main [README](../README.md). 

## Feature-based Ops-files

| Name | Purpose | Notes |
|:---  |:---     |:---   |
| [`just-jenkins.yml`](just-jenkins.yml) | Removes all other buildtools from the deployment apart from `jenkins-master` and `jenkins-slave`. | Using this may fail as it depends upon a bosh link with Nexus. |
| [`just-gerrit.yml`](just-gerrit.yml) | Removes all other buildtools from the deployment apart from `gerrit`. | |
| [`just-nexus.yml`](just-nexus.yml) | Removes all other buildtools from the deployment apart from `nexus`. | Using this may fail as it depends upon a bosh link with Jenkins. |
| [`just-sonarqube.yml`](just-sonarqube.yml) | Removes all other buildtools from the deployment apart from `sonarqube`. |
| [`add-newrelic.yml`](add-newrelic.yml) | Optional newrelic agent addon. | Required variables: _newrelic_license_key newrelic_deployment_tag_ |
| [`add-stackdriver-tools.yml`](add-stackdriver-tools.yml) | Optional stackdriver-tools addon. |  Required variables: _google_stackdriver_creds - (service account JSON)_ ||
