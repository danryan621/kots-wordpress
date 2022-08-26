# Kots Wordpress Demo
This is a demo for packaging Wordpress and MySQL as a Kots application

# YAML File overview
## Kots specific yaml files
- __config.yaml__: Enables a config option in the main menu bar that allows the port to be changed
- __preflight.yaml__: Contains preflight checks for the environment and others based on the Kubernetes installer file to ensure that the environment is set up appropriately for the application
- __support-bundle.yaml__: Collects necessary cluster data and sets appropriate logging limits
- __dashboard.yaml__: Enables two convenient dashboard buttons: 1) Go direct to the app 2) View the Github Repo for the application
- __db-configmap.yaml__: Contains an initialize script that creates a database called "wordpress" which is required for Wordpress to function.  This configmap is mounted as a volume in the MySQL pod.
- __wp-db-secrets.yaml__: Contains MySQL root password which is used by both the wordpress and the MySQL pod.
## MySQL specific yaml files
- __mysql-deployment.yaml__: Deploys MySQL portion of the application
- __mysql-svc.yaml__: Defines MySQL service parameters. The service type ClusterIP is used as the pod will only communicate with the wordpress pod.
- __mysql-volume.yaml__: Creates a Persistent Volume Claim (PVC) for mysql pod  that is used to request a Persistent Volume (PV) to persist information that is stored within the wordpress database; OpenEBS is used for dynamic storage provisioning
## Wordpress specific yaml files
- __wordpress-deployment.yaml__: Deploys Wordpress portion of the application
- __wordpress-volume.yaml__: Creates Persistent Volume Claim (PVC) for the wordpress pod do that is used to request a Persistent Volume (PV) to persist information within the pod; OpenEBS is used for dynamic storage provisioning
- __wordpress.svc.yaml__: Defines Wordpress service parameters; the wordpress service type is NodePort which allows external access to the wordpress frontend webui.

# Quick Start

## Install the Replicated CLI according to these steps in the Replicated Documentation
- [Install the Replicated CLI](https://docs.replicated.com/vendor/tutorial-installing-with-cli#install-the-replicated-cli)
## Create a new Kots application in the Replicated Vendor Portal and obtain a service token 
1. Create a new application and name it
2. Open the Settings page
3. Copy the Application Slug and run this command with your application slug:
```shell
export REPLICATED_APP=your-application-slug
```
4. In the settings menu, create a read/write capable service account token
5. Copy token then run this command with your token to export it:
```shell
export REPLICATED_API_TOKEN=your_token
```
6. Run the following comman to verify the values are set correctly (all values in the output should be empty):
```shell
replicated release ls
```
7. Select the releases tab of the Vendor portal, click "create release," delete the existing example yaml files and upload the yaml files from the `manifests` directory of this repo.  This includes files for Wordpress, MySQL and the Kots specific yaml specs.  
8. Create a release and promote that release to the Unstable deployment channel
## Modify the Kubernetes Installer
1. Open the installer.yaml file from this repo and copy it.
2. On the left menu of the Replicated Vendor Portal, click on "Kubernetes Installer" and create a new installer.  Paste the contents of installer.yaml into the window and save.
3. Promote the new installer to channel: Unstable
## Create a customer and download an application license
1. Select "Customers" on the left menu of the Replicated Vendor Portal. create a new customer and assign the customer to the "unstable" channel.  Select a date for the customer to expire and select "Trial" for the license type.
2. After saving the customer profile, download the customer license using the first of the three icons on the right side of the screen.  Save this file to be uploaded later.
## Install the Application via the command line:
1. Return to the Channels page in the Replicated Vendor Portal and at the bottom of the Unstable channel select the "embedded" cluster option and copy that command (it will look similar to the one below):
```shell
curl -sSL https://kurl.sh/app-slug-channel | sudo bash
```
2. Paste the install command in your CLI and execute
## Test the deployment: 
1. After the installation is complete, in your CLI under the message "Installation complete," copy and paste the Kotsadm url (http://localhost:8800) into your browser, then use the password provided to login.
2. You will be presented with a TLS warning and can select "Continue to Setup"
3. The next page will present you with the option to add a private key and certificate or to "Skip and continue"
4. At the next page, apply the license generated earlier when the customer was created
5. Choose the port 30888
6. At this point you will have access to the Replicated Admin portal for the application 
7. Validate the Wordpress App is running by opening a new tab in your browser and navigating to http://localhost:30888

# Replicated Notes
## Managing Releases with the CLI Documentation Page
- In some aspects of the Managing Releases with the CLI section, a "$" is left in the beginning of the command.  When you copy using the button on the page it copies the "$" sign resulting in a `command not found`
### Setting a service token
- The "New Service Account Window" in the documentation is outdated and no longer shows the permissions field in the same way
### Adding Buttons and Links
- The documentation feels a little light on this and required some experimenting before I could get it to work. It wasn't immediately clear to me that you could add multiple links although it can be inferred.
## Replicated Vendor Portal
- On the Kubernetes Installer page, it would be helpful to have a link to Kurl.sh and short description, so users don't have to track it down in the docs
- When creating a customer or release, this is possible through the portal and the CLI.  It would be helpful to have split screen docs to show what can be done in either channel and what is only possible through one or the other.
- If you have created a release and removed the example files, it seems those don't show up again until you create a new application.  It would be helpful if you could refresh it to show the example files in case you need to reference them again.  
- It would be helpful to have a "redeploy option" in "Releases" in case a current deploy broke something and the user wants to redeploy the last version.  Sometimes as I was experimenting, I wanted to try something but then in order to get things back to the way they were, I had to go through the whole process of creating a release that mirrored a previous one
## Other
- The videos on the ReplicatedHQ Youtube channel were helpful however some of them were outdated and I had to be careful which ones to choose since the UI had evolved and some of them were a couple years old
- So far the videos I've seen have been more like tutorials and product walk throughs. The materials that convey the value of Replicated generally fall into the customer testimonial videos. There could be more done in regards to guiding users and potential customers to the value propositions for Replicated
