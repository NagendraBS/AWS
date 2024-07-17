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

## Here are the Some of the AWS Availability Zones :
 * Code	Name	          Opt-in                      Status
us-east-2	US         East (Ohio)	               Not required
us-east-1	US         East (Virginia)	           Not required
us-west-1	US        West (N. California)	       Not required
us-west-2	US        West (Oregon)	               Not required
af-south-1	        Africa (Cape Town)	         Required
ap-east-1	          Asia Pacific (Hong Kong)	   Required
ap-south-2	        Asia Pacific (Hyderabad)	    Required
ap-southeast-3	    Asia Pacific (Jakarta)	      Required
ap-southeast-4	    Asia Pacific (Melbourne)	    Required
ap-south-1	        Asia Pacific (Mumbai)	        Not required
ap-northeast-3	    Asia Pacific (Osaka)	        Not required
ap-northeast-2	    Asia Pacific (Seoul)	        Not required
ap-southeast-1	    Asia Pacific (Singapore)	    Not required
ap-southeast-2	   Asia Pacific (Sydney)	        Not required
ap-northeast-1	   Asia Pacific (Tokyo)          	Not required
ca-central-1	     Canada (Central)	              Not required
ca-west-1	         Canada West (Calgary)          Required
eu-central-1	      Europe (Frankfurt)	          Not required
eu-west-1	        Europe (Ireland)	              Not required
eu-west-2	          Europe (London)	              Not required
eu-south-1	        Europe (Milan)	              Required
eu-west-3	          Europe (Paris)	              Not required
eu-south-2	        Europe (Spain)	              Required
eu-north-1	        Europe (Stockholm)          	Not required
eu-central-2	      Europe (Zurich)	              Required
il-central-1	      Israel (Tel Aviv)            	Required
me-south-1	        Middle East (Bahrain)	        Required
me-central-1	      Middle East (UAE)	            Required
sa-east-1	          South America (São Paulo)	    Not required

  


