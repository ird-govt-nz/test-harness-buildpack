# Create User Provisioning Services (CUPS)
In order to supply sensitive information to the buildpack, we can create user provided services.
This allows us to store sensitive information in the service, and pull this information into the buildpack as required.

## Setting up AWS s3 credentials (to retreive assets stored on an s3 bucket)
This has already been setup but should this change, you will be required to alter or add new services.
Please see 'Installation / access / reference guides' for installation of Cloud Foundry CLI and access.

### Using Cloud Foundry CLI, to create a new service
```
cf7 cups <USER_PROVIDED_SERVICE_NAME> -p "AWS_BUCKET, AWS_DIR, AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_DEFAULT_REGION"
cf cups test-artifacts-s3-credentials-staging-customer-experience-monitors -p "AWS_BUCKET, AWS_DIR, AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_DEFAULT_REGION"
```
You will be prompted to enter the values for each parameter. This will then provision the service to the Assurity Cloud platform.

### Using Assurity Cloud, to create a new service
Alternatively, you can navigate to the Services tab within the Assurity Cloud platform, and alter / add values to an existing service.
