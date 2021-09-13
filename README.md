# Test Harness Buildpack

version: 1.0.0

## Usage
This buildpack enables the deployment of test harnesses to Assurity Cloud. The supply script, contained within the bin folder, allows: 
- dependencies to be downloaded to support the running of the supply script i.e. AWS s3 CLI.
- sensitive data to be retrieved from user provided services (CUPS) and reused to:
    - copy assets from an AWS s3 bucket e.g. keystores. 
    - supply the app with sensitive customer data.
- a start-up script to expose environment variables to be consumed by the application.

## Deployment of Test Harnesses
In order to deploy a test harness to Assurity Cloud, we need to create the following:
 - a manifest yml contained within the application being deployed
 - user provided services to store sensitive information

### Manifest yaml
An example of a manifest yaml which should be placed within the route of the application.
Take note of:
- buildpacks: references this buildpack and must be followed by your default buildpack e.go java buildpack.
- services: refers to the user provided services you will utilise within the bin/supply script.
- env: refers to the properties that you wish to make available to the application
```
applications:
- name: <APP_NAME>
  health-check-type: process
  disk-quota: 1024M
  memory: 1024M
  buildpacks:
    - https://bitbucket.nsp.ird.govt.nz/scm/com/test-harness-buildpack.git
    - java_buildpack
  env:
    JAVA_OPTS: '-Drest-http-client.keystorePath=$APP_KEYSTORE_PATH'
  services:
    - <CUPS_SERVICES>
```

### Create User Provided Services (CUPS)
These services have already been created on Assurity Cloud. But should you need to amend or add new services, this will provide guidance [CUPS.md](CUPS.md).

## Installation / access / reference guides

### Cloud Foundry
- CF7 installation
- Setting the proxy & export PATH
- [CLI reference](https://cli.cloudfoundry.org/en-US/v7/)
- [Documentation](https://docs.cloudfoundry.org/)

### AWS s3 Bucket access
- permissions / policies (already setup)
- Multifactor Authentication (setup once you have access to bucket)
- [CLI reference](https://docs.aws.amazon.com/cli/latest/reference/s3/index.html)
- [User guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-services-s3-commands.html)

### Assurity Cloud Access
- Please email the Assurity Cloud Team for access.