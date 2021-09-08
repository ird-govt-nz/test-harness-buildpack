# Test Harness Buildpack

version: 1.0.0

## Usage
This buildpack enables:
- deployment of test harnesses to Assurity Cloud.
- assests to be copied from an AWS s3 bucket e.g. keystores.
- the deployed application to retrieve sensitive data from user provided services (CUPS).


## Deployment of test harnesses
In order to deploy a test harness to Assurity Cloud, we need to create the following:

### Manifest yaml



### Create User Provided Services (CUPS)
These services have already been created on Assurity Cloud. But should you need to amend or add new services, this will provide guidance [CUPS.md].


## Example APP Manifest
Create an application manifest.xml within the route of your Cloud Foundry application.
- reference the credentials buildpack url
- reference the keystore through an evironment variable, where the keystore path is supplied as a jvm property
```
applications:
- name: <APP-NAME>
  disk_quota: 1024M
  memory: 1024M
  buildpacks:
    - https://<BASE_URL>/credentials.git
  env:
    JAVA_OPTS: '-Djavax.net.ssl.keyStore=CUSTOM_KEYSTORE'
```

## Pre-requisites

### Cloud Foundry
- CF7 installation,
- Setting the proxy & export PATH
- CLI reference

### AWS
- AWS CLI installation,
- CLI reference

### AWS s3 Bucket access
- permissions / policies,
- Multifactor Authentication

### Assurity Cloud Access
- email assurity-cloud-team