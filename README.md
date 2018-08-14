# Architecture + Product Diagram. 

The infrastructre diagrams attached here show a proposed architecture for medium/large sized company that needs to have their products on premise but can also expand to the cloud withauth changing the technology landscape that much. This does not focuses on any cloud centric approach. 

## Use Case:

The product is a classic webservice. A “frontend” application is serving the requests. This frontend application depends:

- On a in-memory database for caching
- On a RDBMS database for content management
- On an internal API service
- On an external API services

The documentation also explains several key items for the evaluation of this infrastructre as:

- Performance and stability monitoring.
- Capacity planning and scalability.
- Potential improvements or evolution.

### Hihligths of the Diagrams.

The repo includes two diagrams:

[Architecture_diagram2.pdf](https://github.com/jzuniga184/Diagrams/files/2285318/Architecture_diagram2.pdf) -This is a basic architecture diagram at 10k that inter-relates the diferent componenets of the proposed architecture.

[Architecture_diagram.pdf](https://github.com/jzuniga184/Diagrams/files/2285318/Architecture_diagram2.pdf)- This is a suggestion of products to use based on my personal expirience with them, many more can fit but I have the most expirience with these.


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
