# Kots Wordpress Demo
This is a demo for packagin Wordpress and MySQL as a Kots applications

# Installing the example


# kots-wordpress
Pwd 
cd downloads
ls replicated.pem
ls -al replicated.pem
chmod 400 replicated.pem 
ssh -i replicated.pem ubuntu@ec2-54-191-26-84.us-west-2.compute.amazonaws.com

sudo su -
ls
tar xvzf replicated_0.40.2_linux_386.tar.gz
sudo su -
export REPLICATED_API_TOKEN=de67a601c578234f5c0b9e7291fc580c7554acff7a0e50212409fab321bd3095
replicated release ls


curl -sSL https://kurl.sh/wordpress-mayfly-unstable | sudo bash
mkdir replicated-cli-tutorial

replicated customer create \\n  --name "Some-Big-Bank" \\n  --expires-in "240h" \\n  --channel "Unstable"
replicated customer ls
replicated customer download-license \\n  --customer "Some-Big-Bank"
export LICENSE_FILE=~/Desktop/Some-Big-Bank-${REPLICATED_APP}-license.yaml\nreplicated customer download-license --customer "Some-Big-Bank" > "${LICENSE_FILE}"
cat
curl ipecho.net/plain ; echo
pwd
cd D
cd Downloads
ls replicated.pem
chmod
ls -al replicated.pem
chmod 400 replicated.pem
ls -al replicated.pem
ssh -i "replicated.pem" ubuntu@ec2-54-191-26-84.us-west-2.compute.amazonaws.com


ssh -i "wordpress.pem" ec2-user@ec2-54-193-9-205.us-west-1.compute.amazonaws.com
