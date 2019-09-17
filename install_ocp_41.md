
You need an AWS account
You need a Domain name in AWS

Goto try.openshift.com
  Sign In (with your Red Hat account)
    Create Clustes
    Choose AWS 
    Choose Installer-Provisioned Infrastructure
    Choose Download Installer
        Choose your platform to download Installer Binary on your local workstation  
  Choose Copy/Download Pull Secret
  Chose Download Command Line Tools

Go to your shell command prompt on your local workstation
Create a installation-config.yaml
  $ openshift-intall create install-config —dir=<directory>

Now you can change the installation-config.yaml in the <directory> . (for example regions,replica’s..etc)
Create a copy of your changed installation-config.yaml because after the installation the file will be deleted

Start installation:
On your local workstation
  $ openshift-install create cluster —dir=<directory where installation-config.yaml is located>
  ==> This takes approximately 20-30 minutes

When the installation completes:
  Export KUBECONFIG variables given at the end of the installation log
  Save the kubeadmin user and password for later usage
  Save you URL of the cluster

Login first time to the OpenShift cluster:
go to the OCP URL
   Login as kubeadmin
    Choose identity provider in the main page (url)
            Choose HTPasswd    (fill in filename and upload from your location, file created by you earlier)
    Logout
    
 go to the OCP URL
   In the login screen, choose htpasswd as identity provider

Make new users cluster admin:
  First the user has to login and logout then:
    As an admin on the CLI:
      Login as admin on the cluster via the CLO
      $ oc login -u admin -p admin <url cluster>
      $ oc adm policy add-cluster-role-to-user cluster-admin admin 
