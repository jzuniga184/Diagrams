# Architecture + Product Diagram. 

The infrastructure diagrams attached here show a proposed high-level architecture for medium/large sized company that needs to have their products on premise but can also expand to the cloud without changing the technology landscape and integrate easily. 


## Use Case:

The product is a classic web service. A “frontend” application is serving the requests. This frontend application depends:

- On an in-memory database for caching
- On a RDBMS database for content management
- On an internal API service
- On an external API services

My Assuming

1. This is not the first product that this company deploys, that's why it needs a high-end solution for its products.
2. This is not a startup is a medium to large company that has high requirements for their published apps, otherwise the stack will be more open source in the API, Security, integration areas and much cheaper in the CDN/ GTM space.
3. The company has on premise needs, this is not a cloud solution but the stack allows the flexibility to move easily to the cloud for a hybrid approach if need it.


The documentation also explains several key items for the evaluation of this infrastructure as:

- Deployment of code updates
- Performance and stability monitoring.
- Capacity planning and scalability.
- Potential improvements or evolution.

### Highlights of the Diagrams.

The repo includes two diagrams:

[Architecture_diagram.pdf](https://github.com/jzuniga184/Diagrams/files/2285318/Architecture_diagram.pdf) -This is a basic architecture diagram at 10k that inter-relates the different components of the proposed architecture.

[Product_diagram.pdf](https://github.com/jzuniga184/Diagrams/files/2285318/Product_diagram.pdf)- This is a suggestion of products to use based on my personal experience with them, many more can fit but I have the most experience with these.


## Key Items to consider

### Deployment of code updates

As seen in the [Product_diagram.pdf](https://github.com/jzuniga184/Diagrams/files/2285318/Product_diagram.pdf) the proposal is to have and automated build process involving Jenkins as the continuous integration and deployment server for its flexibility and little to no cost. 

In the build process, we have maven or graddle as both are good and well use all across the industry, and after the build process is done this will be added as binaries into Jfrog artifactory to have a common ground for files / binaries and all existing code for the enterprise this will allow to have a beefy repository that then we can deploy to our containers.

### Performance and stability monitoring.

-The proposal here is divided into two approaches. Log Aggregation and APM. Why is that?

The performance and stability of the servers is not an exact science and tools need to be in place to monitor every part of both the VMs and JVMs. 

This is accomplished by having a good mix of log aggregation mechanism’s that can alert me when one of my end points are down or when my recently deployed app is giving specific error with other dependencies. Also, this can be integrated with other tools like Pagerduty or Slack to give transparency to the proper teams when most need it.

In this space, I proposed the tools that I have used the most, but you could also name Splunk, DataDog,Scalyr and other well positioned products to perform these tasks.

-Log aggregation.

The proposal here is to go open source and use 3 on premise servers to index around 300gb of logs per day (Storage and retention policy need to be discuss on a per case basic). These 3 servers will allow the indexing, procesing, alerting and visualizations coming from the stack, 

-APM 

This is expensive but is the leader of APM for a reason, you can really know the guts of your applications and servers/ containers running them with ease and configure policies that fit your needs by application, business transactions and specific error codes for one or many of your end points, definitely a tool that can save you a lot of time. Also, the ability to see your application landscape and traffic coming and going from the different systems is especially useful when troubleshooting a failure in a dependency.


### Capacity planning and scalability.

Here the proposals go into two technologies, first the use of APM tools to monitor the exact need of every machine deploy and the use of Docker images with the binaries need it to run in order to be scalable. 

So, when you assigned certain amount of resources to a container you can verify with the APM tool how much free memory, CPU, open files, etc. is has this allow to modify / replace this container easily by running the pipeline again and changing the IaC for that specific product / App. 

To take this to the next level Kubernetes could be used to allow the immutability of the infrastructure and use the auto scaling to avoid any "running out of resources" situation. Not only that but will ensure the "state" of our application depending on our needs making the capacity and scalability much easier.


### Potential improvements or evolution.

The most relevant improvement areas on this proposal are:

- The full usage of Kubernetes taken into consideration.
- Go into a hybrid On Prem - Hybrid approach depending on the application and the product team’s needs.
- Take big data and machine learning use cases into consideration to gain better insights into the data.
- Implement a blockchain solution to get rid of the Policy server.

