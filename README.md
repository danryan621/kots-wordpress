# Kots Wordpress Demo
This is a demo for packaging Wordpress and MySQL as a Kots application

# YAML File overview
- config.yaml: Enables a config option in the main menu bar that allows the port to be changed
- dashboard.yaml: Enables two convenience dashboard buttons: 1) Go direct to the app 2) View the Github Repo for the application
- db-configmap.yaml: 
- mysql-deployment.yaml
- mysql-svc.yaml
- mysql-volume.yaml
- preflight.yaml: Contains preflight checks for the environment and others based on the Kubernetes installer file to ensure that the environment is set up appropriately for the application
- support-bundle.yaml
- wordpress-deployment.yaml
- wordpress-volume.yaml
- wordpress.svc.yaml
- wp-db-secrets.yaml

# Quick Start


