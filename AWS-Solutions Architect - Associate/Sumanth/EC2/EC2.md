# EC2 (Elastic Cloud Compute) 

## What is EC2(Elastic Cloud Compute) ? 
* AWS EC2 (Amazon Elastic Compute Cloud) is a web service that allows developers/clients to rent virtual computers/Servers on which to run their own Software/Business applications. EC2 instances provide secure and scalable (resizeable) computing capacity in the cloud.

<img width="282" alt="image" src="https://github.com/user-attachments/assets/5f0835bd-76e0-4d61-92a0-021e9ba88e9b">


## What is an EC2 Instance ?
* In AWS, an "Instance" refers to a virtual server/Computer that customers can rent from Amazon Web Services (AWS) to run their applications. 
* These instances are the fundamental building blocks of EC2 and provide the compute power needed to handle various workloads.

## Why we need to use EC2 ?
* ```Below are following Reasons to why we have to use EC2```
  
* 1. ```Scalability```: EC2 allows you to scale (resize) your compute capacity up or down easily based on your application's needs.
                  This scalability ensures that you can handle varying workloads efficiently without ```over-provisioning or under-provisioning``` resources.


* 2. ```Flexibility```: EC2 offers a wide selection of instance types optimized for different use cases, such as compute-optimized, memory-optimized, storage-optimized, and 
                        GPU instances.
                  This allows you to choose instances that best fit your application's requirements.


* 3. ```Cost Efficiency```: EC2 follows a pay-as-you-go pricing model, where you pay only for the compute capacity you actually use.
                      This reduces upfront costs and allows you to optimize your spending based on actual usage patterns.


* 4. ```Reliability```: AWS operates data centers in multiple regions around the world, offering high availability and reliability.
                  EC2 instances are designed to be resilient to failures within a single data center.
                  you can use features like Auto Scaling and Elastic Load Balancing to further enhance availability.


* 5. ```Security```: AWS provides a secure infrastructure for running EC2 instances, including features like security groups, network ACLs (Acess Control Lists), encryption                       options, and integration with AWS Identity and Access Management (IAM).


* 6. ```Global Reach```: AWS has a global footprint with data centers in multiple geographic regions.
                   This allows you to deploy EC2 instances close to your users to reduce latency and improve performance.


* 7. ```Integration with AWS Services```: EC2 integrates with other AWS services such as Amazon S3 (storage), Amazon RDS (database), Amazon VPC (networking), and many others.
                                    This makes it easier to build complex, scalable applications using a combination of AWS services.


* 8. ```Development and Testing```: EC2 provides an ideal environment for development and testing purposes. You can quickly spin up instances with different configurations, test                                 your applications, and then terminate them when no longer needed, saving costs.


# AWS Regions and Availability Zones (AZs)

## AWS Region :
* In General Region is a Geographical Location. Each geographical is the Combinations of one or more isolated Locations.
* Each Region is designed to be isolated from the other Regions. This achieves the greatest possible fault tolerance and stability.
* AWS Regions are Distributed over the World, So the Customer Can choose their availability locations to host their CLOUD Infrastructures.
* AWS Regions are Globally Scoped for Some AWS Services like IAM, S3, Route 53.
* AWS Regions are Not Globally Scoped for AWS RDS.

** Note : ```There is a charge for data transfer between Regions.```
* AWS Regions are Denoted by US-EAST-1, AP-SOUTH-1 etc,..

### If Regions are Not having Replications, then How to Avoid Fault tolerance and Availability ?

* To Overcome this we have Availability Zones called (AZs).
  
## Availability Zones (AZs) :
* Here Each Region having one or More Isolated locations these isolated Locations are 
  Called as Availability Zones (AZs).
* Each Availability Zone is a physicalData Center in the Region. Also Each Az;s are 
  Separated from Each Other.
* AWS Availability Zones (AZs) are Denoted by US-EAST-1a,  US-EAST-1b.


## Best Practices to Chhose the Regions :

* Proximity : When We choose Regions it Need to be near to us and our Customers.
* Services
* Cost
* ServiceLevel Agreement
* Compliance 

<img src="https://github.com/user-attachments/assets/99d2779a-35b5-45e3-bd21-90fec4a604ff" alt="image" style="width:200px;"/>


