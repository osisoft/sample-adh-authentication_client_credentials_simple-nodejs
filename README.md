# OSIsoft Cloud Services Client Credentials NodeJS Sample

**Version:** 1.0.0

[![Build Status](https://dev.azure.com/osieng/engineering/_apis/build/status/product-readiness/OCS/osisoft.sample-ocs-authentication_client_credentials_simple-nodejs?repoName=osisoft%2Fsample-ocs-authentication_client_credentials_simple-nodejs&branchName=main)](https://dev.azure.com/osieng/engineering/_build/latest?definitionId=4474&repoName=osisoft%2Fsample-ocs-authentication_client_credentials_simple-nodejs&branchName=main)

Developed against Node 14.15.1.

## Requirements

- Node 14.15+
- Register a [Client-Credentials Client](https://cloud.osisoft.com/clients) in your OSIsoft Cloud Services tenant and create a client secret to use in the configuration of this sample. ([Video Walkthrough](https://www.youtube.com/watch?v=JPWy0ZX9niU))
  - __NOTE__: This sample only requires the `Tenant Member` role to run successfully 
    - see: ['Authorization Allowed for these roles' in the documentation](https://docs.osisoft.com/bundle/ocs/page/api-reference/tenant/tenant-tenants.html#get-tenant) 
  - It is strongly advised to not elevate the permissions of the client beyond what is necessary.

## About this sample

This sample is meant to be very simple and straightforward to show how you can use common Node library calls (in this case, [axios](https://www.npmjs.com/package/axios)) to authenticate against OCS.  In a more complete application you should reuse the bearer token as appropriate and only reissue a new token when it is about to timeout.  

Steps:
1. Get needed variables
1. Get the token (authentication) endpoint from the discovery URL
1. Use the Client ID and Secret to get a bearer token from the token endpoint
1. Test it by calling the base tenant endpoint, ensuring a valid response is returned

## Configuring the sample

The sample is configured using the file [appsettings.placeholder.json](appsettings.placeholder.json). Before editing, rename this file to `appsettings.json`. This repository's `.gitignore` rules should prevent the file from ever being checked in to any fork or branch, to ensure credentials are not compromised.

OSIsoft Cloud Services is secured by obtaining tokens from its identity endpoint. Client credentials clients provide a client application identifier and an associated secret (or key) that are authenticated against the token endpoint. You must replace the placeholders in your `appsettings.json` file with the authentication-related values from your tenant and a client-credentials client created in your OCS tenant.

```json
{
  "Resource": "https://dat-b.osisoft.com",
  "ApiVersion": "v1",
  "TenantId": "PLACEHOLDER_REPLACE_WITH_TENANT_ID",
  "ClientId": "PLACEHOLDER_REPLACE_WITH_APPLICATION_IDENTIFIER",
  "ClientSecret": "PLACEHOLDER_REPLACE_WITH_APPLICATION_SECRET"
}
```

## Running the sample

To run this example from the command line once the `appsettings.json` is configured, run

```shell
npm ci
node Sample.js
```

## Testing the sample

To run the unit test for this sample, run

```shell
npm test
```

---

Tested against Node 14.15.1

For the main OCS Authentication samples page [ReadMe](https://github.com/osisoft/OSI-Samples-OCS/blob/main/docs/AUTHENTICATION.md)  
For the main OCS samples page [ReadMe](https://github.com/osisoft/OSI-Samples-OCS)  
For the main OSIsoft samples page [ReadMe](https://github.com/osisoft/OSI-Samples)
