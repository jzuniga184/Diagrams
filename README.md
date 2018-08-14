# Architecture + Product Diagram. 

![alternativetext](/Architecture_diagram.pdf)


These creates and contains: 

*Jenkins node 
*Docker Swarm cluster of 1 master and 2 slaves
* CI/CD Jenkins scripted pipeline to deploy the app upon a change.

## Getting Started

Hygieia is a single, configurable, easy-to-use dashboard to visualize near real-time status of the entire delivery pipeline. The health of the continuous delivery pipeline, from code commit to production deployment, with all the necessary information around health and quality of the software, is essential for any DevOps Organization.

### Prerequisites

-Create and AWS account.

AWS account and a "Small tier" for Jenkins (Free tier will ran out of resources at the build process) 

https:aws.amazon.com/free

- Create a docker hub and docker cloud free accounts 

We will use this to publish our images from our scripted pipeline and trigger a deploy to swarm upon a change in the repo.

https://hub.docker.com/
https://cloud.docker.com

Clone or Fork this repo to your localhost.

```git clone https://github.com/jzuniga184/Hygieia-1.git```

### Installing

Here are the steps you need to follow to install your development enviroment, note this steps are for a mac running version 10.13.2

From localhost (mac)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install terraform
sudo easy_install pip
sudo pip install ansible
sudo pip install boto
sudo pip install six
curl -o /usr/local/bin/ec2.py https://raw.githubusercontent.com/ansible/ansible/devel/contrib/inventory/ec2.py
curl -o /usr/local/bin/ec2.ini https://raw.githubusercontent.com/ansible/ansible/devel/contrib/inventory/ec2.ini
```
