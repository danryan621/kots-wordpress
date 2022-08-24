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
- Select the releases tab of the Vendor portal, click "create release," delete the existing example yaml files and upload the yaml files from the `manifests` directory of this repo.  This includes files for Wordpress, MySQL and the Kots specific yaml specs.  Creating the release can also be done via the Replicated CLI (if this method is preferred see ths page in the [Replicated Quickstart Docs](https://docs.replicated.com/vendor/tutorial-installing-with-cli)
- Create a release and promote that release to a deployment channel
2. Create a customer and download an application license
- Select "Customers" on the left menu of the Replicated Vendor Portal. create a new customer and assign the customer to the "unstable" channel
- At the bottom of the Unstable channel select the "embedded" cluster option and copy that command
3. Install the Kots kubectl plugin via the command line:
```shell
curl https://kots.io/install | bash
```
4. Test the deployment: 
- Choose `your namespace` which will be the namespace for every component of the application and in the Kots admin console
```shell
kubectl kots install your-app-slug
```
You will be prompted to provide a namespace to install into as well as a password (to control access to the admin console), and then to connect to http://localhost:30888 , where you can login with the password you just specified, and then upload the customer license.
5. Clean up
```shell
kubectl delete ns your-namespace
```
