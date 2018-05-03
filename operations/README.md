# Ops-files

This is the README for Ops-files. To learn more about `buildstack-deployment`, go to the main [README](../README.md). 

## Feature-based Ops-files

| Name | Purpose | Notes |
|:---  |:---     |:---   |
| [`just-jenkins.yml`](just-jenkins.yml) | Removes all other buildtools from the deployment apart from `jenkins-master` and `jenkins-slave`. | Using this may fail as it depends upon a bosh link with Nexus. |
| [`just-jenkins-and-nexus.yml`](just-jenkins-and-nexus.yml) | Removes all other buildtools from the deployment apart from `jenkins-master`, `jenkins-slave`, and `nexus`. | |
| [`just-nexus.yml`](just-nexus.yml) | Removes all other buildtools from the deployment apart from `nexus`. | Using this may fail as it depends upon a bosh link with Jenkins. |
| [`just-sonarqube.yml`](just-sonarqube.yml) | Removes all other buildtools from the deployment apart from `sonarqube`. | |
| [`add-newrelic-server.yml`](add-newrelic-server.yml) | Includes `newrelic server` as an addon. | |
| [`add-newrelic-infrastructure.yml`](add-newrelic-infrastructure.yml) | Includes `newrelic infrastructure` as an addon. | |
| [`add-stackdriver-tools.yml`](add-stackdriver-tools.yml) | Optional stackdriver-tools addon. | Required variables: _google_stackdriver_creds - (service account JSON)_ |
| [`sonarqube-github-auth.yml`](sonarqube-github-auth.yml) | Optional GitHub auth settings for SonarQube. |  Required variables: _github_server_url - (URL for the GitHub server)_, _sonar_client_id - (Client ID for SonarQube on GitHub Enterprise)_, and _sonar_client_secret - (Client secret for SonarQube on GitHub Enterprise)_ |
| [`sonarqube-mysql.yml`](sonarqube-mysql.yml) | Optional MYSQL settings for SonarQube. |  Required variables: _sonar_mysql_password_ |
