# Deploying the Buildstack against bosh-lite

## Prerequisites

- `bosh` is installed
- You have `bosh-deployment`, `buildstack-boshrelease` and `buildstack-deployment` repos handy

## 1. Installing bosh-lite
To install bosh-lite on your local environment, follow the [Official guide](https://bosh.io/docs/bosh-lite.html#install).

## 2. Targeting and Logging in

There a several ways to target a bosh director.
This doc will use `alias-env` and `-e`,
but you can set environment variables if you prefer.

First, create an alias for your director:
```
bosh -e DIRECTOR_IP --ca-cert <(bosh int ./creds.yml --path /director_ssl/ca) alias-env MY_ENV
```

Then, log in:
```
bosh -e MY_ENV login --client admin --client-secret $(bosh int ./creds.yml --path /admin_password)
```

## 3. Upload the cloud config

```
bosh \
-e MY_ENV
update-cloud-config \
buildstack-deployment/iaas-support/bosh-lite/cloud-config.yml
```

## 4. Upload a stemcell
```
bosh \
-e MY_ENV \
upload-stemcell \
https://bosh.io/stemcells/bosh-warden-boshlite-ubuntu-trusty-go_agent
```

## 5. Create and Upload Release
Navigate into the bosh release repo to create the release:
```
cd buildstack-boshrelease
```
Create the release:
```
bosh \
-e MY_ENV \
create-release
```
Then, upload the release to the director:
```
bosh \
-e MY_ENV \
upload-release
```

## 6. Deploy Buildstack
Navigate back out of the buildstack-boshrelease directory:
```
cd ..
```
Then deploy the local release:
```
bosh \
-e MY_ENV \
-d buildstack \
deploy \
buildstack-deployment/buildstack-deployment.yml \
--vars-store deployment-vars.yml 
```
