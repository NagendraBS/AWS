# IAM SERVICES
# What is IAM
* AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources.
* With IAM, you can manage permissions that control which AWS resources users can access.
* You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.


* IAM stands for Identity and Access Management. 
* It is a foundational service provided by AWS (Amazon Web Services) for managing ```users, groups,  roles,``` and ```their permissions``` within AWS cloud infrastructure. That enables you to manage access to AWS InfraStructure Services and resources securely.
* However IAM will be having Least Privileged principle.

Exp : (IAM will Recognise any User in the way that, Weather that user is an Identified user or Not, If USER is an identified user then the IAM will Provide the permission to user for Accessing any available AWS Infrastructure Service , thats why it is Called as  "```IDENTITY``` and ```ACCESS MANAGEMENT```".)

----


# Root user
* When you create an AWS account, you begin with one sign-in identity that has complete access to all AWS services and resources in the account.
* This identity is called the AWS account root user and is accessed by signing in with the email address and password that you used to create the account.


* Root User :
* The root user has unlimited permissions by default, including the ability to create and manage AWS resources,
* manage billing information, and manage IAM users and their permissions.

* The root user is typically considered the owner of the AWS account and has full control over billing, subscription management, and overall account settings.

```Important Considerations:```
* AWS strongly recommend that you don't use the ```root user``` for the Professional operations. Even though if you want to Use Root Users itself Means,
* ```AWS strongly recommends securing the root user account with multi-factor authentication (MFA) to add an additional layer of protection against unauthorized access.```

### Characteristics of the Root User :
* Created Automatically 
* Default Administrative Access Permissions 
* Highly Privileged



----  
# Why should I use IAM
* AWS Identity and Access Management is a powerful tool for securely managing access to your AWS resources.
* One of the primary benefits of using IAM is the ability to grant shared access to your AWS account.

### Advantages of using IAM (Identity and Access Management) 
* We Can Restrict the Access Permissions to the Required Users as per our organizational Requirements.
* We can define specific access policies based on roles and responsibilities within our organizations.
* IAM users support the best practice of ```least privilege```, which limits users to only the actions necessary for their specific tasks.
* 

------
# How IAM works
<img width="800" alt="image" src="https://github.com/sumanthrao04/Learning/assets/68411350/ebc8f8cb-2101-438b-b793-cca7eca510ea">


<img width="500" alt="image" src="https://github.com/sumanthrao04/Learning/assets/68411350/01c6e05b-a69b-4feb-8787-d55b5008ac96">



