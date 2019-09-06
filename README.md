# redhat_nl_demo_2019
Red Hat NL SA Team Tech Day Demos 

Work packages:

- Set up OpenShift 4.2 Dev Preview on AWS
- Set up htpasswd authentication for the team and / or integrate with GitHub authentication
- Set up OpenShift Container Storage for persistence
- Deploy Fuse Online
- Deploy the Kafka Operator, a Kafka cluster, a topic, and a user
- Create a reasonable Tekton pipeline to build one of the apps
- Build an app to read Twitter message from Kafka and reply to message with happy message
    - needs to be in own consumer group, because the app below needs to read the same messages
    - can be any language, but Python, Java / Quarkus or Go are prefered as they resonate best with developers
    - please make sure you use UBI for this
- Build an app to read Twitter message from Kafka, download any attached images and storage the images somewhere
    - storage can be one of:
      - file system, backed by OCS (the prefered solution)
      - database, like e.g. a postgresql cluster (crunchy data) deployed through an operator
        - this needs at least local storage on the nodes the database pods run on
      - something else: discuss!
    - needs to be in own consumer group, because the app above needs to read the same messages
    - can be any language, but Python, Java / Quarkus or Go are prefered as they resonate best with developers
    - please make sure you use UBI for this
- Build an app to read images from database / file system and display them on a web page
   - web page does not have to be pretty right now
   - but does have to update automatically (i.e. new image is written to disk, image is automatically added to page)
   - can be any language, but Python, Java / Quarkus or Go are prefered as they resonate best with developers
   - please make sure you use UBI for this
- Deploy and set up a Che cluster for working on the above apps (nice to have)
- Write Ansible playbooks based on the documentation generated above
- Investigate state replication between multiple OCP clusters running the above configuration