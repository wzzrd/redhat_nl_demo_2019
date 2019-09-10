# Adding GitHub Authentication to OpenShift

## GitHub steps

1. Create an organization in GitHub
2. Go to organization settings on your personal settings page (lower left
   corner)
3. Under Developer Settings, click OAth Apps and then New OAuth App
4. Fill in the fields, and take note of the Client ID and Client Secret values
  - the application name can be whatever you want, but should be a bit
    descriptive *of your cluster / service*
  - the home page URL should be something like
     https://oauth-openshift.apps-crc.testing/
  - the call back URL should be something like 
     https://oauth-openshift.apps-crc.testing/oauth2callback/githubidp
  - the last bit of the call back URL ('githubidp' above) should exactly match
    the application name field

