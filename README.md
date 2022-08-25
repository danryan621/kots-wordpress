# Kots Wordpress Demo
This is a demo for packaging Wordpress and MySQL as a Kots application

# YAML File overview
## Kots specific yaml files
- __config.yaml__: Enables a config option in the main menu bar that allows the port to be changed
- __preflight.yaml__: Contains preflight checks for the environment and others based on the Kubernetes installer file to ensure that the environment is set up appropriately for the application
- __support-bundle.yaml__: Collects neceesary cluster data and sets apprpriate logging limits
- __dashboard.yaml__: Enables two convenience dashboard buttons: 1) Go direct to the app 2) View the Github Repo for the application
- __db-configmap.yaml__: Creates Database for Wordpress
- __wp-db-secrets.yaml__: Contains MySQL root password
## MySQL specific yaml files
- __mysql-deployment.yaml__: Deploys MySQL portion of the application
- __mysql-svc.yaml__: Defines MySQL service parameters
- __mysql-volume.yaml__: Creates Persistent Volume Claim for MySQL
## Wordpress specific yaml files
- __wordpress-deployment.yaml__: Deploys Wordpress portion of the application
- __wordpress-volume.yaml__: Creates Persistent Volume Claim for Wordpress
- __wordpress.svc.yaml__: Defines Wordpress service parameters

# Quick Start
1. Create a new Kots application in the Replicated Vendor Portal
- Create a new application and name it 
- Select the releases tab of the Vendor portal, click "create release," delete the existing example yaml files and upload the yaml files from the `manifests` directory of this repo.  This includes files for Wordpress, MySQL and the Kots specific yaml specs.  Creating the release can also be done via the Replicated CLI (if this method is preferred see ths page in the [Replicated Quickstart Docs](https://docs.replicated.com/vendor/tutorial-installing-with-cli))
- Create a release and promote that release to the Unstable deployment channel
2. Install the Replicated CLI according to these steps in the Replicated Documentation
- [Install the Replicated CLI](https://docs.replicated.com/vendor/tutorial-installing-with-cli#install-the-replicated-cli)
3. Get a service account token using these steps in the Replicated Documentation (Repace cli-quickstart with your apps details)
- [Set a Service Account Token](https://docs.replicated.com/vendor/tutorial-installing-with-cli#set-a-service-account-token)
4. Modify the Kubernetes Installer
- Open the installer.yaml file from this repo and copy it.
- On the left menu of the Replicated Vendor Portal, click on "Kubernetes Installer" and create a new installer.  Paste the contents of installer.yaml into the window and save.
- Promote the new installer to channel: Unstable
5. Create a customer and download an application license
- Select "Customers" on the left menu of the Replicated Vendor Portal. create a new customer and assign the customer to the "unstable" channel.  Select a date for the customer to expire and select "Trial" for the license type.
- After customer saving the customer profile, download the customer license using the first of the three icons on the right side of the screen.
6. Install the Kots kubectl plugin via the command line:
```shell
curl https://kots.io/install | bash
```
7. Install the Application via the command line
- Return to the Channels page and at the bottom of the Unstable channel select the "embedded" cluster option and copy that command
- Paste the install command in your CLI
8. Test the deployment: 
- Choose `your namespace` which will be the namespace for every component of the application and in the Kots admin console
```shell
kubectl kots install your-app-slug
```
You will be prompted to provide a namespace to install into as well as a password (to control access to the admin console), and then to connect to http://localhost:30888 , where you can login with the password you just specified, and then upload the customer license.
9. Clean up
```shell
kubectl delete ns your-namespace
```
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
