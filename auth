# Adding GitHub Authentication to OpenShift

## GitHub steps

1. Create an organization in GitHub
2. Go to organization settings on your personal settings page (lower left
   corner)
3. Under Developer Settings, click OAth Apps and then New OAuth App
4. Fill in the fields, and take note of the Client ID and Client Secret values
  - the application name can be whatever you want, but should be a bit
    descriptive *of your cluster / service*. I'm using "githubidp" in this
    example.
  - the home page URL should be something like
     https://oauth-openshift.apps-crc.testing/
  - the call back URL should be something like 
     https://oauth-openshift.apps-crc.testing/oauth2callback/githubidp
  - the last bit of the call back URL ('githubidp' above) should exactly match
    the application name field

## OpenShift steps

Create a secret containing the clientSecret from GitHub:

```
oc create secret generic github-secret --from-literal=clientSecret=<secret> -n
openshift-config
```

Finally, create and `oc apply -f` the following YAML, adapted with your
specific clientID, obviously:

```
apiVersion: config.openshift.io/v1
kind: OAuth
metadata:
  name: cluster
spec:
  identityProviders:
  - name: githubidp
    mappingMethod: claim
    type: GitHub
    github:
      clientID: <your-clientID>
      clientSecret:
        name: github-secret
      organizations:
      - <your-organization>
```

