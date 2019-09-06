# Getting started with Quarkus

Follow steps on quarkus.io to create a Quarkus app, or, alternatively, use a Git repository with an already built Quarkus app.

## Steps to build a Quarkus app into a native-image with s2i

Build the Quarkus app with the official builder image from quay.io:
```
oc new-app quay.io/quarkus/ubi-quarkus-native-s2i:19.1.1~https://github.com/someuse/my-quarkys-app.git --name=my-quarkus-app
```

Mind that building a native image with Quarkus takes a fairly long time, at least several minutes.


## Steps to build a Quarkus app as a normal Java app with s2i

Doing a Java build is a little trickier, because the version of Maven in the standard openjdk builder image does not match the requirements of Quarkus. Setting up the openjdk/openjdk-11-rhel8 image from registry.redhat.io as a work around.

In order to pull this image, you need to set up a pull secret for the 'builder' service account. Go to https://access.redhat.com/terms-based-registry/#/accounts to create a service account, download the secret as yaml, import it into your project ('maxim-test' as an example) and link it to the 'builder' account.

```
kubectl create -f my-secret.yml --namespace=maxim-test
oc get secrets # check for your secret
oc secret link builder my-secret
oc import-image openjdk/openjdk-11-rhel8 --from=registry.redhat.io/openjdk/openjdk-11-rhel8 --confirm -n maxim-test
```

Now create the actual build and deployment configs

```
oc new-app --name quarkus-download-service-java --image-stream openjdk-11-rhel8 --build-env=ARTIFACT_COPY_ARGS="-p -r lib/ *-runner.jar" --env=JAVA_OPTIONS="-Dquarkus.http.host=0.0.0.0" --env=JAVA_APP_JAR="download-service-1.0-SNAPSHOT-runner.jar" https://github.com/wzzrd/quarkus-download-service.git
```

## Exposing a route to the app

```
oc expose svc/my-quarkus-app
```