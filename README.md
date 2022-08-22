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
export REPLICATED_APP=wordpress-mayfly
export REPLICATED_API_TOKEN=f0ae9cc88cc16d5acc290745b027244d9c5eb50dab94e24ee524f81acd6dc5f7
replicated release ls

git clone https://github.com/danryan621/kots-wordpress.git

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

The UIs of Prometheus, Grafana and Alertmanager have been exposed on NodePorts 30900, 30902 and 30903 respectively.

To access Grafana use the generated user:password of admin:Shf6OZHng .



To access the cluster with kubectl, copy kubeconfig to your home directory:

    cp /etc/kubernetes/admin.conf ~/.kube/config
    chown -R 0 ~/.kube
    echo unset KUBECONFIG >> ~/.bash_profile
    bash -l

You will likely need to use sudo to copy and chown /etc/kubernetes/admin.conf.



Node join commands expire after 24 hours.

To generate new node join commands, run curl -fsSL https://kurl.sh/version/v2022.08.19-0/wordpress-mayfly-unstable/tasks.sh | sudo bash -s join_token on this node.

To add worker nodes to this installation, run the following script on your other nodes:
    curl -fsSL https://kurl.sh/version/v2022.08.19-0/wordpress-mayfly-unstable/join.sh | sudo bash -s kubernetes-master-address=10.0.29.72:6443 kubeadm-token=w6v3vt.2iznhepp4w8k2jid kubeadm-token-ca-hash=sha256:be0265515416114bb30d9523b96994548c679972874a67cede2dba51cbc28a1c kubernetes-version=1.19.16 docker-registry-ip=10.96.0.136 primary-host=10.0.29.72


root@ip-10-0-29-72:~/Wordpress/kots-wordpress# 
